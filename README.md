# Debian Droid

[![Build status](https://github.com/minhmc2007/DebianDroid/workflows/Build/badge.svg)](https://github.com/minhmc2007/DebianDroid/actions)
[![Testing status](https://github.com/minhmc2007/DebianDroid/workflows/Unit%20tests/badge.svg)](https://github.com/minhmc2007/DebianDroid/actions)

Debian Droid is an Android terminal application that provides a full Debian Linux environment, forked from [Termux](https://termux.com). Instead of using the original Termux environment, this project uses a complete Debian distribution powered by proot-distro technology.

Note that this repository is for the app itself (the user interface and the terminal emulation). The core difference from the original Termux is that Debian Droid provides a full Debian Linux distribution environment using proot technology, giving you access to the complete Debian package ecosystem instead of the limited Termux packages.

For more information about proot-distro, see [proot-distro documentation](https://github.com/termux/proot-distro).

***

**NOTICE: Debian Droid may be unstable on Android 12+.** Android OS will kill any (phantom) processes greater than 32 (limit is for all apps combined) and also kill any processes using excessive CPU. You may get `[Process completed (signal 9) - press Enter]` message in the terminal without actually exiting the shell process yourself. Check the related issue [#2366](https://github.com/termux/termux-app/issues/2366) and related documentation for more information on how to disable trimming of phantom and excessive cpu usage processes.

***

## Contents
- [Installation](#installation)
- [Uninstallation](#uninstallation)
- [Important Links](#important-links)
- [Debugging](#debugging)
- [For Maintainers and Contributors](#for-maintainers-and-contributors)
- [Forking](#forking)

## Installation

Latest version is available from [GitHub Releases](https://github.com/minhmc2007/DebianDroid/releases).

Debian Droid can be obtained for **only** Android `>= 7` with full Debian Linux environment support.

The APKs are [`debuggable`](https://developer.android.com/studio/debug) builds created for testing purposes.

Both universal and architecture specific APKs are released. The APK and bootstrap installation size will be approximately 180MB if using universal and approximately 120MB if using architecture specific.

**Security warning**: APK files are signed with a test key that has been shared with the community. This IS NOT an official developer key. Be careful when installing builds from sources other than the official repository at https://github.com/minhmc2007/DebianDroid.

## Uninstallation

To uninstall Debian Droid completely, go to `Android Settings` -> `Applications` and look for the app. You can also use the search feature if available on your device.

## Important Links

### Community
- [Original Termux Reddit community](https://reddit.com/r/termux)
- [Original Termux Wiki](https://wiki.termux.com/wiki/)

### Wikis
- [Original Termux App Wiki](https://github.com/termux/termux-app/wiki)
- [Original Termux Packages Wiki](https://github.com/termux/termux-packages/wiki)

### Miscellaneous
- [FAQ](https://wiki.termux.com/wiki/FAQ)
- [File System Layout](https://github.com/termux/termux-packages/wiki/Termux-file-system-layout)
- [Differences From Linux](https://wiki.termux.com/wiki/Differences_from_Linux)
- [Debian Package Management](https://www.debian.org/doc/manuals/debian-reference/ch02.en.html)
- [Proot-distro Documentation](https://github.com/termux/proot-distro)
- [Remote Access](https://wiki.termux.com/wiki/Remote_Access)
- [Terminal Settings](https://wiki.termux.com/wiki/Terminal_Settings)
- [Touch Keyboard](https://wiki.termux.com/wiki/Touch_Keyboard)
- [Android Storage and Sharing Data with Other Apps](https://wiki.termux.com/wiki/Internal_and_external_storage)

## Debugging

You can help debug problems by setting appropriate `logcat` `Log Level` in app settings -> `Debugging` -> `Log Level`. The `Log Level` defaults to `Normal` and log level `Verbose` currently logs additional information. It's best to revert log level to `Normal` after debugging since private data may otherwise be passed to `logcat` during normal operation.

Once log levels have been set, you can run the `logcat` command in the terminal to view the logs in realtime (`Ctrl+c` to stop) or use `logcat -d > logcat.txt` to take a dump of the log. You can also view the logs from a PC over `ADB`.

Users can generate files `stat` info and `logcat` dump automatically with terminal's long hold options menu `More` -> `Report Issue` option and selecting `YES` in the prompt shown to add debug info.

Users must post complete report (optionally without sensitive info) when reporting issues. Issues opened with partial screenshots of error reports instead of text will likely be automatically closed.

##### Log Levels

- `Off` - Log nothing.
- `Normal` - Start logging error, warn and info messages and stacktraces.
- `Debug` - Start logging debug messages.
- `Verbose` - Start logging verbose messages.

## For Maintainers and Contributors

This fork maintains the same structure as the original Termux project. The main constants are defined by the `TermuxConstants` class, which also contains information on how to fork or build with your own package name.

The `versionName` in `build.gradle` files must follow the [semantic version `2.0.0` spec](https://semver.org/spec/v2.0.0.html) in the format `major.minor.patch(-prerelease)(+buildmetadata)`.

### Commit Messages Guidelines

Commit messages **must** use the [Conventional Commits](https://www.conventionalcommits.org) spec. **The first letter for `type` and `description` must be capital and description should be in the present tense.**

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Only the `types` listed below must be used:**

- **Added** for new features.
- **Changed** for changes in existing functionality.
- **Deprecated** for soon-to-be removed features.
- **Removed** for now removed features.
- **Fixed** for any bug fixes.
- **Security** in case of vulnerabilities.

## Forking

This project is a fork of the original Termux. When making further modifications:

- Check the `TermuxConstants` class for instructions on changing package names
- You may need to recompile bootstrap zip packages for new package names
- Some components may have hardcoded values that need manual patching

For more detailed information on forking, refer to the original Termux documentation.
