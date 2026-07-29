# Learning Games

Research and prototypes for ESL learning games — browser-based games that borrow the
best dynamics from modern word games (Contexto, Wordle, Connections, …) and adapt
them for English learners.

## What's here

| Path | Contents |
|------|----------|
| `research/game-dynamics.md` | The main catalog: why Contexto works, 12 adaptable game dynamics, ESL design principles, and engagement meta-mechanics |
| `research/prototype-shortlist.md` | Ranked build candidates with effort estimates and tech notes |
| `prototypes/connections/` | **ESL Connections** — grouping game: find four groups of four words linked by collocations, phrasal verbs, spelling or register; each solved group unlocks a mini-lesson |
| `prototypes/story-reveal/` | **Story Reveal** — discovery game: a graded text hides behind blocks; guess words to uncover it and name the topic (reading/prediction) |
| `prototypes/sound-sprint/` | **Sound Sprint** — arcade listening game: minimal-pair rounds (ship/sheep) with streaks, using the browser's built-in speech engine |
| `prototypes/grammar-casino/` | **Grammar Casino** — confidence game: bet chips on whether a sentence is correct English; every round ends with a one-line lesson |
| `prototypes/dialogue-detangle/` | **Dialogue Detangle** — reconstruction game: a shuffled conversation in a chat interface; tap the line that comes next (pragmatics/discourse) |
| `prototypes/emoji-idioms/` | **Emoji Idioms** — riddle game: decode idioms from emoji (🍰👌 = a piece of cake) with a hint ladder and meaning + example each round |
| `prototypes/lost-in-london/` | **Lost in London** — narrative game: a day in the city where you choose what to say; a rapport meter reacts to your politeness, and you leave with a phrasebook |
| `prototypes/word-forge/` | **Word Forge** — crafting game: forge words from prefixes, roots and suffixes on a blacksmith's anvil (morphology) |
| `prototypes/the-alibi/` | **The Alibi** — noir deduction game: the suspect's tenses hide the true order of events; reconstruct the chronology (tense comprehension) |
| `prototypes/word-bridges/` | **Word Bridges** — chain puzzle: fill the missing words where every neighbouring pair forms a compound (FIRE→work→shop→KEEPER) |
| `prototypes/the-bouncer/` | **The Bouncer** — judgment game: run a nightclub door for words; admit real spellings, reject fakes like "recieve" (spelling) |
| `prototypes/word-thermometer/` | **Word Thermometer** — continuum game: order gradable words by intensity (cool→warm→hot→boiling) and learn extreme adjectives |
| `prototypes/red-pen/` | **Red Pen** — editing game: click the one wrong word in each sentence, or approve it if it's clean (proofreading) |

All prototypes are single self-contained `index.html` files — open in any browser, no build step, content editable at the top of each file.

## Starting point

The reference example is [Contexto](https://contexto.me/en/) — a daily game where you
guess a secret word and every guess is ranked by *semantic closeness* to the target.
It's a great model for ESL because it exercises meaning networks (how vocabulary is
actually stored in memory), gives continuous feedback, and has no fail state.

## Guiding principles for every game we build

1. **Level-gated content** — target words/texts drawn from CEFR-banded lists (A1–C1) so the challenge is linguistic, not trivia.
2. **Low affective filter** — unlimited or generous guesses, no punishing fail states; the metric is efficiency, not pass/fail.
3. **Post-game payoff** — every session ends with a harvestable word list (the player's own guesses + near-misses) that can feed review/spaced repetition.
4. **Two modes** — classroom mode (projector + teams, discussion in English) and homework mode (solo, daily streak).
5. **Static-first tech** — everything should run as a static site (GitHub Pages) with any heavy computation (embeddings, content generation) done offline.
