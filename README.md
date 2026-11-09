# Just Player 

[![GitHub release (latest)](https://img.shields.io/github/v/release/malocnet/JustPlayer.svg?logo=github&label=GitHub)](https://github.com/malocnet/JustPlayer/releases/latest)
[![Original](https://img.shields.io/badge/original-moneytoo%2FPlayer-blue?logo=github)](https://github.com/moneytoo/Player)
[![Forked from](https://img.shields.io/badge/forked%20from-whistlingwoods%2FJustPlayer-blue?logo=github)](https://github.com/whistlingwoods/JustPlayer)
[![Media3](https://img.shields.io/badge/Media3-1.11.1-007ec6)](https://github.com/androidx/media)
[![Translation Status](https://hosted.weblate.org/widgets/just-player/-/svg-badge.svg)](https://hosted.weblate.org/engage/just-player/)

Android video player based on [ExoPlayer](https://github.com/google/ExoPlayer)

It uses ExoPlayer's ``extension-ffmpeg`` with [all its audio formats](https://exoplayer.dev/supported-formats.html#ffmpeg-extension) enabled (it can handle even special formats like AC3, EAC3, DTS, DTS HD, TrueHD etc.).

It properly syncs audio with video track when using Bluetooth earphones/speaker. (I was not able to find any other nice ExoPlayer based video player so I created this one.)

## Supported formats

 * **Audio**: Vorbis, Opus, FLAC, ALAC, PCM/WAVE (μ-law, A-law), MP1, MP2, MP3, AMR (NB, WB), AAC (LC, ELD, HE; xHE on Android 9+), AC-3, E-AC-3, DTS, DTS-HD, TrueHD
 * **Video**: H.263, H.264 AVC (Baseline Profile; Main Profile on Android 6+), H.265 HEVC, MPEG-4 SP, VP8, VP9, AV1
 * **Containers**: MP4, MOV, WebM, MKV, Ogg, MPEG-TS, MPEG-PS, FLV
 * **Streaming**: DASH, HLS, SmoothStreaming, RTSP

HDR (HDR10+ and Dolby Vision) video playback on compatible/supported hardware.

## Screenshots

<img src="https://raw.githubusercontent.com/moneytoo/Player/master/fastlane/metadata/android/en-US/images/phoneScreenshots/1.png" width="820"> <img src="https://raw.githubusercontent.com/moneytoo/Player/master/fastlane/metadata/android/en-US/images/phoneScreenshots/2.png" width="410"> <img src="https://raw.githubusercontent.com/moneytoo/Player/master/fastlane/metadata/android/en-US/images/phoneScreenshots/3.png" width="410">

## Features

 * Audio track selection
 * Playback speed control
 * Horizontal swipe and double tap to quickly seek
 * Vertical swipe to change brightness (left) / volume (right)
 * Pinch to zoom (Android 7+)
 * PiP (Picture in Picture) on Android 8+ (resizable on Android 11+)
 * Resize (fit/crop)
 * Volume boost
 * Auto frame rate matching on Android TV/boxes (Android 6+)
 * No ads, tracking or excessive permissions

**`WRITE_SETTINGS` ("Modify system settings") permission**: When the system file chooser is opened, it will always use current system orientation, even if the Player app sets its own. Granting this permission via adb (`adb shell pm grant com.brouken.player android.permission.WRITE_SETTINGS`) or App info screen will allow this app to temporarily enable Auto-rotate to at least partially mitigate [this imperfection](https://issuetracker.google.com/issues/141968218).

Translate: [Weblate](https://hosted.weblate.org/engage/just-player/)

## Download

[<img src="https://raw.githubusercontent.com/andOTP/andOTP/master/assets/badges/get-it-on-github.png" alt="Get it on GitHub" height="75">](https://github.com/malocnet/JustPlayer/releases/latest)

Also available on **OPPO App Market**, [**Xiaomi GetApps**](http://app.xiaomi.com/detail/1351636) ([for now](https://www.reddit.com/r/JustPlayer/comments/mqvtve/just_player_app_is_too_simple_for_xiaomi_failed/)) or [Uptodown](https://just-video-player.en.uptodown.com/android).

Other links/channels: application thread on [XDA Developers](https://forum.xda-developers.com/t/app-5-0-just-video-player-no-bluetooth-lag-exoplayer-ffmpeg-audio-codecs.4189183/), subreddit on [reddit](https://www.reddit.com/r/JustPlayer/), entry on [AlternativeTo](https://alternativeto.net/software/just-video-player/about/), git mirror on [GitLab](https://gitlab.com/moneytoo/Player), group on [Telegram](https://t.me/JustVideoPlayer)

## FAQ

### What to do if Bluetooth audio is not in sync with video?

Just pause and resume playback once again.

### Are there any media formats it CANNOT play?

Unfortunately, upstream ExoPlayer doesn't handle some older formats like [AVI container](https://github.com/google/ExoPlayer/issues/2092), WMV or [Theora](https://github.com/google/ExoPlayer/issues/4970).

Just Player focuses on playing videos so audio only playback isn't officialy supported ([request](https://github.com/moneytoo/Player/issues/55)). 

### How to view detailed video information (like resolution, bitrate etc.)?

Available since `v0.33`: Install app like [MediaInfo](https://play.google.com/store/apps/details?id=net.mediaarea.mediainfo) (or APK from [MediaArea.net](https://mediaarea.net/en/MediaInfo/Download/Android)). Then, to quickly open MediaInfo from Just Player, long press the video name/title.

### I want to automatically activate PiP mode when leaving the player...

There as a hidden feature - Auto PiP. Long press the PiP icon to activate this feature. Then, when you leave Just Player through the home button and video is playing, PiP will be activated automatically.

## Other open source Android video players

Here's a comparison table presenting all available and significant open source video players for Android I was able to find. Just Player is something like 80% feature complete. It will probably never have dozens of options or some rich media library UI. It will never truly compete with feature rich VLC. It just attempts to provide functional feature set and motive others to create greater players based on amazing ExoPlayer.

| App name (source)                                                           | Tested version        | Media engine                                                                                                                                                            | Subtitles (embedded)                                  | DTS/AC3/E-AC3 decoders | PiP                      | Cutout (notch) | HDR (4K 60 FPS HEVC)        | HDR (4K 60 FPS VP9)         | Gestures                  |
| --------------------------------------------------------------------------- | --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------- | ---------------------- | ------------------------ | -------------- | --------------------------- | --------------------------- | ------------------------- |
| [Fermata Media Player](https://github.com/AndreyPavlenko/Fermata)           | 1.7.3                 | [MediaPlayer](https://developer.android.com/guide/topics/media/mediaplayer), [ExoPlayer](https://exoplayer.dev/) and [libVLC](https://www.videolan.org/vlc/libvlc.html) | 🟢 Yes (libVLC only)                                  | 🟢 Yes (libVLC only)   | 🔴 No                    | 🔴 No          | 🟢 Yes                      | 🔴 No                       | 🟡 Seek/Volume            |
| [Just (Video) Player](https://github.com/moneytoo/Player)                   | 0.11                  | [ExoPlayer](https://exoplayer.dev/)                                                                                                                                     | 🟢 Yes                                                | 🟢 Yes                 | 🟢 Yes                   | 🟢 Yes         | 🟢 Yes                      | 🟢 Yes                      | 🟢 Seek/Volume/Brightness |
| [Kodi](https://github.com/xbmc/xbmc)                                        | 18.9                  | ?                                                                                                                                                                       | 🟢 Yes                                                | 🟢 Yes                 | 🔴 No                    | 🔴 No          | 🟢 Yes                      | 🔴 No                       | 🔴 No                     |
| [mpv](https://github.com/mpv-android/mpv-android)                           | 2020-11-16-release    | [libmpv](https://github.com/mpv-player/mpv)                                                                                                                             | 🟢 Yes                                                | 🟢 Yes                 | 🔴 No                    | 🟢 Yes         | 🟡 Yes (performance issues) | 🟡 Yes (performance issues) | 🟢 Seek/Volume/Brightness |
| [Nova Video Player](https://github.com/nova-video-player/aos-AVP)           | 4.49.15-20201210.0809 | ?, ([ExoPlayer](https://exoplayer.dev/) in [nova v7](https://github.com/nova-video-player/aos-AVP/milestone/9))                                                         | 🟢 Yes                                                | 🟢 Yes                 | 🟢 Yes                   | 🔴 No          | 🟢 Yes                      | 🔴 No                       | 🔴 No                     |
| [VLC](https://code.videolan.org/videolan/vlc-android)                       | 3.3.2                 | [libVLC](https://www.videolan.org/vlc/libvlc.html)                                                                                                                      | 🟡 Yes (may be cut off in some video display formats) | 🟢 Yes                 | 🟢 Yes                   | 🟢 Yes         | 🟢 Yes                      | 🔴 No                       | 🟢 Seek/Volume/Brightness |
| [YetAnotherVideoPlayer](https://github.com/shadow578/YetAnotherVideoPlayer) | 1108                  | [ExoPlayer](https://exoplayer.dev/)                                                                                                                                     | 🔴 No                                                 | 🔴 No                  | 🟡 Yes (with black bars) | 🔴 No          | 🔴 No                       | 🔴 No                       | 🟡 Volume/Brightness      |

_The tested HDR VP9 video was "The World in HDR" from [Kodi Sample](https://kodi.wiki/view/Samples#4K_.28UltraHD.29), running on OnePlus 7 (Snapdragon 855)._

To find other video players (including non-FOSS), check out [a list on IzzyOnDroid](https://android.izzysoft.de/applists/category/named/multimedia_video_player).
