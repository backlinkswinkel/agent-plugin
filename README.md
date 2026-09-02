# Backlinkswinkel — agent plugin

Zoek Nederlandse websites in de catalogus van [Backlinkswinkel](https://backlinkswinkel.nl), bestel een backlink na jouw bevestiging en volg de plaatsing. Werkt in Claude Code, Codex, Cursor, Grok Build en elke andere MCP-client.

## Wat zit erin
- `mcp.json` / `.mcp.json` — verbinding met de hosted MCP-server `https://backlinkswinkel.nl/mcp` (Streamable HTTP, stateless).
- `skills/backlinks-bestellen` — de veilige bestelvolgorde: saldo → zoeken → prijs verversen → bestellen na akkoord → status.

## Tools (6)
`account_balance`, `search_domains`, `get_domain`, `order_backlink`, `order_status`, `topup`. `order_backlink` maakt een echte bestelling en trekt saldo af; de skill eist daarom eerst een expliciete bevestiging. `topup` maakt alleen een betaallink die een mens opent.

## API-sleutel
Maak een sleutel aan op https://backlinkswinkel.nl/account/api/ en zet hem in de omgeving van je client als `BACKLINKSWINKEL_API_KEY`. De server verwacht `Authorization: Bearer blw_...`.

- **Claude Code:** `.mcp.json` in deze repo gebruikt `${BACKLINKSWINKEL_API_KEY}`; exporteer de variabele en installeer met `claude plugin marketplace add backlinkswinkel/agent-plugin`.
- **Codex:** `codex plugin marketplace add backlinkswinkel/agent-plugin`.
- **Cursor / Agent Plugins-clients:** `mcp.json` bevat alleen de URL (de standaard staat geen geheimen in headers toe); voeg de Authorization-header toe in de MCP-instellingen van je client.
- **Grok Build:** `grok plugin install https://github.com/backlinkswinkel/agent-plugin.git`, daarna de header in de MCP-config zetten.

## Netwerk en data
De plugin praat alleen met `https://backlinkswinkel.nl`. De API-sleutel verlaat je machine alleen richting dat domein. Privacy: https://backlinkswinkel.nl/privacy/

## Licentie
MIT (deze plugin-verpakking). De dienst valt onder de algemene voorwaarden van Backlinkswinkel.
