# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
bundle install                          # Install dependencies
bundle exec jekyll serve                # Serve locally at localhost:4000
bundle exec jekyll serve --force_polling  # Use this on WSL
```

Requires Ruby 2.7.0 (see `.ruby-version` or Gemfile).

**Note:** Changes to `_config.yml` require restarting the Jekyll server to take effect.

## Architecture

This is a Jekyll static site that renders a single-page resume, deployed via GitHub Pages.

**Content flow:**
- `index.html` — entry point, uses `layout: resume`
- `_layouts/resume.html` — the full page template; all sections are conditionally rendered based on `_config.yml` flags
- `_data/*.yml` — structured content for each resume section (experience, education, projects, skills, associations, interests, links, recognitions)
- `_config.yml` — controls personal info, section visibility (`resume_section_*: true/false`), social links, and display options

**Styling:**
- `css/main.scss` imports from `_sass/`; key files are `_resume.scss`, `_layout.scss`, `_variables.scss`
- Print-specific styles use the `.no-print` / `.print-only` CSS classes

**To add/edit resume content:** modify the corresponding `_data/*.yml` file.
**To toggle sections on/off:** set `resume_section_<name>: true/false` in `_config.yml`.
**To add a new section:** add a data file in `_data/`, then add a loop block in `_layouts/resume.html` gated by a config flag.
