# Matinee Player: releases

Signed releases of [Matinee Player](https://matineeplayer.com), a player for Android TV and
Google TV. Matinee has no channels, films or series of its own: you add your own source.

This repository holds nothing but the releases. Each one has three files:

| File | What it is |
|---|---|
| `matinee-<version>.apk` | The app, signed with Matinee's release key. |
| `matinee.apk` | The same file under a name that does not change, so that `releases/latest/download/matinee.apk` is always the newest. |
| `version.json` | Which version it is: version code and name, the name of the APK, its size and its SHA-256. |

The app looks at `version.json` of the latest release to see whether there is a newer
version. It downloads the APK from the same release, checks its size and SHA-256 against
`version.json`, and checks that it is signed with the same key as the app that is installed,
before Android is asked to install it. Android checks the signature once more itself.

## Checking a download yourself

Every release is signed with the same key. The SHA-256 fingerprint of its certificate is:

```
38:A9:70:47:B2:96:2F:6A:EF:B9:95:D4:B9:9D:EF:54:A7:65:AF:2D:D0:FF:96:CB:EB:2B:E5:23:97:0C:62:E2
```

With the Android SDK's build tools: `apksigner verify --print-certs matinee.apk`.

## Installing

Matinee is installed from the file (sideloading), on Android TV and Google TV with Android 9
or later. Download `matinee.apk` to the TV, with a file manager or a downloader app, and
allow installation from that app when Android asks.

The build scripts of the FFmpeg audio decoders that the app uses, under the LGPL, are in
[matinee-ffmpeg](https://github.com/linusbjorklund/matinee-ffmpeg).
