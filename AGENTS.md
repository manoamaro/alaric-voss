# Copilot Instructions — Alaric Voss Vault

This repository is an **Obsidian vault**, not a code project. It is a D&D 5e
character journal and campaign log for *Alaric Voss* in *Curse of Strahd*.
There is no build, test, or lint step — content is plain Markdown rendered by
Obsidian. Edits should preserve Obsidian-specific conventions below.

## Vault Layout

- `index.md` — Title page; in-character framing for the journal.
- `Alaric Voss.md` — Character sheet/backstory.
- `sessions/` — Numbered session logs (`Session N.md`) with `index.md`.
- `compendium/` — Lore: `characters/`, `locations/`, `study notes/`,
  `world/`, `bestiary/`, `visions notebook/`.
- `spells/Level 0` … `spells/Level 9` — One note per spell.
- `items/` — Notable inventory items.
- `media/` — Images/assets, often grouped per session (`media/session10/...`)
  or topic. Embedded via `![[file.ext]]`.
- `_templates/` — Obsidian Templates plugin sources (`_session.md`,
  `_turn.md`, `_initiative.md`). Use these verbatim when creating new notes
  of those types.
- `*.base` files (`Spells.base`, `SpellBook.base`) — Obsidian **Bases**
  (YAML) view definitions. Not Markdown; edit as YAML.

## Conventions

### Links and media
- Use Obsidian **wiki links** (`[[Note Name]]`, `[[Note Name|alias]]`) for
  every cross-reference, not standard Markdown links.
- Embed images with `![[filename.jpg]]` (optionally `|400` for width). Place
  images under `media/` (per-session subfolder when tied to a session).

### Frontmatter (YAML)
Properties drive Obsidian views, so match existing keys exactly — Bases
filters are case- and spelling-sensitive.

- **Sessions** (`sessions/*.md`): `tags: [session]`, `date:` (fill in).
- **Spells** (`spells/Level N/*.md`): keys used by `Spells.base` /
  `SpellBook.base`:
  - `Level` (number), `School`, `CastingTime`, `Range`, `Duration`,
    `Components` (list of V/S/M), `Material`, `Concentration` (bool),
    `Ritual` (bool), `Damage`, `Damage Type`, `Upgrade`, `Prepared` (bool),
    `Spell Book` (bool), `Classes` (list, must include `Wizard` to appear),
    `tags: [spell]`.
  - Set `Spell Book: true` to include the spell in the personal spellbook
    view (`SpellBook.base`).
- **Character** (`Alaric Voss.md`): uses `aliases:` so `[[Alaric]]` resolves.

### Style of prose
- Session notes and the journal are written **in-character** as Alaric's
  first-person ledger — reflective, scholarly, slightly literary. Preserve
  that voice when extending existing entries; out-of-character mechanics
  belong in compendium / spell / item notes.
- Use `---` thematic breaks to separate scenes inside a session.

### Bases (`*.base`) files
- Plain YAML consumed by Obsidian's Bases plugin. Top-level keys:
  `filters`, `formulas`, `properties`, `views`, `summaries`.
- Filters reference note properties (e.g. `note["Spell Book"] == true`,
  `Classes.contains("Wizard")`, `file.inFolder("spells")`). Match the
  existing quoting/casing exactly.

## Workflow Notes

- New session → copy `_templates/_session.md` into `sessions/Session N.md`,
  set `date`, write in-character.
- New spell → create under the matching `spells/Level N/` folder with the
  full frontmatter block above; it auto-appears in `Spells.base` and (if
  `Spell Book: true`) in `SpellBook.base`.
- New compendium entry → place under the right `compendium/` subfolder and
  link it from related session/character notes via `[[...]]`.

## Git / Tooling

- `.gitignore` excludes `.DS_Store`, `.obsidian/workspace.json`,
  `.obsidian/app.json`, and `*.gdoc`. Don't commit those.
- Other `.obsidian/` config (core plugins, templates, graph, bases) **is**
  tracked — preserve it when editing settings.
- Binary assets in `media/` and the `character-sheet*.pdf` files are
  reference material; leave them untouched unless explicitly asked.
