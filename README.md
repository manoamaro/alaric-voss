**Overview**
- Obsidian vault for a D&D 5e character and campaign journal: Alaric Voss in Curse of Strahd.
- Tracks backstory, session logs, world/character compendium, and a spellbook using Obsidian’s Bases views.
- Start with `index.md` (title page) or open `Alaric Voss.md` for the character sheet and backstory.

**Vault Structure**
- `Alaric Voss.md` — Character portrait, backstory, traits.
- `sessions/` — Numbered session notes with frontmatter (`tags: [session]`, `date:`) and in-note images.
- `compendium/` — Lore reference:
  - `characters/`, `locations/`, `study notes/`, `world/`.
- `spells/` — Spells organized by level (`Level 0`…`Level 9`).
- `Spells.base`, `SpellBook.base` — Bases (table) configurations for browsing and filtering spells.
- `_templates/_session.md` — Minimal template for new sessions.
- `media/` — Images and assets referenced via Obsidian wiki links (`![[...]]`). Includes subfolders per session and compendium art.
- `.obsidian/` — Workspace, core plugin settings, and one bundled community plugin (`cmenu-plugin`).

**Open in Obsidian**
- In Obsidian: Open folder as a vault pointing to this repository root.
- Ensure the following core plugins are enabled (they’re preconfigured in `.obsidian/core-plugins.json`):
  - `Files`, `Search`, `Backlinks`, `Outgoing links`, `Properties`, `Templates`, `Workspaces`, `Graph`, and `Bases`.
- Optional: Enable the bundled community plugin `cmenu-plugin` (Contextual Menu) if desired.

**Spellbook (Bases)**
- Open `Spells.base` to view all spells in a table. Useful views include “All” and per-level views.
- `SpellBook.base` provides a curated view filtered for:
  - Notes in the `spells/` folder
  - `Classes` includes `Wizard`
  - Note property `Spell Book` set to true
- Spells rely on note properties. Common properties used in the tables:
  - `level` (number), `school` (text), `CastingTime`, `Range`, `Duration`
  - `components` (list), `concentration` (checkbox), `ritual` (checkbox)
  - Optional: `Damage`, `Damage Type`, `Prepared`, `Spell Book`
- To include a spell in the personal spellbook, set `Spell Book: true` in that spell note.

**Adding Content**
- New session: Create a note in `sessions/` using `_templates/_session.md` and fill `date`.
- New compendium entry: Add a note under the appropriate `compendium/` subfolder and link it from session notes or `Alaric Voss.md` using `[[Wiki Links]]`.
- New spell: Add or edit a note under the relevant `spells/Level X/` folder and set properties as needed.
- Images: Place under `media/` (e.g., `media/session10/...`, `media/compendium/...`) and embed with `![[relative_file_name.ext]]`.

**Navigation Tips**
- Use the Graph and Backlinks panes to explore connections between sessions and compendium pages.
- `index.md` is a simple entry; the workspace is set to show the Spells base and index side-by-side.

**Notes**
- PDFs (`character-sheet.pdf`, `character-sheet-lvl4.pdf`) and `.stl` files in `media/` are reference assets.
- This vault uses standard Obsidian features and Bases; no build or runtime steps are required.
