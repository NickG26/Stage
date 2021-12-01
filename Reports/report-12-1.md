# Report Woensdag 1 december
## Troubleshooting Segmentatie Model
### Pixels in Mask image [SOLVED]
<p>
    Ik heb me bezig gehouden om de error op te lossen in de trainingsfase van het segmentatiemodel.
</p>
<p>
    Hiervoor moest ik heel wat bijleren over numpy om waarden te manipuleren. De concrete uitdaging was om de mask die drie kanalen (RGB) had te transformeren naar een ndarray met enkel één kanaal die de klasse weergeeft waartoe de pixel behoort.
</p>
<p>
    Met Numpy is het me gelukt, maar Numpy kon niet gebruikt worden dus moest verder opzoeken in Tensorflow API. Het probleem dook op tijdens het mappen van de afbeeldingen. In deze situatie doet tensorflow moeilijk en kan bepaalde functies niet uitvoeren zoals .numpy().
</p>
<p>
    Ik heb gevonden dat de originele masks perfect waren om mee te werken, maar doordat ik deze heb verandert van .tif naar .jpg bestand zijn een aantal pixels vergrijst. Dit resulteert in veel slechtere masks.
</p>
<p>
    Als ik elke pixel groter dan 0 laat oplichten dan krijg ik de volgende afbeelding te zien.
</p>

[Image mask](./images/mask.JPG)

<p>
    De mask is in orde. Elke pixel met waarde boven 60 krijgt waarde 1 en alles daaronder waarde 0.
</p>

### Geen Validatie [SOLVED]
<p>
    Ik heb even problemen gehad dat tijdens het trainen de validatie set niet werd gebruikt. Dit is opgelost.
</p>

## Model verfijnen
### Klasse verdeling is sterk ongelijk
<p>
    Ik schat dat elke 60 pixels behoort tot de klasse 1. Dit is de klasse die aangeeft een anomalie ontdekt te hebben. Natuurlijk voorspelt het model alle pixels op 0 waardoor het maar 1/60 pixels fout heeft en een heel goede score heeft. Dit is natuurlijk niet bruikbaar.
</p>
<p>
    Door gewichten toe te voegen werkt het model veel beter. Maar omdat er maar twee klasses zijn wil ik ook nog proberen om de metrics/loss te veranderen naar f-score. 
</p>
<p>
    Ik heb geprobeerd om naar een one-hot-encoding over te gaan, maar dit is me vandaag spijtig genoeg niet gelukt.
</p>