<div align="center">

# DDNet AppImage 🐧

[![CI Build Status](https://github.com/Nemo-010/ddnet-AppImage/actions/workflows/appimage.yml/badge.svg)](https://github.com/Nemo-010/ddnet-AppImage/releases/latest)
[![Latest Stable Release](https://img.shields.io/github/v/release/Nemo-010/ddnet-AppImage)](https://github.com/Nemo-010/ddnet-AppImage/releases/latest)

| Latest Stable Release | Upstream URL |
| :---: | :---: |
| [Click here](https://github.com/Nemo-010/ddnet-AppImage/releases/latest) | [Click here](https://github.com/ddnet/ddnet) |

</div>

---

Unofficial AppImage of [DDNet](https://github.com/ddnet/ddnet), the cooperative
Teeworlds modification with a focus on racing, built from source with CMake.

AppImage made using [quick-sharun](https://github.com/pkgforge-dev/Anylinux-AppImages/blob/main/useful-tools/quick-sharun.sh), which makes it extremely easy to turn any binary into a portable package reliably without using containers or similar tricks.

**This AppImage bundles everything and it should work on any Linux distro, including old and musl-based ones.**

This AppImage doesn't require FUSE to run at all, thanks to the [uruntime](https://github.com/VHSgunzo/uruntime).

This AppImage is also supplied with a self-updater by default, so any updates to this application won't be missed, you will be prompted for permission to check for updates and if agreed you will then be notified when a new update is available.

Self-updater is disabled by default if AppImage managers like [am](https://github.com/ivan-hc/AM), [soar](https://github.com/pkgforge/soar) or [dbin](https://github.com/xplshn/dbin) exist, which manage AppImage updates.

## Building

The client (`DDNet`) and the dedicated server (`DDNet-Server`) are both included
in the AppImage, and both are compiled from the latest upstream release tag with
video recording (FFmpeg), the Vulkan and OpenGL backends, and the Rust part of
the codebase. **Do not build this anywhere except Arch Linux** — deploying this
on any other distribution is a very bad idea. The application must be installed
to `/usr` before `quick-sharun` deploys it, which `get-dependencies.sh` does with
`cmake --install`.

The game data (`/usr/share/ddnet/data`) is copied to `$APPDIR/bin/data`, because
DDNet looks for its resources next to the path it was started as. The tools
(`DDNet-Tools`) and the optional MySQL, UPnP, websocket and Discord integrations
are left out; the autoupdater is compiled out, since this AppImage updates
through zsync instead.

The icon is upstream's own `other/icons/DDNet_256x256x32.png`.