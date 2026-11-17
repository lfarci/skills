# Skills

Personal [Hermes Agent](https://hermes-agent.nousresearch.com/) skills. Each skill lives in its own folder with a `SKILL.md`.

## Layout

```
lab/
  create-lab-issue/SKILL.md
  save-resource/SKILL.md
  split-lab-issue/SKILL.md
  restructure-subissues/SKILL.md
  review-backlog/SKILL.md
  research-topic/SKILL.md
  grill-idea/SKILL.md
  sync-issue-progress/SKILL.md
  ingest-notes/SKILL.md
  sort-note-sources/SKILL.md
  compare-note-coverage/SKILL.md
  clean-up-migration/SKILL.md
```

- `create-lab-issue` — create an issue in the lab repo (for example `lfarci/notes`) and attach it under the right Idea → Experiment → Task parent. Source of truth for hierarchy, titles, and bodies; the other lab skills follow it.
- `save-resource` — resolve a link, then open one focused issue per concern (no files).
- `split-lab-issue` — split a packed issue into one-concern children.
- `restructure-subissues` — reparent sub-issues, fix depth, close duplicates as duplicate, never delete.
- `review-backlog` — show what needs attention and recommend a next step; quiet on a weekly cron if the backlog is clean.
- `research-topic` — investigate a question against official sources and file a cited issue or comment (no files).
- `grill-idea` — relentlessly interview an Idea until it is well scoped, or close it as not planned if it is not worth pursuing.
- `sync-issue-progress` — verify claimed progress, comment, close finished Tasks, and update the parent index (never merge, never delete).
- `ingest-notes` — synthesize source notes already in the lab repo (Keep, Notion, or new captures) into topic-based concept notes written for retrieval, following `wiki/FILING.md`, and open one PR (never merge).
- `sort-note-sources` — triage source notes (keep or drop) and group the kept ones into topics with a destination note each, before ingestion.
- `compare-note-coverage` — map every source file to the concept notes that cite it, check URLs and content, and update the coverage ledger.
- `clean-up-migration` — after the user reviews the ledger, delete a migration folder in its own PR and rewrite source links so none break (never merge).

Exporting from a tool (Google Keep Takeout, Notion) is a one-time step and has no skill.

The `lab/` group is a category, not the Hermes default tap root (`skills/`). Install skills one at a time (commands below). To add this repo as a tap later, set the tap path to `lab/`.

## Install

Documented form: `hermes skills install owner/repo/path/to/skill`, or `hermes skills install https://example.com/SKILL.md`.

On the lab-master profile:

```bash
sudo hermes -p lab-master skills install lfarci/skills/lab/create-lab-issue
sudo hermes -p lab-master skills install lfarci/skills/lab/save-resource
sudo hermes -p lab-master skills install lfarci/skills/lab/split-lab-issue
sudo hermes -p lab-master skills install lfarci/skills/lab/restructure-subissues
sudo hermes -p lab-master skills install lfarci/skills/lab/review-backlog
sudo hermes -p lab-master skills install lfarci/skills/lab/research-topic
sudo hermes -p lab-master skills install lfarci/skills/lab/grill-idea
sudo hermes -p lab-master skills install lfarci/skills/lab/sync-issue-progress
sudo hermes -p lab-master skills install lfarci/skills/lab/ingest-notes
sudo hermes -p lab-master skills install lfarci/skills/lab/sort-note-sources
sudo hermes -p lab-master skills install lfarci/skills/lab/compare-note-coverage
sudo hermes -p lab-master skills install lfarci/skills/lab/clean-up-migration
```

Or from a raw `SKILL.md` URL, for example:

```bash
sudo hermes -p lab-master skills install https://raw.githubusercontent.com/lfarci/skills/main/lab/create-lab-issue/SKILL.md
```

Preview first with `hermes -p lab-master skills inspect lfarci/skills/lab/create-lab-issue`. These path and `main` URL forms apply once the skill is on `main`. For another profile, use `hermes -p <profile> skills install …` (with `sudo` only if that install needs it).

Matt Pocock's [grilling](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md) can be installed as-is:

```bash
sudo hermes -p lab-master skills install mattpocock/skills/skills/productivity/grilling
```

`grill-idea` is the adapted version for this lab (it files through `create-lab-issue` / `split-lab-issue`). You do not need both unless you want the upstream interview skill as well.

License: MIT.
