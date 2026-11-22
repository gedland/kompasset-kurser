# Kursene til Investeringskompasset

Dette repoet henter kursene til [Investeringskompasset](https://investeringskompasset.lovable.app) hvert
5. minutt med GitHub Actions, uten Lovable Cloud. Det er gratis fordi repoet er offentlig.

- `.github/workflows/kurser.yml`: jobben. Den kjører `kursjobb.mjs` og legger resultatet i grenen `data`.
- `kursjobb.mjs`: kursjobben bygd til én fil. **Ikke rediger her.** Den lages i
  `gedland/github-site-connector` med `node scripts/bygg-kursjobb.mjs`.
- Grenen `data`: kursene (`live.json`, `d-<dato>.json`, `index.json`, `tilstand.json` og vedlikeholdet).
  Siden henter dem fra `https://raw.githubusercontent.com/gedland/kompasset-kurser/data/<navn>.json`.
  Grenen skrives over med én ny commit hver gang.

Kildene er Yahoo Finance, Euronext, CoinGecko, Nasdaq, SEC EDGAR og Oslo Børs (Newsweb). Læringsverktøy,
ikke personlig finansiell rådgivning.

Ser `tilstand.json` gammel ut, sjekk fanen **Actions**. GitHub slår av planlagte jobber i offentlige repoer
etter 60 dager uten aktivitet. Skjer det, står det i Actions-fanen, og «Enable workflow» starter den igjen.
