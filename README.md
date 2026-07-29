# Learning Games

Research and prototypes for ESL learning games — browser-based games that borrow the
best dynamics from modern word games (Contexto, Wordle, Connections, …) and adapt
them for English learners.

## What's here

| Path | Contents |
|------|----------|
| `research/game-dynamics.md` | The main catalog: why Contexto works, 12 adaptable game dynamics, ESL design principles, and engagement meta-mechanics |
| `research/prototype-shortlist.md` | Ranked build candidates with effort estimates and tech notes |
| `prototypes/` | Playable prototypes (to come) |

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
