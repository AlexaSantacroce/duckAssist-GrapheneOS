# duckAssist-GrapheneOS

**Fork of [duckAssist](https://github.com/diekaiju/duckAssist) hardened for GrapheneOS/Vanadium WebView.**

A lightweight, privacy-focused Android WebView wrapper for [Duck.ai](https://duck.ai/) (DuckDuckGo's private AI chat service).

## Changes from upstream

| Change | Rationale |
|--------|-----------|
| `setAllowFileAccess(false)` | Prevents `file://` URLs from bypassing Vanadium's strict site isolation |
| `setAllowContentAccess(false)` | Removes unnecessary `content://` URI attack surface |
| `setAcceptThirdPartyCookies(false)` | Restores Vanadium's default third-party cookie blocking |
| `minSdk 21 → 24` | Vanadium requires API 24+; ensures hardened WebView is always used |
| Removed remote Google Fonts from settings page | Eliminates external network request from a WebView with JS bridge to preferences |

## Upstream sync

```bash
git checkout main
git pull upstream main
git checkout hardened
git rebase main
git push origin hardened --force
```

## License

GPLv3
