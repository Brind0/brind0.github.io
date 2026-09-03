# Publishing this site

Draft built 12/08/2026 by Claude Code, per the hub's web-design skill.
Refreshed 03/09/2026: repo links now point at the real GitHub URLs (the
repos themselves are committed locally, not yet pushed — see
`vault/domains/career/portfolio-publish-03-09-2026.md`), a Writing section
was added for the AMG write-up, and the sg-statutes-agent eval figures were
corrected to the current measured numbers (the 10/08 figures had gone
stale once all four Acts were indexed — see that repo's README). Nothing
here has been pushed anywhere. Publication is Charlie's act.

## What to fill in before publishing

Search the repo for these placeholders and replace them:

| File | What | Find |
|---|---|---|
| `index.html` | LinkedIn URL | `[Charlie sets]` (footer) |
| `index.html` | Email address | `[Charlie sets]` (footer) |
| `index.html` | AMG write-up link | Writing section, currently "(to follow, pending publication)" — link it once `amg-build-writeup-03-09-2026.md` clears its own publication gate (security audit, client-approved wording, Charlie's edit and go) |
| `index.html` | Life Hub write-up link | still points at your GitHub profile (`github.com/Brind0`) with "(public write-up to follow)" — swap for the write-up URL once `life-hub-writeup-10-08-2026.md` is published |

The GitHub profile link (`github.com/Brind0`) is already real and can stay as-is.

Before any of the above goes live, the usual publication gate applies
(career.md §4): security-audit pass, then your explicit go. This is a
static page with no secrets or client data in it, so the audit should be
quick, but run it anyway.

## Steps to publish on GitHub Pages

1. **Review the content first.** Read `index.html` top to bottom — every
   claim on it is meant to trace to the vault (positioning.md, the career
   README timeline) or to something you told Claude directly. If anything
   reads as overstated, fix it before it goes anywhere public.

2. **Create the GitHub repo, in the browser** (no `gh` CLI on this
   machine as of 03/09/2026 — checked, not installed). Suggest
   `Brind0.github.io` for a root profile site at `https://brind0.github.io`
   (Pages publishes automatically for a repo with that exact name), rather
   than a normal `portfolio` repo name that would need Pages enabled
   separately. Create it empty: no README, no licence, no gitignore (this
   local repo already has all three).

3. **Add the remote and push** (a first commit already exists locally —
   check `git log` and `git status` before adding more):

   ```bash
   cd ~/projects/portfolio-site
   git add -A
   git commit -m "Fill in contact links and repo URLs"
   git remote add origin https://github.com/Brind0/Brind0.github.io.git
   git push -u origin main
   ```

4. **Enable Pages**, only if the repo is not named `<username>.github.io`
   (which publishes automatically): repo Settings → Pages → Source →
   Deploy from a branch → `main` / `/ (root)`.

5. **Verify.** Give it a minute or two, then check the live URL loads,
   dark/light mode both render correctly (toggle your OS appearance),
   and every link you filled in actually resolves.

## Notes on the build

- Single `index.html` + `style.css`, no build step, no framework, no
  external font or asset loading — it will be fast on GitHub Pages as-is.
- Passed `npx impeccable detect` clean (accessibility contrast, heading
  hierarchy, type scale, generic-font and AI-hero-pattern checks) — see
  the build session for the before/after if useful context.
- No stock imagery, no testimonials, no client logos, nothing implying
  an active client engagement — Silver Lining, CoreAbility and AMG stay
  out of this page entirely (prospects-not-clients rule, ME.md).
