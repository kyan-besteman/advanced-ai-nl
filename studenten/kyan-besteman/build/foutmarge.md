# Foutmarge, 21 oktober 2026

Model: `claude-opus-5-5` (hetzelfde model als mijn testset, zie `kosten.md`). n = 10 inputs (T01–T10 uit `test-set.md`), 3 runs per versie. Zelfde inputs voor beide versies.

**Hoe ik het draaide:** elke run in een nieuwe sessie (`claude -p --model claude-opus-5-5 --tools ""`), zonder tools en zonder mijn `context.md` of `CLAUDE.md`. De prompt is alles onder de eerste streep van `prompt-v1.md` en `prompt-v2.md`, met de input ingevuld. De verwachte antwoorden zijn niet aangepast nadat ik de uitvoer zag.

**Wat ik scoor:** het label. Per run: het aantal van de 10 inputs waar het label juist is. De velden (naam, abonnement, online aankoop, datum) tel ik hier niet mee. Mijn testset geeft van de meeste inputs geen verwachte waarde voor die velden.

## Score per run

| Versie | Run 1 | Run 2 | Run 3 | Laagste | Hoogste |
|---|---:|---:|---:|---:|---:|
| v1 | 7/10 | 7/10 | 6/10 | **6** | **7** |
| v2 | 8/10 | 8/10 | 8/10 | **8** | **8** |

## Per input

1 = label juist, 0 = fout. v1 en v2 elk in run 1 / 2 / 3.

| ID | Verwacht label | v1 | v2 |
|---|---|---|---|
| T01 | online ticket niet getoond | 1 · 1 · 1 | 1 · 1 · 1 |
| T02 | abonnement vergeten | 0 · 0 · 0 (`onzeker`) | 1 · 1 · 1 |
| T03 | andere | 1 · 1 · 1 | 1 · 1 · 1 |
| T04 | ticket te laat gekocht | 0 · 0 · 0 (`onzeker`) | 0 · 0 · 0 (`onzeker`) |
| T05 | geen geldig vervoersbewijs | 0 · 0 · 0 (`andere`) | 1 · 1 · 1 |
| T06 | onzeker | 1 · 1 · 1 | 1 · 1 · 1 |
| T07 | onzeker | 1 · 1 · 1 | 1 · 1 · 1 |
| T08 | no cash aan boord | 1 · 1 · 0 (`onzeker`) | 0 · 0 · 0 (`onzeker`, `onzeker`, `abonnement vervallen`) |
| T09 | kortingskaart vergeten | 1 · 1 · 1 | 1 · 1 · 1 |
| T10 | abonnement vervallen | 1 · 1 · 1 | 1 · 1 · 1 |

## Mijn claim

Uit week 3: prompt v2 labelt beter dan v1. T02 gaf in v1 twee keer `onzeker` en in v2 twee keer het juiste label. (Zo las ik de claim. Klopt dat niet, dan pas ik het aan.)

**Volgens de regel uit de README: bevestigd.** De laagste score van v2 (8) ligt hoger dan de hoogste van v1 (7).

**Mijn advies: ingetrokken**, om twee redenen die ik hieronder uitleg.

**Mijn beslissing (21 oktober 2026): ingetrokken.**

### Waarom de uitslag wankel is

1. **T05 is na de v1-runs aangepast.** In `test-set.md` stond het juiste antwoord eerst op `andere`. Ik zette het op `geen geldig vervoersbewijs` vóór de v2-runs, en dat is in het logboek genoteerd. Met het oude antwoord `andere` wordt v1 7–8 en v2 7–7. Dan overlappen de bereiken, en de claim is ingetrokken. Ik heb hier de antwoorden uit het huidige testset gebruikt.

2. **v2 is gemaakt met T02 en T05.** Die twee inputs zijn de fouten van v1 waarvoor ik regels heb toegevoegd. Dat is geen onafhankelijk bewijs. Zonder T02 en T05 (8 inputs):
   - v1: 7, 7, 6 → 6–7
   - v2: 6, 6, 6 → 6–6
   
   Dan is er geen verschil meer dat buiten de foutmarge valt.

### Extra: T08 blijft een probleem

v2 geeft T08 in alle drie de runs fout (`onzeker`, `onzeker`, `abonnement vervallen`). In v1 was dat 1 keer fout. Dat is een nieuwe fout die v2 erbij heeft, en de regel uit v2 heeft die niet opgelost.

## Wat ik hieruit meeneem

- Het verschil tussen v1 en v2 zit vooral in T02 en T05. Die zijn voor v2 geschreven, dus die bewijzen weinig.
- Voor v3: een testset die ik niet gebruik om regels te schrijven. Anders test ik alleen mijn eigen antwoorden.
- De foutmarge van v2 is 0 punten (8–8). Dat klinkt goed, maar met 3 runs zegt dat weinig: drie keer dezelfde score is niet hetzelfde als altijd goed.
