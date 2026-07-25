# DankCalendar on Flatpak

[![DankLinux](assets/danklogo.svg)](https://danklinux.com)

[DankCalendar](https://danklinux.com/docs/dankcalendar/) is a standalone calendar app for the modern Linux desktop with a Material Design 3 inspired UI. It brings your Local, Google, Microsoft, CalDAV, and iCloud calendars together in one place. It runs as a lightweight daemon with a tray icon, keeps your accounts in sync, and reminds you about events.

It's one of the first to be built with [Quickshell](https://quickshell.org/), Qt6, and Go. You can optionally pair it with [DankMaterialShell (DMS)](https://github.com/AvengeMedia/DankMaterialShell) for a more integrated experience.

This repository packages DankCalendar for [Flathub](https://flathub.org/apps/com.danklinux.dankcalendar) as `com.danklinux.dankcalendar`. Application source and issues live upstream at [AvengeMedia/dankcalendar](https://github.com/AvengeMedia/dankcalendar).

## Installation

```bash
flatpak install flathub com.danklinux.dankcalendar
```

Launch from your desktop menu, or:

```bash
flatpak run com.danklinux.dankcalendar
```

## Sandbox notes

Notifications and credentials use the XDG desktop portals
(`org.freedesktop.portal.Notification` and `org.freedesktop.portal.Secret`).

DankMaterialShell theme colors live in the host cache. To enable theme sync:

```bash
flatpak override --user \
  --filesystem=xdg-cache/DankMaterialShell:ro \
  com.danklinux.dankcalendar
```

Local ICS calendar directories also need an explicit grant, e.g.:

```bash
flatpak override --user \
  --filesystem=~/calendars \
  com.danklinux.dankcalendar
```

or the equivalent in [Flatseal](https://flathub.org/apps/com.github.tchx84.Flatseal)

App data is stored under `~/.var/app/com.danklinux.dankcalendar/`

## Building

```bash
flatpak run org.flatpak.Builder \
  --force-clean --user --install --repo=repo \
  builddir com.danklinux.dankcalendar.yml
```

```bash
flatpak run com.danklinux.dankcalendar
```

## Contributing

- App bugs and features: [AvengeMedia/dankcalendar](https://github.com/AvengeMedia/dankcalendar)
- Packaging and Flathub integration: this repository

## License

MIT [LICENSE](https://github.com/AvengeMedia/dankcalendar/blob/master/LICENSE)
