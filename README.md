# Retokia MCP server

AI product photos for fashion shops: remove background and mannequin, ghost mannequin, AI model.

Retokia is an MCP server. Add it to your AI assistant once, sign in, and ask in plain words: create a card, choose the options, see the price, get the images.

- **Server address:** `https://app.retokia.com/mcp` (streamable HTTP)
- **Sign-in:** OAuth 2.1 with PKCE — the assistant never sees your password, and its access token lives one hour.
- **Documentation:** https://retokia.com/developers/mcp/
- **Official MCP Registry name:** `com.retokia/retokia`
- **Website:** https://retokia.com/ · **Prices:** https://retokia.com/pricing/ · **Contact:** contact@retokia.com

This repository holds no code: the server is hosted by Retokia (Alokavi 777 S.L., Barcelona). It is a listing for MCP directories.

## What it does
- Background & mannequin remover: the garment cut out of its background on white, mannequin or stand removed.
- Ghost mannequin from a phone photo: the garment as if worn by somebody invisible, white background.
- On model: the garment on an AI fashion model, one frame per garment and pose (front, back, side, three-quarter), styles Catalogue, Natural, Creative.

## Connect
**Claude (claude.ai, desktop and mobile).** In Claude open Settings → Connectors and choose “Add custom connector”. Name it Retokia, paste the server address above and add it. Press Connect. Retokia opens: sign in with your Retokia account. Read what Claude will be able to do and press Allow. Leave the spending box unticked if Claude should only prepare cards and quote prices.

**Claude Code.** Add the server in a terminal, then run `/mcp` inside Claude Code and choose Authenticate — the sign-in opens in your browser.

```
claude mcp add --transport http retokia https://app.retokia.com/mcp
```

**ChatGPT.** In ChatGPT open Settings → Apps & Connectors → Advanced settings and turn on Developer mode (on plans that offer it). Create a connector: name Retokia, the server address above, authentication OAuth. Sign in to Retokia when ChatGPT asks, and press Allow. In a new chat, turn the Retokia connector on and ask. In ChatGPT you buy credits on the Retokia website, not in the chat.

**Other MCP clients.** Any client that speaks MCP over HTTP with OAuth sign-in can connect, as long as its sign-in returns to a local address (localhost) — for example the MCP Inspector. Clients that return to their own app scheme are not accepted yet.

## Spending is a separate yes
Without the box the assistant can see your cards, create new ones, add photos, quote prices and ask for free corrections — and spend nothing. With the box it can also start processing. Every launch is quoted first, and it goes ahead only after you say yes to that price in the chat. It can never buy credits, change your settings or see your payment details. Disconnect at any time in Settings → Integrations of the Retokia app; the connection stops at once.

## What to ask
- “Remove the background and the mannequin from these four photos.”
- “Make a 3D ghost mannequin from this phone photo of a jacket, size Large.”
- “Show me the models I can use and put this dress on one of them, front and back.”
- “How many credits will this card cost? Start it if it is under 100.”
- “The left sleeve on photo 2 is wrong — ask for a correction.”

## The tools
| Tool | What it does |
|---|---|
| `whoami` | Who is signed in. |
| `retokia_account` | Your balance and where to buy credits. |
| `retokia_options` | Services, models, styles, sizes and prices to choose from. |
| `cards_list` | Your recent cards. |
| `card_create` | A new card from photos or image addresses. |
| `card_add_photos` | More photos for a card. |
| `card_get` | A card: its photos, what is in them, its status. |
| `card_set_garment` | Which garment is sold, when a photo shows several. |
| `card_set_item` | Correct a garment of an On model card. |
| `card_quote` | The price before anything is spent. |
| `card_process` | Start processing — spends credits, only after your yes. |
| `results_get` | Download links of the finished images. |
| `photo_repair` | A free correction of a finished photo. |
| `frame_retake_quote` | The price of one more On model frame. |
| `frame_retake` | Shoot one more frame — spends credits, only after your yes. |

## Prices
Pay per photo, no subscription; credits never expire. New accounts get 100 free credits to start; one photo can be tried without an account at https://app.retokia.com/try. Current prices: https://retokia.com/pricing/

Photos are stored in the EU and deleted after 30 days. Terms: https://retokia.com/terms/ · Privacy: https://retokia.com/privacy/

## License
The text of this README and `server.json` are © Alokavi 777 S.L., published under CC BY 4.0. “Retokia” is a trade name of Alokavi 777 S.L.; the service itself is not open source.
