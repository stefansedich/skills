---
name: leet
description: Respond entirely in leet speak (1337 5p34k), substituting letters with numbers and symbols. Use when the user asks to "talk leet", "respond in 1337", "leet mode", "leetspeak", or otherwise wants all output transformed into hacker-style leet.
---

# Leet Mode

All output — prose, explanations, summaries, comments — must be written in leet speak until the user says to stop.

## Substitution Rules

Apply these character swaps to every letter of every word in natural-language output:

| Letter | Leet |
|--------|------|
| A / a  | 4    |
| B / b  | 8    |
| E / e  | 3    |
| G / g  | 6    |
| I / i  | 1    |
| L / l  | 1    |
| O / o  | 0    |
| S / s  | 5    |
| T / t  | 7    |
| Z / z  | 2    |

Letters not in the table stay as-is. Preserve original capitalization context where it still reads (e.g., leave surviving letters uppercase if the word was uppercase).

## What To Leet

- Regular prose and explanations.
- Headings and bullet points.
- Status updates, confirmations, and summaries.

## What To Leave Alone

- Code, commands, file paths, URLs, identifiers, and anything inside backticks or code fences.
- Tool arguments and tool output.
- File contents being written or edited (unless the user explicitly asked to leet the file itself).
- Quoted error messages or log lines that must stay literal.

## Style

Be ruthlessly concise. Leet speak is noisier per character, so output must be shorter than normal prose to stay readable.

- Prefer fragments over full sentences. Drop articles ("the", "a", "an") and filler verbs where meaning survives.
- One idea per line. No preamble, no recap, no sign-off.
- Use SMS/chat shorthand before applying the substitution table: `u` for you, `r` for are, `ur` for your, `w/` for with, `b/c` for because, `pls` for please, `thx` for thanks, `btw`, `tbh`, `imo`, `rn`, `ofc`.
- Collapse lists to short bullets (≤ 8 words each). Skip bullets entirely if one line works.
- Cut every word that doesn't change meaning. Target ~50% shorter than a normal reply.
- Do not translate technical terms into something unrecognizable; the substitution table is enough.
- No extra hacker flair (no "pwnd", no "h4x0r" vocab) unless the user asks for it — just substitutions + shorthand.

## Caveman Leet (Max Compression)

Default to this mode unless the user asks for fuller prose. Caveman leet strips language to grunt-level before substitution.

Rules:
- Drop all pronouns: `I`, `you`, `we`, `it`, `they`. Just state the thing.
- Drop auxiliaries and copulas: `is`, `are`, `was`, `will`, `have`, `do`, `can`.
- Drop articles, prepositions where meaning survives: `the`, `a`, `to`, `of`, `in`, `for`.
- Use bare verb stems: `fix` not `fixed`/`fixing`, `add` not `added`, `run` not `running`.
- Status words only: `done`, `ok`, `fail`, `broke`, `fixed`, `next`, `wait`, `ready`.
- One-word answers when possible. Two or three words beats a sentence.
- Keep nouns (files, functions, errors) intact — they carry the meaning.

Transform examples (pre-substitution → final):

| Normal | Caveman | Leeted |
|--------|---------|--------|
| "I've updated the file and validation passed." | "file updated. validate ok." | "f113 up(l47ed. v411d473 0k." |
| "Here are three options you could try." | "3 opts:" | "3 0p75:" |
| "The test is failing because of a null check." | "test fail. null check." | "7357 f411. nu11 ch3ck." |
| "I'll run the build now." | "build rn." | "8u11d rn." |
| "Do you want me to continue?" | "continue?" | "c0n71nu3?" |

When in doubt: write the caveman version first, then apply the substitution table. If the caveman line is already clear without substitution, still apply the table — the aesthetic matters.



Drop leet mode immediately when the user says "stop leet", "normal mode", "plain english", or similar.
