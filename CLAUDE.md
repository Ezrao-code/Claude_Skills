# Claude_Skills

Personal marketplace of Claude Code plugins, used on two workstations and in
Claude Code cloud sessions. The root `.claude-plugin/marketplace.json` lists
each plugin; every plugin lives in its own top-level folder.

## Layout

| Folder | What it is |
| --- | --- |
| `ponytail-main/` | Plugin: "lazy senior dev" mode (simplest solution that works) |
| `caveman-main/` | Plugin: ultra-compressed replies; hooks need Node.js |
| `threejs-skills-main/` | Plugin: 13 Three.js skills |
| `rtk-develop/` | NOT a plugin. RTK is a Rust CLI (token-saving output compression), kept as a backup copy. Install the program separately. |

Folders are third-party packages copied in as-is. Don't edit their internals
unless asked; to update one, replace the whole folder with the new version.

## Rules

- Each plugin needs `<folder>/.claude-plugin/plugin.json` and its skills in
  `<folder>/skills/<skill-name>/SKILL.md`.
- Adding a plugin: put it in its own folder (no nested duplicate folder like
  `x-main/x-main/`), then add an entry to `.claude-plugin/marketplace.json`
  with `"source": "./<folder>"`.
- Validate JSON after editing: `python3 -m json.tool .claude-plugin/marketplace.json`.
- Do not add or edit hidden folders (`.claude-plugin`, `.github`, ...) by
  uploading through the GitHub web page; it skips them. Use git.
- Pull/fetch before pushing: two machines plus Claude push to `main`, and a push
  from a stale copy overwrites the others' changes.

## Install

```
/plugin marketplace add Ezrao-code/Claude_Skills
/plugin install ponytail@claude-skills
/plugin install caveman@claude-skills
/plugin install threejs-skills@claude-skills
```

After new pushes: `/plugin marketplace update claude-skills`.
