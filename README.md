# flatpak for kiss

NOTICE: This repo is no longer maintained as Flatpak is now included in the kiss-community/community repo. I'm leaving it here for reference purposes only.

Forked from [mmatongo/kiss-flatpak](https://github.com/mmatongo/kiss-flatpak) which was in turn forked from [dylanaraps/kiss-flatpak](https://github.com/dylanaraps/kiss-flatpak). Neither repo was building for me, which probably isn't surprising given their age and the pace of changes to KISS itself, so I forked the most recent one and attempted to fix all the build failures.

Even though this builds correctly, I still couldn't launch any Flatpaks that required dbus such as LibreOffice. I found that installing dbus and then launching the Flatpak with `dbus-launch --exit-with-session flatpak run --user org.libreoffice.LibreOffice` does the trick.

INSTRUCTIONS

```
# NOTE: You must have user namespaces enabled in your kernel.
-> CONFIG_USER_NS=y

# NOTE: The community repository must also be enabled.
-> git clone https://github.com/dylanaraps/kiss-flatpak
-> export KISS_PATH=/path/to/kiss-flatpak/flatpak:$KISS_PATH

-> kiss b flatpak
-> kiss i flatpak

-> flatpak remote-add --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
-> flatpak install --user gimp
-> flatpak run --user org.gimp.GIMP
```

ISSUES

- [ ] No audio in flatpaks expecting a running PulseAudio server on the host.


OTHER FLATPAK REPOSITORIES

- https://flatpak.citra-emu.org/
