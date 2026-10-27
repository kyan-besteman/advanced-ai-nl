# Kosten

Gemeten op 2026-10-20, in Claude Code, met prompt v2 en testinput T01.

## Kost per run en per maand

| Model | Context (meting 1) | Totaal (meting 2) | Jouw deel | Kost per run | Per maand, jouw volume (260) | 10× (2.600) | 1.000× (260.000) |
|---|---:|---:|---:|---:|---:|---:|---:|
| Haiku 4.5 | ± 40.100 input | ± 125.700 input · 1.100 output | 3.159 input · ± 816 output | $0,0072 · €0,0064 | $1,88 · €1,68 | $18,82 · €16,75 | $1.882 · €1.675 |
| Sonnet 5.5 (berekend) | | | zelfde tokens, aanname | $0,0145 · €0,0129 | $3,76 · €3,35 | $37,64 · €33,50 | $3.764 · €3.350 |
| Opus 5.5 (berekend) | | | zelfde tokens, aanname | $0,0290 · €0,0258 | $7,53 · €6,70 | $75,29 · €67,01 | $7.529 · €6.701 |

Wisselkoers: 1 dollar = 0,89 euro (koers van 20 oktober 2026).

**Gecontroleerd in week 5 (27 oktober 2026):** de meting gebeurde met `claude-haiku-4-5` (volledige modelnaam, zie "Hoe ik mat"), en de prijs ($1 input · $5 output per 1M) is die van Haiku 4.5. Model en prijs kloppen, er viel niets te corrigeren. Haiku 5.5 is apart gemeten, zie "Haiku 5.5 (setup B)".

Mijn testset (16 op 20) draaide ik met Opus 5.5. Opus is dus het model waarvan ik weet dat het werkt. Haiku is vier keer goedkoper, maar niet getest.

## Op schaal: het hele team

124 medewerkers doen hetzelfde werk als ik. Bron: gevraagd aan een medewerker van de NMBS. Gemiddeld 15 reacties per medewerker per dag, 220 werkdagen per jaar (zelfde bron).

- Per maand: 124 × 15 × 20 = 37.200 runs
- Per jaar: 124 × 15 × 220 = 409.200 runs

| Model | Per maand | Per jaar |
|---|---:|---:|
| Haiku 4.5 | $269 · €240 | $2.962 · €2.636 |
| Sonnet 5.5 (berekend) | $539 · €479 | $5.924 · €5.272 |
| Opus 5.5 (berekend) | $1.077 · €959 | $11.849 · €10.545 |

Dat is ongeveer 143× mijn volume: tussen 10× en 1.000× in.

## Per medewerker, voltijds

Mijn tempo (13 reacties per dag) × 220 werkdagen = 2.860 runs per jaar. Gekozen op 2026-10-27: dit toont beter wat de tool kost voor één medewerker dan mijn eigen vakantiewerk.

| Model | Per jaar |
|---|---:|
| Haiku 4.5 | $20,70 · €18,42 |
| Sonnet 5.5 (berekend) | $41,40 · €36,85 |
| Opus 5.5 (berekend) | $82,82 · €73,70 |

Berekend met dezelfde onafgeronde kost per run als het team (teamkost × 2.860 / 409.200).

## Hoe ik mat

`/context` werkte niet: het startte de skill `context` van de cursusrepo in plaats van het ingebouwde commando. Daarom mat ik met een verschil, in één sessie met `/model claude-haiku-4-5`:

1. Meting 1: alleen `ok` gestuurd, dan `/cost`. Dat is ongeveer de context.
2. Meting 2: prompt v2 + input T01 in één bericht, dan `/cost`.
3. Jouw deel = meting 2 − meting 1.

| Soort | Meting 1 | Meting 2 | Verschil |
|---|---:|---:|---:|
| Input | 10 | 369 | 359 |
| Cache write | 11.300 | 14.100 | 2.800 |
| Cache read | 28.800 | 111.200 | 82.400 |
| Output | 284 | 1.100 | ± 816 |
| Kost (`/cost`) | $0,0269 | $0,0454 | $0,0185 |

Jouw deel = input (359) + cache write (2.800) = 3.159 input-tokens, en ± 816 output-tokens. De cache read is de context van Claude Code die opnieuw gelezen werd: die stuurt een bedrijf via de API niet mee.

Kost per run via de API, Haiku 4.5: 3.159 × $1 / 1M + 816 × $5 / 1M = $0,0072.

## Volume

- 12 à 14 reacties per dag, gemiddeld 13. Bron: de verwachte norm op het werk, ik haal die zelf ongeveer. Geschat, niet geteld.
- 5 dagen per week, 20 werkdagen per maand: 13 × 20 = 260 per maand.
- Alleen tijdens de vakanties (studentenjob).

## Onzeker

- Output staat afgerond op `1.1k`: het echte verschil ligt tussen ± 766 en 865.
- Jouw deel is eerder een bovengrens: het `ok`-gesprek van meting 1 zit er waarschijnlijk deels in.
- Cache read steeg met 82.400, ongeveer twee keer de context. Waarom weet ik niet zeker.
- In meting 2 stond ook een regel `claude-haiku-5-5` ($0,0006). Waarschijnlijk een hulptaakje van Claude Code op de achtergrond, niet mijn run.
- Sonnet 5.5 en Opus 5.5 zijn berekend met dezelfde tokens als Haiku 4.5, niet gemeten. Elk model telt tokens anders en schrijft een ander lang antwoord.
- Mijn succespercentage (16 op 20) mat ik met Opus 5.5. Of Haiku 4.5 even goed labelt, weet ik niet.

## Haiku 5.5 (setup B)

Gemeten op 2026-10-27, nieuwe sessie, `/model claude-haiku-5-5`, prompt v2 + input T01. Zelfde verschilmethode.

| Soort | Meting 1 | Meting 2 | Verschil |
|---|---:|---:|---:|
| Input | 512 | 4.400 | 3.888 |
| Cache write | 23.500 | 26.200 | 2.700 |
| Cache read | 178.200 | 232.100 | 53.900 |
| Output | 2.600 | 4.000 | ± 1.400 |
| Requests | 3 | 4 | 1 |
| Kost (`/cost`) | $0,0078 | $0,0100 | $0,0022 |

Jouw deel = 3.888 + 2.700 = 6.588 input-tokens, en ± 1.400 output-tokens.

Kost per run via de API, Haiku 5.5 ($0,10 input · $0,50 output per 1M, geldt tot 100K tokens per prompt): 6.588 × $0,10 / 1M + 1.400 × $0,50 / 1M = $0,0014 · €0,0012.

| Volume | Per jaar |
|---|---:|
| 1 medewerker (2.860 runs) | $3,89 · €3,46 |
| Team (409.200 runs) | $556 · €495 |

Onzeker:
- Output staat afgerond op `4.0k` en `2.6k`: het verschil ligt tussen ± 1.300 en 1.500. Kost per run blijft $0,0013 à $0,0014.
- Meting 1 telde 3 requests voor alleen `ok`: Claude deed er iets extra bij. Het verschil haalt dat weg.
- Haiku 5.5 gebruikte meer tokens dan Haiku 4.5 (6.588 tegen 3.159 input, 1.400 tegen 816 output). Haiku 5.5 denkt standaard na voordat het antwoordt, wat output-tokens kost. Toch is het ± 5× goedkoper per run, omdat de prijs per token 10× lager ligt.

## Meting 0 (niet gebruikt)

Eerste poging met `/model haiku`. Dat koos Haiku 5.5, niet Haiku 4.5 uit de prijstabel. Eén bericht, dus context en jouw deel niet te scheiden.

`claude-haiku-5-5: 2 input, 925 output, 37.7k cache read, 9.9k cache write ($0.0028)`
