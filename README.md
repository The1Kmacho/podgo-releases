# PodGo — Android releases

This **public distribution repository** hosts versioned Android downloads for **PodGo**, an independent, player-driven multiplayer digital tabletop.

- The application source stays in a separate private development repository.
- Only verified, **signed** installable APKs are published here.
- The APKs are supplied as **GitHub Release assets**, not committed into Git history.
- Release pages include version details, minimum Android requirements, SHA-256 checksums and notices.
- Development / experimental releases are labeled as prereleases; stable releases are published only after testing.

Official public builds appear under [GitHub Releases](https://github.com/The1Kmacho/podgo-releases/releases). Do not download APKs from unverified mirrors.

PodGo is unofficial and is not endorsed by or affiliated with Wizards of the Coast. Magic: The Gathering and Commander are trademarks of their respective owners. Card content retrieved from Scryfall belongs to its respective rights holders. Scryfall is not affiliated with this application.

## Release channels

PodGo's public channels share **one permanent Android release signing key**,
but use different Android package IDs. You can install them side by side:

| Channel | Home-screen name | Android package ID |
| --- | --- | --- |
| Stable | PodGo | `com.the1kmacho.mtggo.unity` |
| Preview | PodGo Preview | `com.the1kmacho.mtggo.unity.preview` |
| Beta | PodGo Beta | `com.the1kmacho.mtggo.unity.beta` |
| Alpha | PodGo Alpha | `com.the1kmacho.mtggo.unity.alpha` |

The private development build uses `com.the1kmacho.mtggo.unity.dev`,
which is not a public release channel. Each application has independent local
storage, deck lists, card-art cache, and settings. Switching channels does not
transfer your data automatically; release updates apply **within** a channel,
provided Android signing identity and version codes are compatible.

## Install and update

Once a release is available, open **Releases** on the right of this page (or the releases tab on mobile), download the `PodGo-Android-arm64.apk` file, and follow your Android device's install prompts. Installation from outside the Play Store may require approval for that browser/file manager.

Keep the same app package and signing certificate when updating: an APK signed with a different key cannot replace an installed build in place. Back up local data before changing between testing and public versions.

Visit Camacho's Craft for the app's project page and the current release history after publication.

## Camacho's Craft release notification

Publishing a GitHub Release with an uploaded installable APK triggers `.github/workflows/notify-camachos-craft.yml`. That workflow requests a fresh production build of Camacho's Craft through a Cloudflare Workers Deploy Hook; the site build retrieves the latest GitHub release metadata automatically. It can also be run manually from Actions if a release event was missed.

The repository needs an Actions secret named **`CLOUDFLARE_DEPLOY_HOOK_URL`**, containing the deploy hook URL for the Camacho's Craft Worker on its `main` branch. Never commit or disclose the hook URL. The website also performs a six-hour backup synchronization.
