# Week 5: Hoe mijn foutmarge de nettowinst beïnvloedt

## Mijn foutmarge

Ik draaide v1 en v2 elk 3 keer op dezelfde 10 inputs, met Opus 5.5. v1 haalde 7, 7 en 6 op 10 (bereik 6–7), v2 drie keer 8 op 10 (bereik 8–8).

Ik schreef eerst "bevestigd", maar met hulp van de docent veranderde ik dat in "ingetrokken". Na v1 heb ik regels en nieuwe labels toegevoegd, waardoor ik v2 eigenlijk niet zomaar met v1 mag vergelijken. Als ik de twee inputs weglaat waarvoor ik de regels schreef, zie ik dat v2 niet beter scoort dan v1: v1 haalt 6–7, v2 6–6 (n = 8, 3 runs).

T08 verraste me het meest: v1 had hem twee keer van de drie juist, v2 drie keer fout. Het is een moeilijke klantenreactie, omdat er twee labels in passen. Daardoor kan de tool moeilijk kiezen.

Bij v3 doe ik twee dingen anders: ik verander één regel per keer, en ik test op een aparte testset met nieuwe klantenreacties die ik niet gebruik om regels te schrijven.

## Model en effort

Ik testte drie setups met prompt v2, elk 1 run op dezelfde 10 inputs: Sonnet 5.5 met effort medium haalde 7 op 10, Haiku 5.5 en Opus 5.5 elk 8 op 10.

Ik heb de runs uitgevoerd zonder er eerst aan te denken dat ik moest gokken. Die gok maakte ik wel onbewust, maar ik schreef hem pas op nadat ik de resultaten had gezien. Het verraste me dat Haiku even goed scoorde als het beste en duurste model, en één punt hoger dan Sonnet. Dat verschil met Sonnet is maar één input, en elke setup draaide maar 1 keer, dus het valt binnen mijn foutmarge. De vragen die ik de modellen stel zijn niet moeilijk, maar voor die prijs blijft het impressive: Haiku 5.5 kost € 0,0012 per run, Opus 5.5 € 0,0258.

Ik zou Haiku 5.5 gebruiken, omdat mijn taak niet moeilijk is. Voor het hele team kost Haiku 5.5 ± € 495 per jaar, Opus 5.5 ± € 10.545. Dat is ± € 10.000 per jaar minder kosten voor de NMBS.

## Mijn value chain, met de foutmarge erin

| Schakel | Laag (6/10) | Basis (8/10) |
|---|---:|---:|
| Winst bij opzoeken, min draaien en nakijken | 2,4 min | 2,4 min |
| Fouten herstellen (% fout × 3 min) | − 1,2 min | − 0,6 min |
| Winst per reactie | 1,2 min | 1,8 min |
| × € 53,85 per uur (€ 60.000 bruto × 1,5) | € 440.700 | € 661.100 |
| − Haiku 5.5 | − € 495 | − € 495 |
| **Netto per jaar** | **± € 440.000** | **± € 660.600** |

Mijn zwakste cijfer is de opzoekwinst: ± 2 min bij een makkelijke reactie en ± 5 min bij een ingewikkelde. Die heb ik geschat, nooit geklokt. Is die winst maar de helft, dan zakt het netto naar ± € 43.600. Dat is − 93%, terwijl mijn foutmarge het netto maar − 33% laat dalen. Op het werk ga ik 10 reacties zonder de tool en 10 met de tool klokken.

De score van 8 op 10 vertrouw ik ook niet helemaal, omdat ik na v1 regels en nieuwe labels heb toegevoegd zodat de tool begrijpt waarom het fout was.

## Mijn dashboard

https://claude.ai/artifact/WvtreLoSPAyPk439U61Gb9

Wat je eerst moet zien: de score van mijn AI-tool bij de NMBS.

## Mijn AI-ismen

> Week 3: "De labels moeten altijd kloppen, omdat ze je een inzicht geven in wat je precies moet opzoeken of controleren."
> Herschreven: "Het label moet altijd kloppen, want het zegt me waar ik de info moet zoeken: bij een abonnement, een online ticket, …"

> Week 4: "De tool werkt goed bij duidelijke klantenreacties"
> Herschreven: "De tool had 16 op 20 labels juist (n = 10, 2 runs)."

> Week 4: "De velden zijn dus nog in progress."
> Herschreven: "Label en velden samen waren maar 11 op 20 juist (n = 10, 2 runs)."

> Week 4: "Hoe beter de tool, hoe meer tijd hij wint."
> Herschreven: "Bij 20 op 20 win ik 1–3 min extra per reactie."

> Week 3: "Dit is een werkpuntje dat in v3 zeker opgelost moet worden."
> Herschreven: "In v3 zeg ik wanneer een veld `nee` is en wanneer `niet vermeld`."
