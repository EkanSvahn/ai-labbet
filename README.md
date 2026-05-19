# AI-Labbet

Klassrumsdemo av AI för förstaklassare. Vanilla HTML + en serverless proxy mot Anthropic API.

## Deploya på Vercel

1. Skaffa API-nyckel på [console.anthropic.com](https://console.anthropic.com) → Settings → API Keys.
2. **Sätt en spending limit** under Billing → Usage limits. $5/månad räcker gott för demo-bruk och skyddar dig om någon hittar URL:en.
3. Pusha den här mappen till GitHub.
4. På [vercel.com](https://vercel.com): Add New Project → välj repot → Deploy.
5. I projekt-Settings → Environment Variables: lägg till `ANTHROPIC_API_KEY` med nyckeln. Tryck Redeploy.
6. Öppna `https://din-app.vercel.app` på telefonen.

## Lokal körning (valfritt)

```bash
npm i -g vercel
vercel dev
```

Sätt `ANTHROPIC_API_KEY` i en `.env.local`-fil först (committa **aldrig**).

## Filer

- `index.html` — appen. Frontend-only, vanilla JS, inga deps.
- `api/claude.js` — serverless proxy som lägger på API-nyckeln och forwardar till `api.anthropic.com/v1/messages`.

## Kostnad

Sonnet 4 ligger på ~$3/M input-tokens, ~$15/M output-tokens. En bildanalys kostar typ 0.5 cent. Hela klassrummet körs igenom för någon krona.

## Säkerhet

Appen är öppen för internet utan auth. För engångsdemo helt OK om du har spending limit + raderar projektet efteråt (Vercel → Settings → Delete Project). För återkommande bruk: lägg till en password gate eller en shared header.

## På telefonen

- `facingMode: 'environment'` ger bakkameran automatiskt
- HTTPS via Vercels gratis-cert krävs för `getUserMedia` (ingen åtgärd, det följer med)
- iOS: Share → Add to Home Screen för app-känsla utan adressfält
