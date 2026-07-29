# Prototype Shortlist

Ranked by (ESL value × novelty) ÷ build effort. All are static-site friendly except #4.

## 1. Collocation Connections — *build first*

Connections-style 4×4 grid where groups encode collocations, phrasal verbs, irregular
forms, register — not just topics. Post-solve micro-lesson note per group.

- **Why first:** highest teaching value per hour of work; the tech is a static page
  reading a JSON puzzle file; all effort goes into *content*, which is exactly the
  part a teacher can author and iterate on. Playable in class (projector) on day one.
- **Tech:** plain HTML/JS/CSS, one `puzzles/YYYY-MM-DD.json` per day. No backend.
- **Effort:** ~1 day for the game + a puzzle-authoring format; puzzles thereafter are
  content work.
- **Open question:** puzzle authoring pipeline — hand-written JSON vs. a small
  generator that drafts groups from a collocation list for teacher review.

## 2. Close Words (Contexto for learners)

Semantic-similarity daily word game with CEFR-banded targets, hint ladder, and a
post-game "nearest neighbors" vocabulary harvest.

- **Why:** it's the requested reference mechanic, and the ESL adaptations (level
  banding, hint ladder, neighbor harvest) make it meaningfully different from Contexto.
- **Tech:** embeddings computed **offline** (Python + fastText or
  `sentence-transformers`) over a ~5k learner vocabulary; ship one static JSON of
  `word → rank` per puzzle (a 5k-word rank table is ~50–100 KB). The site stays static.
- **Effort:** ~2–3 days (offline pipeline + game UI). Guess normalization
  (plurals, verb forms → lemma) is the main gotcha — lemmatize offline and ship an
  inflection→lemma map.

## 3. Cloze Reveal (graded Redactle)

A 100–150-word graded text, every content word hidden; guess words to reveal them;
identify the topic. Function words pre-revealed.

- **Why:** trains reading/prediction, works brilliantly as a team projector game.
- **Tech:** static; each puzzle is just a text + level tag. Reveal-matching should be
  lemma-aware (guessing "run" reveals "running").
- **Effort:** ~1–2 days. Content = any graded text you already use in class.

## 4. Question Master (20 Questions with grammar feedback)

Player asks typed yes/no questions to an AI to identify a hidden word; malformed
questions get a gentle inline correction instead of an answer.

- **Why:** question formation is chronically under-practiced; nothing on the market
  does this well.
- **Tech:** needs an LLM API (Claude) → requires a small serverless proxy for the API
  key, or class use via a shared session. Not static — build after 1–3 prove the format.
- **Effort:** ~3–4 days including prompt design for the answerer/corrector roles.

## Deferred (good, but later)

- **Semantic ladder** (novel mechanic, needs embedding UX experimentation)
- **Minimal-pair audio game** (needs curated audio or careful TTS)
- **Dialogue scramble** (solid but lower novelty; easy to add to the stable later)
- **AI role-play NPC** (highest ceiling, highest effort — after Question Master proves
  the LLM plumbing)
