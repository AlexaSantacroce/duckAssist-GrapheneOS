# duckAssist-GrapheneOS

**Fork of [duckAssist](https://github.com/diekaiju/duckAssist) hardened for GrapheneOS/Vanadium WebView.**

## I don't think voice activation and digital assitant features are working. I made tweaks that prioritize security and Vanadium Webview compatibility.

A lightweight, privacy-focused Android WebView wrapper for [Duck.ai](https://duck.ai/) (DuckDuckGo's private AI chat service).

## Changes from upstream

| Change | Rationale |
|--------|-----------|
| `setAllowFileAccess(false)` | Prevents `file://` URLs from bypassing Vanadium's strict site isolation |
| `setAllowContentAccess(false)` | Removes unnecessary `content://` URI attack surface |
| `setAcceptThirdPartyCookies(false)` | Restores Vanadium's default third-party cookie blocking |
| `minSdk 21 → 24` | Vanadium requires API 24+; ensures hardened WebView is always used |
| Removed remote Google Fonts from settings page | Eliminates external network request from a WebView with JS bridge to preferences |
| Block `improving.duckduckgo.com` via `shouldInterceptRequest` | Prevents DuckDuckGo telemetry from leaving the device |

## Upstream sync

```bash
git checkout main
git pull upstream main
git checkout hardened
git rebase main
git push origin hardened --force
```

## Credits

- [woheller69/FreeDroidWarn](https://github.com/woheller69/FreeDroidWarn) — Shows a deprecation warning about Google's developer verification requirements

## License

GPLv3
