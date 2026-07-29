# ESL Connections (prototype 1)

A Connections-style game where the four groups encode *language patterns* —
collocations, phrasal verb particles, irregular past forms, silent letters,
register — and solving a group unlocks a one-line mini-lesson.

## Run it

Open `index.html` in any browser. No server, no build step, no dependencies.
It works from a double-click, a shared drive, or GitHub Pages.

- The puzzle changes daily (date-based rotation), or pick one from the dropdown.
- `?p=3` in the URL jumps straight to puzzle 3 — handy for assigning a specific
  puzzle to a class.
- **Projector mode** button enlarges everything for the classroom.

## Rules

Standard Connections: select 4 words, submit. Four mistakes allowed; "One away…"
tells you three of your four were right. When the game ends (win or lose) all
groups and their mini-lessons are revealed, plus a spoiler-free emoji result to
copy and share.

## Writing your own puzzles

Puzzles live at the top of `index.html` in the clearly marked `PUZZLES` block.
Each puzzle looks like this:

```js
{
  title: "Collocations: make, do, take, have",
  level: "B1",
  groups: [
    { name: "MAKE a/some ___",                    // shown when solved
      words: ["decision", "mistake", "noise", "progress"],
      note: "We MAKE decisions, mistakes, ..." }, // the mini-lesson
    // ...three more groups, easiest first (yellow → green → blue → purple)
  ]
}
```

Authoring guidelines:

1. **All 16 words must be different** within one puzzle.
2. **Order groups easiest → hardest.** Yellow should be gettable by the whole
   class; purple can hide a trap.
3. **Build in one trap.** The best puzzles have a word that *looks* like it
   belongs to another group ("break" tempts HAVE, belongs to TAKE). Mention the
   trap in the note — that's where the learning lands.
4. **Keep notes to 1–2 sentences.** They appear at the moment of the "aha", so
   short beats complete.
5. Good group types: collocations (make/do/take/have, verb+noun), phrasal verbs
   by particle, irregular past patterns, silent letters, word stress, register
   (formal/informal), prepositions after adjectives (afraid *of*, good *at*),
   countable/uncountable, British/American pairs.
