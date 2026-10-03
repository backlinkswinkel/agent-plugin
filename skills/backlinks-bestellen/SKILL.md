---
name: backlinks-bestellen
description: Zoek relevante Nederlandse websites in de Backlinkswinkel-catalogus en bestel een backlink na uitdrukkelijke bevestiging. Gebruik bij linkbuilding, "koop een backlink", "zoek een site met DR 30+ over wonen" of het controleren van een bestelling.
---

# Backlinks zoeken en bestellen via Backlinkswinkel

Volg deze volgorde en sla geen stap over:

1. `account_balance` — controleer het prepaid saldo (in eurocenten) vóór je iets voorstelt.
2. `search_domains` — zoek op onderwerp, taal en minimale DR. Gebruik `limit` en `offset` tot een pagina minder rijen bevat dan `limit`. Toon een korte shortlist: domein, DR, prijs, onderwerp.
3. `get_domain` — ververs prijs en metrics van het gekozen domein vlak vóór het bestellen.
4. `order_backlink` — **alleen na een expliciet "ja" van de gebruiker** op domein, anchor, doel-URL en prijs. Eén bestelling per bevestiging.
   Maak voor iedere bevestigde bestelling een nieuwe UUID en geef die mee als `idempotency_key`. Bewaar die sleutel bij de bestelling. Bij een timeout of onbekende uitkomst: herhaal dezelfde bestelling uitsluitend met dezelfde sleutel en dezelfde argumenten. Ook bij een nieuw requestnummer blijft die retry dezelfde order. Gebruik voor een tweede bewuste bestelling een nieuwe sleutel. Zonder sleutel wordt niets besteld. Controleer bij twijfel het Backlinkswinkel-account of vraag support om de uitkomst te bevestigen. Meld pas succes na een teruggelezen orderresultaat.
5. `order_status` — volg review en publicatie; geef de plaatsings-URL door zodra die er is.
6. `topup` — maak alleen een betaallink; de gebruiker opent en betaalt die zelf. Voer nooit zelf een betaling uit.

## Regels
- Verzin geen REST-paden als een tool ontbreekt; het gepubliceerde contract staat op https://backlinkswinkel.nl/api/v1/.
- Kies op relevantie en intentie, niet alleen op DR.
- Gebruik natuurlijke anchors; geen exact-match-stapeling op één doelpagina.
- Meld de kosten in euro's (saldo en prijzen komen binnen in centen).
- Geen backlinks naar sites die de gebruiker niet zelf beheert zonder dat expliciet te bevestigen.
