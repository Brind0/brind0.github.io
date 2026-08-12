# Publishing this site

Draft built 12/08/2026 by Claude Code, per the hub's web-design skill.
Nothing here has been pushed anywhere. Publication is Charlie's act.

## What to fill in before publishing

Search the repo for these placeholders and replace them:

| File | What | Find |
|---|---|---|
| `index.html` | LinkedIn URL | `linkedin.com/in/[to-fill]` (footer) |
| `index.html` | Email address | `[to-fill@example.com]` (the `mailto:` href) and the visible `[email, to fill]` label |
| `index.html` | oscola-cite repo link | `data-repo="oscola-cite"` anchor, currently `href="#"` — point at the real GitHub URL once that repo is pushed, and delete the "(repository link to follow)" span |
| `index.html` | sg-statutes-agent repo link | same pattern, `data-repo="sg-statutes-agent"` |
| `index.html` | Life Hub write-up link | `data-repo="life-hub"` currently points at your GitHub profile (`github.com/Brind0`) with "(public write-up to follow)" — swap for the write-up URL once `life-hub-writeup-10-08-2026.md` is published |
| `index.html` | The "Draft, built..." status line in the footer | delete it once the site is live — it's a working-copy marker, not meant to ship |

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

2. **Create the GitHub repo** (suggest `Brind0.github.io` for a root
   profile site at `https://brind0.github.io`, or a normal repo name like
   `portfolio` if you'd rather it live at `https://brind0.github.io/portfolio/`):

   ```bash
   cd ~/projects/portfolio-site
   gh repo create Brind0/Brind0.github.io --public --source=. --remote=origin
   ```

   (`gh` is already authenticated per STATE.md's 11/08 GitHub Pro claim.)

3. **Commit and push** (a first commit already exists locally from the
   build session — check `git log` and `git status` before adding more):

   ```bash
   git add -A
   git commit -m "Fill in contact links and repo URLs"
   git push -u origin main
   ```

4. **Enable Pages** (only needed if the repo isn't named
   `<username>.github.io`, which publishes automatically):

   ```bash
   gh api -X POST repos/Brind0/portfolio/pages -f source[branch]=main -f source[path]=/
   ```

   Or via the UI: repo Settings → Pages → Source → Deploy from a branch →
   `main` / `/ (root)`.

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
