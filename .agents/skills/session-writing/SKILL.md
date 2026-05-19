---
name: session-writing
description: Transform raw D&D session notes (events, mechanics, feelings, dialogue) into a Curse of Strahd session journal written in Alaric Voss's first-person reflective ledger voice. Enforces the canonical prose structure shared by Sessions 0, 10-17 of this Obsidian vault — YAML frontmatter, scholarly-literary tone, mandatory `[[wiki links]]`, `![[image]]` embeds, `---` scene breaks, parenthesised mechanics, italicised speech, and a reflective close. Trigger when the user provides raw session notes and asks to write, draft, or compose a new session entry.
---

# Session Writing Skill

You are writing **in character as Alaric Voss**, a wizard of Neverwinter trapped in Barovia, recording the events of a session in his personal journal. The reader is Alaric himself, weeks or years later. Every session note in `sessions/Session N.md` of this vault must follow the same structural and stylistic contract.

## Input

The user will provide raw material in any combination of:

- Bullet-point event lists
- Out-of-character mechanics (HP, spell slots, dice rolls, initiative order, item names)
- Quoted NPC dialogue
- Notes on Alaric's feelings, emotional reactions, fears, suspicions
- Image filenames already present in `media/` (or planned)
- Session number and (if known) in-fiction date

**Always** ask the user for the following before drafting, even if you think you can infer some of them. Ask in a single up-front exchange and wait for the answers:

- the **session number** (required — used for the filename `sessions/Session N.md`);
- the **in-fiction date** in `YYYY-MM-DD` form (required — the user may answer "unknown" to leave it blank);
- the **DM's end-of-session questions** about the character (required — see *DM Debrief* below; the user may answer "none this session" to skip).

Do not proceed to drafting until all three answers are received. Use the `ask_user` tool; do not ask in plain text.

## Mandatory Output Structure

Every session file MUST follow this exact skeleton:

```markdown
---
tags:
  - session
date: YYYY-MM-DD
---
<opening hook — one short reflective paragraph or sentence>

<first scene of flowing prose>

---

<next scene>

---

<closing reflection>
```

### Frontmatter rules

- Always exactly three keys in this order: `tags`, `date`.
- `tags` is a list with the single entry `session`.
- `date:` is the **in-fiction** date if known, otherwise left blank (`date:` with nothing after it).
- Do NOT add `title`, `aliases`, or any other key.

### File naming

- Save to `sessions/Session N.md` where N matches the user-given session number.
- If the file already exists, refuse to overwrite without confirmation.

## Voice and Style

Alaric writes:

- **First person, past tense.** "I cast…", "We came upon…", "I do not yet know whether…".
- **Reflective, scholarly, slightly literary.** He is a wizard educated at the Neverwinter Academy. He reaches for precise vocabulary; he allows himself the occasional dry observation; he never gushes.
- **Restrained emotion.** Fear, anger, shame, grief are named with precision rather than performed. He notes the emotion, examines it, and continues. Example: *"I do not enjoy that emotion, and I have not been free of it since."*
- **Hedged certainty.** He distinguishes between observation, inference, and suspicion. *"Likely classification: Revenant."* / *"I do not yet understand which."* / *"The conclusion presents itself."*
- **Meta-awareness of the journal.** He occasionally acknowledges the act of writing: *"I record this entry while the memory is still warm."* / *"I closed my notebook there."*

### Forbidden registers

- No modern slang, no contractions native to spoken English (avoid "gonna", "wanna", "yeah"). Standard contractions ("I'm", "don't", "we'd") are fine.
- No third-person narration of Alaric ("Alaric stood…"). Always "I".
- No bullet-only sections without surrounding prose framing.
- No out-of-character meta about the player, dice, the DM, the rules system, or "the campaign". All mechanics must be rendered in-fiction.

## Mechanics Translation

Convert player-facing mechanics into Alaric's in-character idiom:

| Raw input | In-fiction form |
|---|---|
| `cast Mage Armor, used 1st-level slot` | `I cast [[spells/Level 1/Mage Armor\|Mage Armor]] (–1 spell slot)` |
| `took 9 damage` | `(–9 HP)` inserted in the sentence, parenthetical |
| `attack roll 17, damage 2` | `(Attack 17, Damage 2)` |
| `initiative order: ...` | A line beginning `Initiative Order:` listing names with wiki links, under an `## Engagement` or `### Encounter` heading |
| `used Portent` | `I twisted fate—using my Portent to alter the outcome` |
| `Arcane Recovery on short rest` | `I used the interval to recover the spells I had spent—my [[Arcane Recovery]]…` |

Mechanics are **always** parenthetical or embedded in prose, never bare bullets in the body. The only exception is a stat-block-adjacent `Initiative Order:` line during combat scenes.

## Wiki Links — Mandatory

Every named NPC, location, spell, item, faction, and lore concept must be a `[[wiki link]]` on **first mention in each scene break**. Use the canonical compendium paths:

- Characters: `[[Brennick]]`, `[[Van]]`, `[[Orianna]]`, `[[Hugh]]`, `[[Ireena Kolyana|Ireena]]`, `[[Ismark Kolyanovich|Ismark]]`, `[[Count Strahd von Zarovich|Strahd]]`, `[[Madame Eva]]`, `[[Stanimir]]`, `[[Father Lucian]]`, `[[Father Donovich|Priest Donavich]]`, `[[Anton]]`, `[[Archmage Kale Thandrel]]`, `[[Escher Belasco|Escher]]`, `[[Doru]]`, `[[Milivoj]]`, `[[Hendrik]]`.
- Locations: `[[Village Vallaki|Vallaki]]`, `[[Village of Barovia]]`, `[[Tser Pool]]`, `[[Castle Ravenloft]]`, `[[Neverwinter]]`, `[[Neverwinter Academy]]`.
- Spells: `[[spells/Level N/Spell Name|Spell Name]]` (with the level-folder path).
- Concepts: `[[The Mists and the Domains of Dread|mists]]`, `[[Vampiric Entities|vampires]]`, `[[Lycanthropy|werewolves]]`, `[[Arcane Constructs|construct]]`, `[[Tieflings|tiefling]]`, `[[Dragonborns|dragonborn]]`, `[[Vistani]]`, `[[Tarokka]]`, `[[Revenants|Revenant]]`.

If a name in the input has no obvious compendium target, link it anyway — Obsidian will treat it as an unresolved link, which is the correct signal that a new compendium entry is owed.

## Dialogue

NPC speech is rendered as italicised quoted text, never as a screenplay line:

> Good. He smiled faintly. *"Don't ever do that again,"* he said. The tone was not anger.

Alaric's own thoughts may be paraphrased or, rarely, quoted in italics for emphasis (*"Use me,"* the stone said).

## Images

- Embed images with `![[filename.jpg]]` on their own line, surrounded by blank lines.
- Place them at the moment in the narrative where Alaric would have seen them, not in a gallery at the end.
- Use exactly the filenames the user provides. Do not invent filenames.

## Scene Breaks and Headings

- Use a literal `---` line, surrounded by blank lines, to separate scenes — the moment of a journey segment, a vision, a combat, a conversation, an aftermath.
- For longer or more analytical sessions (e.g. Sessions 13, 14, 17), `##` or `###` headings may title each scene (e.g. `### The Reading`, `## Hendrik's House`). Use headings when:
  - the session contains more than ~5 scene breaks, OR
  - the user's notes are already organised into named beats.
- For shorter or more flowing sessions (Sessions 0, 10, 11, 12, 15, 16), prefer plain `---` breaks without headings.
- Combat scenes commonly use `## The Engagement` / `# Encounter begins` followed by an `Initiative Order:` line and per-actor paragraphs, then a closing `## Aftermath` or `### Aftermath` heading.

## Opening Hook

The first paragraph after the frontmatter should be a single short reflective line or a brief framing observation, not a "Today we…" recap. Examples drawn from the canonical sessions:

- *"I record this entry while the memory is still warm, because I have already learned that visions of this kind do not survive a full night of sleep intact."*
- *"I slept poorly. That is becoming a pattern I will need to address before it becomes a condition."*
- *"We came again to the gallows."*
- *"The mists do not merely obscure—they mute. Sound, certainty, even reason seem dulled beneath their veil."*

## Closing Reflection

Every session must end with a reflective beat — one of:

- a single sentence of foreboding or resolve (*"Caution remains insufficient. But it is all we have."*);
- a short paragraph of synthesis (*"That, more than anything I saw today, is what I intend to avoid."*);
- a numbered/bulleted **Observations / Conclusion / Private Notes** section listing unresolved threads, persons, established facts — but only if the session warrants analytical closure (combat-heavy or revelation-heavy sessions).

Do not end on dialogue or on mid-action. The journal always returns to Alaric reflecting.

### Optional analytical appendix

For tactically dense sessions, an optional appendix may be added after a final `---`, structured as:

```markdown
**Private Notes**
**Persons**
- **[[Name]]** — short evaluation.

**Established**
- Fact 1.

**Unresolved**
- Question 1.
```

Use this only when the user's notes contain enough material to populate at least two of the three blocks.

## DM Debrief

At the end of each session the DM poses one or more questions to Alaric's player about the character — typically introspective prompts ("What did Alaric learn tonight?", "What does he fear now that he did not fear before?", "What memory surfaced unbidden?"). These are not in-fiction conversations; they are debrief prompts. The journal records them as a closing appendix in which Alaric answers each one in his own voice.

Render this section **after** the reflective close (and after any `**Private Notes**` appendix, if present), separated by a `---`, structured exactly as follows:

```markdown
---

## DM Debrief

> *The DM's question, quoted verbatim.*

<Alaric's first-person answer — one short paragraph in the same reflective ledger voice as the rest of the journal. Two paragraphs at most.>

> *Second question, if any.*

<Answer.>
```

Rules:

- Each question is rendered as a Markdown blockquote in italics, quoting the DM's wording verbatim (lightly tidied for punctuation only).
- Each answer is a plain paragraph immediately beneath its question, written in first person as Alaric. The same restraint, hedged certainty, and scholarly tone apply.
- Do not paraphrase the question into in-fiction language. Keep it as the meta prompt it was; only the answer is in-character.
- If the user answers "none this session", omit the entire `## DM Debrief` block — do not leave an empty heading.

## Workflow

When invoked:

1. **Ask the user, before doing anything else**, for the session number, the in-fiction date, and the DM's end-of-session questions (see the very top of this skill). Do not proceed until all three answers are received.
2. Skim the raw notes and identify scene boundaries (travel, conversation, combat, aftermath, vision, reflection).
3. Identify every named entity and assign it a wiki link target. If unsure, link anyway.
4. Identify every emotional beat the user provided and weave it into the reflective register — never as a bald "Alaric was scared", always as observation or aftermath.
5. Draft the file following the skeleton above.
6. Before writing to disk, verify:
   - Frontmatter is exactly the three lines (tags, date) inside `---` fences.
   - Every name has at least one wiki link in the file.
   - Every image filename from the input appears as `![[…]]`.
   - All mechanics are parenthesised or embedded in prose.
   - The opening hook is reflective, not expository.
   - The closing beat is reflective, not action.
   - `---` scene breaks are surrounded by blank lines.
   - If DM questions were provided, the `## DM Debrief` block is present at the very end of the file, after any other appendix, with each question as a blockquote and each answer as a first-person paragraph.
7. Write the file with the `create` tool (never overwrite without explicit confirmation).
8. Report briefly to the user: file path, scene count, any names that were linked but have no compendium entry yet (so they know what stubs to create).

## Examples to Imitate

Read these files for tone calibration before drafting (in this order of priority):

1. `sessions/Session 15.md` — canonical mid-length reflective ledger with embedded wiki links.
2. `sessions/Session 16.md` — long flowing investigation entry with a closing **Private Notes** appendix.
3. `sessions/Session 11.md` — combat-heavy session with `## The Engagement` / `## Aftermath` and `Initiative Order:`.
4. `sessions/Session 13.md` — analytical session with `###` subheadings per Tarokka card.
5. `sessions/Session 0.md` — solo introspective vision-heavy opening session.

Do not deviate from this established voice. The unity of the journal is the point.
