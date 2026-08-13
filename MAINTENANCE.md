# TimeMemo — How to run this blog

Written 2026-08-13, after an 18-month gap. Read this first when you come back.

---

## 1. What this blog actually is

| Piece | What it is |
|---|---|
| Generator | **Hugo** (extended), config in `config.toml` |
| Theme | **FixIt**, a git **submodule** at `themes/FixIt` |
| Content | Markdown page bundles in `content/posts/<name>/` |
| Languages | `zh-tw` (default) + `en`, via `index.zh-tw.md` / `index.en.md` |
| Build & deploy | GitHub Actions → GitHub Pages (`.github/workflows/gh-pages.yml`) |
| Trigger | **Every push to `master`** (the default branch is `master`, not `main`) |
| Domain | `timememo.lizhou31.com` — DNS on **Cloudflare**, `CNAME` file pins it |
| Comments | **utterances** — stored as GitHub issues on `Lizhou31/TimeMemo` |
| Search | **Fuse.js**, local, no external account (see §5) |

You do not deploy by hand. You push to `master`, and the Action builds and publishes.

---

## 2. State when I picked it up

- The site was **live and fine** — last built 2025-02-03, serving your last commit.
- But the **build was broken**. Not visibly: the workflow used `hugo-version: latest`,
  and the theme (FixIt v0.3.15, Nov 2024) does not compile under modern Hugo.
  The next push you made — any push — would have failed the deploy.

Reproduced locally, current Hugo v0.165.0:

```
ERROR render of "/categories" failed: template "terms/categories" not found
ERROR render of "/tags" failed: template "terms/tags" not found
```

Hugo changed its template-lookup rules in **v0.146.0**. Verified boundary:
`0.140.2` ✅ · `0.145.0` ✅ · `0.146.0` ❌ · `0.165.0` ❌.

This is the thing that would have made "taking the blog back" feel impossible:
you'd write a post, push, and the site would silently stop updating.

---

## 3. One-time setup on a machine

```bash
brew install hugo
```

Then clone **with the theme submodule** — this is the step people forget, and
without it the build fails with confusing "theme not found" errors:

```bash
gh repo clone Lizhou31/TimeMemo -- --recurse-submodules
```

Already cloned without it? Fix with:

```bash
git submodule update --init --recursive
```

---

## 4. Writing a post

Copy an existing post — the theme's `hugo new` archetype does **not** match the
front matter style your posts actually use.

```bash
cp -r content/posts/some_AI_murmur content/posts/my_new_post
```

Then in `content/posts/my_new_post/`:

1. Edit `index.zh-tw.md` — set `title`, `date`, `lastmod`, `tags`, `categories`.
2. Set `draft: false` when it's ready. **`draft: true` never publishes.**
3. Replace `featured-image.webp`. Put every image for the post in this folder and
   reference it by bare filename: `featured-image.webp`, not a path.
4. Edit or delete `index.en.md`. A post can be Chinese-only — delete the file if
   you don't want an English version.

Categories must be one of the existing five, or the category page will be empty:
`tech_note` · `tech_experience` · `life_memo` · `book_reflection` · `fictionary`.

**The URL is the folder name**, because `config.toml` sets `[Permalinks] posts = ":filename"`.
So `content/posts/my_new_post/` publishes at `https://timememo.lizhou31.com/my_new_post/`.
Renaming a published folder breaks its URL, its inbound links, and its utterances
comment thread (utterances keys comments by pathname). Don't rename old posts.

### Preview locally

```bash
hugo server -D
```

`-D` includes drafts. Open http://localhost:1313. Live-reloads as you save.

### Publish

```bash
git add -A && git commit -m "[post] new post \"...\"" && git push origin master
```

Then watch the deploy — don't assume it worked:

```bash
gh run watch
```

---

## 5. What I changed, and why

All changes are **uncommitted** in your working tree. Review with `git diff` before
committing. Nothing has been pushed; the live site is untouched.

**1. Theme submodule: FixIt v0.3.15 → v0.4.5** *(the actual fix)*

Verified: builds clean on Hugo 0.165.0. With every change below applied, the
build produces an **identical URL set** — 72 HTML pages, none added, none lost
(checked by diffing the generated file lists before and after). Your permalinks,
and therefore your utterances comment threads, are safe.

**2. `gh-pages.yml`: `hugo-version` `latest` → `0.165.0`**

`latest` is what broke you. It means "whatever Hugo shipped this morning", so an
untouched repo rots on its own. Pinned now — bump it deliberately, only after
`hugo --gc --minify` passes locally.

**3. `config.toml`: search `algolia` → `fuse`**

Your Algolia app `6UTKX9KXC6` no longer exists — its hostname doesn't resolve at
all, so site search was dead on the live site. `fuse` indexes locally at build
time. No account, nothing to renew, nothing to expire.

**4. `config.toml`: added `search` to `[outputs] home`**

Required for the above. FixIt declares a `search` output format, but listing
`home` in your own config **replaces** the theme's list rather than extending it
— so the search index was never generated. Verified working: typing `IEEE` now
returns four highlighted hits.

FixIt also offers `archives` and `offline` output formats here. I left both out
deliberately: adding them creates six new pages (`/archives/`, `/offline/`, and
their `en` equivalents), and the goal was to change nothing visible. Add them if
you want a post-archive page — it won't appear in the menu until you add one.

**5. `config.toml`: `[params.gitInfo] branch` `main` → `master`**

Your repo has only a `master` branch, so every "Edit this page" link on the live
site 404s today.

**6. `config.toml`: `languageCode`/`languageName` → `locale`/`label`**

Deprecated in Hugo 0.158, slated for removal. Renaming now avoids the next break.

**7. Renamed `Special_caculate.webp` → `Special_calculate.webp`**

Pre-existing typo, unrelated to any of the above. The IEEE754 post referenced the
correct spelling while the file on disk was misspelled, so that image has been
**broken on the live site since 2023**. Confirmed: the old URL returns 404 today.

Remaining build warnings (`.Language.LanguageCode was deprecated…`) come from
inside the FixIt theme, not your config. Harmless; upstream's to fix.

---

## 6. Two drafts are waiting for you

Both are `draft: true`, written in 2023, never published:

- `content/posts/cat_and_me_1/` — 愛貓的我與像貓的她 (fictionary)
- `content/posts/talk_about_engineer/` — 關於工程的一些心得和看法 (tech_experience)

`talk_about_engineer` has only `index.md`, not `index.zh-tw.md`. In a multilingual
site that file belongs to the default language (`zh-tw`) and works, but rename it
to `index.zh-tw.md` for consistency with every other post.

---

## 7. Things that will bite you again

- **`hugo-version: latest` in CI.** Now pinned. Don't undo it.
- **The submodule.** A fresh clone without `--recurse-submodules` cannot build.
  CI is already correct (`submodules: true` in the workflow).
- **Never renaming published post folders.** The folder name *is* the URL.
- **`draft: true`** is the default in new posts. It is also why two of your posts
  have been invisible for three years.
- **GitHub Pages source** is set to a stale branch `Test-branch` in repo settings.
  Harmless — `build_type` is `workflow`, so that field is ignored — but confusing
  if you ever go looking. Ignore it, or point it at `master`.
- **"Enforce HTTPS" is off** in Pages settings. Cloudflare currently 301s HTTP →
  HTTPS so it works, but that's Cloudflare covering for it, not GitHub.
- **`resources/_gen/` is committed** to the repo, and Hugo rewrites it on every
  build — so `git status` looks dirty after any local preview. Optional cleanup:

  ```bash
  git rm -r --cached resources/_gen && echo "resources/_gen/" >> .gitignore
  ```

---

## 8. Quick reference

```bash
hugo server -D                 # preview at localhost:1313, drafts included
hugo --gc --minify             # exactly what CI runs — must pass before you push
git push origin master         # deploy
gh run watch                   # watch the deploy
gh run list --limit 5          # recent deploys
```
