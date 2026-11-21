# CLAUDE.md — Second Brain

This repo is Alex's second brain, organized with the PARA method (Projects, Areas, Resources, Archive) plus an inbox and a journal.

## Folder map

| Folder | What lives here |
|---|---|
| `00-inbox/` | Quick captures and anything not yet sorted. Triage regularly. |
| `01-projects/` | Active efforts with a clear goal and an end date. One subfolder per project. |
| `02-areas/work/` | Ongoing work responsibilities (team, product areas, partners, processes). |
| `02-areas/personal/` | Ongoing personal responsibilities (health, finances, home, learning). |
| `03-resources/` | Reference material and topics of interest for future use. |
| `04-archive/` | Completed projects and inactive areas/resources. Move here, don't delete. |
| `journal/` | Daily notes, one file per day: `journal/YYYY-MM-DD.md`. |
| `.claude/skills/` | Custom Claude skills for working with this repo. |

## Routing rules

- **Not sure where it goes?** → `00-inbox/`.
- **Has a goal and a deadline/finish line?** → `01-projects/<project-name>/`.
- **Ongoing responsibility with no end date?** → `02-areas/work/` or `02-areas/personal/`.
- **Reference info, how-tos, research, topic notes?** → `03-resources/`.
- **Meeting notes** → the related project or area folder; if none fits, `00-inbox/`.
- **Daily log, reflections, what happened today** → `journal/YYYY-MM-DD.md`.
- **Project finished or area no longer active** → move it to `04-archive/` and set `status: archived`.
- **People / partner notes** → `02-areas/work/` (e.g. `02-areas/work/partners/`).

## Conventions

- **Filenames:** kebab-case, lowercase, no spaces (e.g. `broker-api-survey.md`).
- **Dates:** always `YYYY-MM-DD`. Prefix dated notes with the date (e.g. `2026-11-21-product-sync.md`).
- **Frontmatter:** every note starts with:

```yaml
---
type: note        # note | project | area | resource | meeting | journal
status: active    # active | on-hold | done | archived
updated: 2026-11-21
tags: []
---
```

Update `updated` whenever a note is edited.

## Git workflow

Commit and push directly to `main`. No branches or pull requests. Use short, descriptive commit messages.

## Azure DevOps access

- **Org URL:** https://dev.azure.com/merchantgrowth
- **Project:** Products
- **Auth:** handled by a network secret on `dev.azure.com`. Call the REST API with `curl` and **no auth header**. Never look for, ask for, or print tokens.

Example:

```bash
curl -s "https://dev.azure.com/merchantgrowth/Products/_apis/git/repositories?api-version=7.1"
```

### Repositories

As of 2026-11-21, the API call above returned **0 repositories**. Sign-in works: the request is authenticated as Alex Suto and can see the Products project. So the token is probably missing the **Code (Read)** scope, or the account lacks read access to the repos. Fix the token scope, then re-run the call and list each repo here with a one-line description.
