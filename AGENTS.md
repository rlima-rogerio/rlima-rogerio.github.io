# AGENTS.md

Canonical instructions for any coding agent (Claude Code, Codex, Gemini CLI, Copilot, Cursor, etc.)
working on this repository. Tool-specific files (`CLAUDE.md`, `GEMINI.md`,
`.github/copilot-instructions.md`) only point here: **edit this file, not them.**

## What this is

Personal academic website of Prof. Rogerio R. Lima (DEE/UFMG), published by **GitHub Pages**
at <https://rlima-rogerio.github.io> from the `master` branch. GitHub Pages builds it with
**Jekyll** automatically on push; there is no CI, no theme, no JavaScript and no Node tooling.

Design goal: **minimal, light, fast**. One stylesheet, system fonts, no frameworks, no web fonts,
no tracking scripts. The only third-party embed is the Flag Counter image in the footer.

## Layout

| Path | Purpose |
|---|---|
| `_config.yml` | Site settings: title, email, nav menu, academic profile links, Flag Counter id |
| `_layouts/default.html` | The single page layout (header, nav, footer) |
| `_includes/flagcounter.html` | Flag Counter widget (hidden while `flagcounter_id` is empty) |
| `_data/news.yml` | News items shown on the home page (newest first) |
| `_data/publications.yml` | Publications, grouped by year on `/publications/` (newest first) |
| `_data/people.yml` | Current students (by group) and alumni |
| `index.html` | Home: bio, extension course highlight, news, contact |
| `research.html`, `publications.html`, `people.html`, `teaching.html` | Section pages |
| `cursos/percepcao-robotica/index.html` | Extension course page (Portuguese) |
| `assets/css/style.css` | All styles; colors and width are tokens in `:root` |
| `assets/img/`, `assets/docs/` | Photos, figures, CV PDF |

## Conventions

- **Content lives in `_data/*.yml` whenever possible.** To add a paper, student or news item, edit
  the YAML, not the HTML. Keep lists newest first and follow the field names already used.
- Site language is **English**; the extension course page is **Brazilian Portuguese** (`lang: pt-BR`
  in its front matter) because its audience is Brazilian students.
- Use proper accents in names and Portuguese titles (Gonçalves, Robótica, etc.).
- Internal links use `{{ '/path/' | relative_url }}`; pages use `permalink:` with a trailing slash.
- Student photos: square JPEG, ~600×600, in `assets/img/students/`, referenced by `photo:` in
  `_data/people.yml`. Without a photo, initials are shown.
- Keep it light: do not add JS frameworks, icon fonts, CSS libraries or analytics.
- Do not invent facts (dates, co-authors, approvals, enrollment links). Leave a clear TODO or ask.
- The extension course URL `/cursos/percepcao-robotica/` is referenced from the Google Sites page
  (sites.google.com/view/rlima-rogerio/home/cursos) listed in the UFMG SIEX proposal. **Do not change it.**

## Build and preview

```bash
bundle install            # once (Gemfile: jekyll + webrick)
bundle exec jekyll serve  # http://127.0.0.1:4000
# or, without bundler:  jekyll build  → output in _site/ (git-ignored)
```

Always run a build after changes and fix any Liquid/YAML errors before committing.

## Git

- Default branch: `master` (deployed). Work on a branch for larger changes.
- Push only when the owner asks; pushing to `master` publishes the site.

## Related sources

- `../webpage/`: the department-hosted version of the site (cpdee.ufmg.br), richer and in English.
  Use it as a source of facts when updating this site.
