# PolluxDEX Wallet: published releases

The PolluxDEX Wallet runs as one web page, **https://wallet.polluxdex.com/**. Your phone key lives encrypted on your
device; the page has no internet permission. You still trust whoever serves that page, as with any website wallet.
This repository lets anyone check that the page being served is a published release, not a modified one.

## Current version

| Version | Fingerprint (sha256) | Live since |
|---|---|---|
| **0.2.5** | `2c34c50914079cff64f4a444c342b6ef5cc84a87be992223f4700c3c9f89a57d` | 2026-11-27 |

The wallet shows its version at the bottom of its screen ("v0.2.5"). **0.1.9** is historical/retired (replaced 2026-11-27). Older versions: [RELEASES.md](RELEASES.md).

## What's in this repository
- `SHA256SUMS`: the fingerprints of the versions that are **allowed right now** (normally just the newest).
- `releases/<fingerprint>/release.json`: the exact security headers that version must be served with.
- `RELEASES.md`: the full history.
- `watch/`: the watcher PolluxDEX runs on a separate server (alerts to Discord). You can run it too.

## Check it yourself (any computer with curl)

```
curl -s https://wallet.polluxdex.com/ | sha256sum
curl -s https://raw.githubusercontent.com/pollux254/polluxdex-wallet-releases/main/SHA256SUMS
```
The first fingerprint must appear in the second list. If it doesn't, **don't sign anything with the PolluxDEX Wallet**
and tell PolluxDEX. Your MASTER paper can always remove the phone key and take the wallet back.

## Run the watcher yourself
`watch/polluxdex-wallet-watch` is a small bash script (curl + sha256sum + python3 for the alert). Set
`ALLOW_URL=https://raw.githubusercontent.com/pollux254/polluxdex-wallet-releases/main/SHA256SUMS` and
`DISCORD_WEBHOOK_URL=...` (your own) and run it every few minutes.
