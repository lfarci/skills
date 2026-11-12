# Skills

Personal [Hermes Agent](https://hermes-agent.nousresearch.com/) skills. Each skill lives in its own folder with a `SKILL.md`.

## Layout

```
notes/
  create-notes-issue/SKILL.md
  save-resource/SKILL.md
```

- `create-notes-issue` — create an issue in a notes repo (for example `lfarci/notes`) and attach it under the right Idea → Experiment → Task parent.
- `save-resource` — resolve a link, then open one focused issue per concern (no files).

The `notes/` group is a category, not the Hermes default tap root (`skills/`). Install skills one at a time (commands below). To add this repo as a tap later, set the tap path to `notes/`.

## Install

Documented form: `hermes skills install owner/repo/path/to/skill`, or `hermes skills install https://example.com/SKILL.md`.

On the lab-master profile:

```bash
sudo hermes -p lab-master skills install lfarci/skills/notes/create-notes-issue
sudo hermes -p lab-master skills install lfarci/skills/notes/save-resource
```

Or from a raw `SKILL.md` URL:

```bash
sudo hermes -p lab-master skills install https://raw.githubusercontent.com/lfarci/skills/main/notes/create-notes-issue/SKILL.md
sudo hermes -p lab-master skills install https://raw.githubusercontent.com/lfarci/skills/main/notes/save-resource/SKILL.md
```

Preview first with `hermes -p lab-master skills inspect lfarci/skills/notes/create-notes-issue`. These path and `main` URL forms apply once the skill is on `main`. For another profile, use `hermes -p <profile> skills install …` (with `sudo` only if that install needs it).

License: MIT.
