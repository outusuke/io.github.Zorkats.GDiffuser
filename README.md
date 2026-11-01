# io.github.Zorkats.GDiffuser

Unofficial Flatpak of [G-Diffuser](https://github.com/Zorkats/G-Diffuser) (F-Zero X PC port).
It repackages the upstream Linux release; no game files are included.

## Install

    flatpak install --user G-Diffuser.flatpak
    flatpak run io.github.Zorkats.GDiffuser

## First run

You need your own F-Zero X **US rev0** ROM (`.z64`), the Expansion Kit disk image and a 64DD IPL
ROM. The Linux build has no file picker: **drag and drop** the files onto the first-boot window.
The Flatpak can read `~/Downloads` by default. For other folders:

    flatpak override --user --filesystem=/path/to/folder:ro io.github.Zorkats.GDiffuser

## Where your data lives

G-Diffuser is portable: it keeps everything beside its own executable. Because `/app` is
read-only, the launcher installs the program into a writable folder and runs it from there:

    ~/.var/app/io.github.Zorkats.GDiffuser/data/g-diffuser/
        G-Diffuser, lib/, fonts/, ...   program files, managed by the Flatpak (listed in .managed)
        saves/  ghosts/  mods/  shaders/  fzerox.o2r  *.cfg.json   yours; never touched

The program files are refreshed only when the Flatpak itself is updated. Updating the Flatpak is
the supported way to update; the in-game updater is disabled (no network permission).
