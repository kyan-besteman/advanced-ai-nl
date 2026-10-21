# Modellen, 21 oktober 2026

## Mijn gok

_Geschreven ná de test, nadat ik de uitslag al gezien had._

Ik dacht dat Opus het beste zou scoren, omdat het het duurste en beste model is. Daarna Sonnet, dan Haiku. Omdat deze prompt niet zo moeilijk is, dacht ik dat alle modellen ongeveer hetzelfde zouden scoren. Als één model minder goed zou zijn, dacht ik aan Haiku, omdat dat heel goedkoop is.

## Resultaat

Prompt: `prompt-v2.md` (alles onder de eerste streep, met de input ingevuld). n = 10 inputs (T01–T10 uit `test-set.md`), 1 run per setup.

**Hoe ik het draaide:** zoals de foutmargetest. Elke run in een nieuwe sessie (`claude -p --model <model> --tools ""`), zonder tools en zonder mijn `context.md` of `CLAUDE.md`. De verwachte antwoorden zijn niet aangepast nadat ik de uitvoer zag.

**Wat ik scoor:** het label, net als in `foutmarge.md`. De velden tel ik niet mee.

| Setup | Model | Effort | Score | Gem. output-tokens per run |
|---|---|---|---:|---:|
| A | `claude-sonnet-5-5` | medium | **7/10** | 176 |
| B | `claude-haiku-5-5` | standaard (geen `--effort`) | **8/10** | 620 |
| C | `claude-opus-5-5` | standaard (geen `--effort`) | **8/10** | 347 |

Output-tokens komen uit `usage.output_tokens` van elke run. Daar zit het denkwerk van het model mee in, niet alleen het antwoord dat je ziet.

## Per input

1 = label juist, 0 = fout (met het label dat het model gaf).

| ID | Verwacht label | A (Sonnet) | B (Haiku) | C (Opus) |
|---|---|---|---|---|
| T01 | online ticket niet getoond | 1 | 1 | 1 |
| T02 | abonnement vergeten | 1 | 1 | 1 |
| T03 | andere | 0 (`onzeker`) | 1 | 1 |
| T04 | ticket te laat gekocht | 0 (`geen geldig vervoersbewijs`) | 0 (`onzeker`) | 0 (`onzeker`) |
| T05 | geen geldig vervoersbewijs | 1 | 1 | 1 |
| T06 | onzeker | 1 | 1 | 1 |
| T07 | onzeker | 1 | 1 | 1 |
| T08 | no cash aan boord | 0 (`onzeker`) | 0 (`abonnement vervallen`) | 0 (`onzeker`) |
| T09 | kortingskaart vergeten | 1 | 1 | 1 |
| T10 | abonnement vervallen | 1 | 1 | 1 |
