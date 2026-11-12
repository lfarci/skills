# Skills

Personal [Hermes Agent](https://hermes-agent.nousresearch.com/) skills. Each skill lives in its own folder with a `SKILL.md`.

## Layout

```
notes/
  notes-issue/SKILL.md
  notes-hierarchy/SKILL.md
  save-resource/SKILL.md
```

The `notes/` group is a category, not the Hermes default tap root (`skills/`). Install skills one at a time (commands below). To add this repo as a tap later, set the tap path to `notes/`.

## Install

From a GitHub path (documented form: `hermes skills install owner/repo/path/to/skill`):

```bash
hermes -p <profile> skills install lfarci/skills/notes/notes-issue
hermes -p <profile> skills install lfarci/skills/notes/notes-hierarchy
hermes -p <profile> skills install lfarci/skills/notes/save-resource
```

Or from a raw `SKILL.md` URL (documented form: `hermes skills install https://example.com/SKILL.md`):

```bash
hermes -p <profile> skills install https://raw.githubusercontent.com/lfarci/skills/main/notes/notes-issue/SKILL.md
hermes -p <profile> skills install https://raw.githubusercontent.com/lfarci/skills/main/notes/notes-hierarchy/SKILL.md
hermes -p <profile> skills install https://raw.githubusercontent.com/lfarci/skills/main/notes/save-resource/SKILL.md
```

Replace `<profile>` with the target profile (for example `lab-master`). Preview first with `hermes -p <profile> skills inspect lfarci/skills/notes/notes-issue`. These path and `main` URL forms apply once the skill is on `main`.

License: MIT.
