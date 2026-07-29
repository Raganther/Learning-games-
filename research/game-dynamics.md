# Game Dynamics for ESL Learning Games

Research notes, July 2026. Reference example: [Contexto](https://contexto.me/en/).

## Part 1 — Why Contexto works

Contexto is a daily game: there is one secret word, you type guesses, and every guess
gets a **rank** — its position in a list of the entire vocabulary ordered by semantic
similarity to the target (computed offline with word embeddings / cosine similarity).
Rank 1 is the answer; rank 30 means "very close in meaning"; rank 5,000 means "cold."

Five design decisions make it compelling, and all five matter for ESL:

1. **Continuous feedback gradient.** Every single guess returns information. There is
   no dead turn — even a bad guess tells you which semantic region to abandon. This is
   the "warmer/colder" mechanic scaled to the whole vocabulary. For learners, it means
   every attempt is rewarded with signal, not judgment.

2. **Meaning, not spelling.** "Dog" and "puppy" share no letters but rank next to each
   other. The game exercises the *semantic network* — synonyms, hypernyms, collocates,
   associations — which is exactly how the mental lexicon stores vocabulary. Most word
   games test orthography; this one tests the thing ESL vocabulary teaching actually
   targets.

3. **No fail state.** Unlimited guesses; everyone eventually solves it. The score is
   *how many guesses it took*, so the competition is about efficiency, not survival.
   This keeps the affective filter low — weak students still finish.

4. **Daily ritual + shareable result.** One puzzle per day, same puzzle for everyone,
   a spoiler-free shareable summary (guess count). Streaks and shared results drive
   retention without any account system.

5. **Emergent strategy is a language skill.** The optimal strategy — start with broad
   category words ("animal", "place", "action"), then narrow with synonyms — is
   literally a vocabulary-organization exercise. The game teaches players to think in
   semantic hierarchies.

### ESL adaptation of Contexto itself ("Close Words")

- **Level-banded targets:** pick secret words from CEFR lists (A1/A2/B1/B2) so the
  answer is always inside the learner's reachable vocabulary. Rank guesses against a
  learner-sized vocabulary (~5k words), not all of English — ranks become meaningful.
- **Progressive hints:** after N guesses, offer the definition → an example sentence
  with a blank → the first letter. Hints cost guesses, so they're a trade, not a crutch.
- **Post-game harvest:** after solving, show the top-20 nearest neighbors of the
  target with definitions. The player's own guess history *is* a personalized semantic
  map — export it as a review list.
- **Classroom mode:** puzzle on the projector, teams alternate guesses, teams must
  justify each guess in English ("I think it's related to weather because…"). The
  justification is where the speaking practice happens.

## Part 2 — Catalog of adaptable dynamics

Each entry: the core mechanic → what it trains → the ESL twist that makes it more
than a clone.

### 1. Semantic proximity (Contexto, Semantle)
- **Mechanic:** guesses ranked by embedding similarity to a hidden word.
- **Trains:** semantic networks, synonyms/hypernyms, category thinking.
- **ESL twist:** level-banded vocab, hint ladder, post-game neighbor list (above).

### 2. Letter-position deduction (Wordle)
- **Mechanic:** fixed guesses, per-letter green/yellow/gray feedback.
- **Trains:** spelling, orthographic patterns, common letter sequences.
- **ESL twist:** the clue is a *definition or picture*, and the grid confirms the
  spelling — flipping it from "guess an arbitrary word" to "you know the word, now
  spell it." Targets the classic ESL gap between oral vocabulary and spelling.

### 3. Grouping / semantic fields (NYT Connections)
- **Mechanic:** 16 words, find four groups of four; limited mistakes.
- **Trains:** this is the highest-value mechanic for ESL because groups can encode
  *any* linguistic pattern, not just meaning:
  - collocations: things you *make* (a decision, a mistake, noise, progress) vs things you *do*
  - phrasal verbs sharing a particle (give **up**, look **up**, make **up**, turn **up**)
  - irregular past forms, silent letters, minimal pairs, word stress patterns
  - register: formal vs informal synonyms
- **ESL twist:** after solving, each group gets a 1-line grammar/usage note — the
  "aha" moment becomes a micro-lesson. Content is pure authoring (a JSON file per
  puzzle); tech is trivial.

### 4. Constrained construction (Spelling Bee, Waffle, anagrams)
- **Mechanic:** build valid words from limited letters / rearrange a grid.
- **Trains:** morphology, spelling, productive vocabulary recall.
- **ESL twist:** score bonuses for words from the current unit's word list; accept
  only words the learner's level should know (avoids the Scrabble problem of obscure
  words beating real vocabulary).

### 5. Chain / ladder (Weaver, word-association chains)
- **Mechanic:** transform word A into word B one step at a time (one letter, or one
  association, per step).
- **Trains:** spelling (letter version) or fluency of association (semantic version).
- **ESL twist:** *semantic* ladders judged by embeddings — get from "cold" to "beach"
  in the fewest associated-word steps, each hop validated by similarity threshold.
  Novel mechanic, very ESL-native (mirrors classroom memory-chain games).

### 6. Cloze reveal (Redactle-style)
- **Mechanic:** a text with every word hidden; guess words to reveal all their
  occurrences; goal is to identify the topic/title.
- **Trains:** reading strategies, function-word awareness, prediction from context —
  the core comprehension skills.
- **ESL twist:** use short graded texts (100–150 words at the class's level); the top
  100 function words start pre-revealed so the game is about *content* prediction.
  Excellent projector/team game.

### 7. Sentence ordering / dialogue scramble
- **Mechanic:** drag scrambled lines into a coherent dialogue or paragraph.
- **Trains:** discourse markers, pragmatics (adjacency pairs: offer→accept/decline),
  cohesion.
- **ESL twist:** score by "moves used" like Waffle; daily dialogue with an audio
  playback reward when solved.

### 8. Audio deduction (Heardle, Morsle)
- **Mechanic:** guess from progressively longer/clearer audio.
- **Trains:** listening; adapted well it targets *minimal pairs* (ship/sheep,
  live/leave) — the highest-pain ESL listening problem.
- **ESL twist:** "Blurred word": a word played through a low-pass filter that
  sharpens with each wrong guess; or classic minimal-pair binary rounds with streaks.
  Browser TTS makes content free to generate.

### 9. Forbidden words / circumlocution (Taboo)
- **Mechanic:** describe a target word without using N banned words.
- **Trains:** circumlocution — the single most useful communication strategy for
  learners (talking around a word you don't know).
- **ESL twist:** digital single-player version: the player types/speaks a description,
  an LLM guesses the word. If the AI guesses it, you win — the AI's guess quality is
  the score. Needs an LLM API, but is a genuinely novel production-practice game.

### 10. Interrogation (20 Questions / Akinator)
- **Mechanic:** narrow down a hidden thing via yes/no questions.
- **Trains:** *question formation* — reliably the weakest structure for most learners,
  because classrooms give little practice asking.
- **ESL twist:** the player must type well-formed questions to an AI answerer; the
  game gently rejects malformed questions with a correction ("Did you mean: *Does it
  live in water?*"). Grammar practice disguised as a guessing game.

### 11. One-word clues (Codenames)
- **Mechanic:** a clue-giver links multiple board words with a single word + number.
- **Trains:** deep semantic/collocational knowledge; the receiving team practices
  justification and negotiation ("'water' could mean 'bottle' or 'river'…").
- **ESL twist:** team classroom game; embeddings can power a solo mode where the AI
  is your teammate and you evaluate its clues (receptive) or it evaluates yours
  (productive).

### 12. Branching dialogue / role-play with an AI NPC
- **Mechanic:** navigate a scenario (ordering food, job interview, complaint) by
  conversing; outcomes branch on what you say.
- **Trains:** pragmatics, functional language, fluency under mild time pressure.
- **ESL twist:** LLM-driven NPC with a rubric (did the player greet, request,
  clarify, close?); post-scene feedback lists better phrasings. Highest effort,
  highest ceiling.

## Part 3 — Engagement meta-mechanics (apply to any of the above)

- **Daily cadence** — one shared puzzle/day creates ritual and classroom talkability
  ("did you get today's?").
- **Streaks** — the strongest retention mechanic in daily games; keep them gentle
  (a "freeze" token) to avoid demotivating breaks.
- **Shareable spoiler-free results** — emoji grids / guess counts; free viral loop and
  a classroom leaderboard without any backend.
- **Unlimited guesses, efficiency scoring** — success guaranteed, mastery visible.
- **Progressive hint ladders** — hints cost score, converting frustration into a
  choice instead of a wall.
- **Team/projector mode** — a toggle that hides personal streaks and enlarges UI;
  turns any solo game into a speaking activity.
- **Spaced-repetition tail** — words a player struggled with re-enter future puzzles
  or a review deck; this is where a game becomes a *learning system*.

## Sources

- [Contexto (contexto.me)](https://contexto.me/en/) — reference game
- [The technology behind contexto.me — Poatek](https://medium.com/@poatek/the-technology-behind-contexto-me-79579cfa9334) — embeddings + cosine similarity ranking
- [Semantle](https://legacy.semantle.com/) — original semantic-similarity daily game
- [Semantic word games explained](https://contexto.uk/semantic-word-games-explained-how-they-work-and-why-they-are-different/)
- [Daily logic word games guide (2025)](https://crosswordle.com/blog/daily-logic-word-games) — survey of daily-puzzle mechanics incl. streak/share design
- [Thinky Games: daily puzzle roundup](https://thinkygames.com/features/tired-of-wordle-and-connections-try-these-6-fun-daily-puzzle-games-that-will-get-you-thinking/) — incl. Morsle (audio deduction)
- [Systematic review: competitive digital gamification in adult ESL — Smart Learning Environments](https://link.springer.com/article/10.1186/s40561-026-00447-z) — effects on vocabulary retention, motivation, engagement
- [TEFL Institute: essential ESL classroom games](https://teflinstitute.com/blog/7-essential-esl-games-list-for-effective-classroom-teaching/) — the four pillars: clear rules, calibrated challenge, linguistic purpose, built-in repetition
