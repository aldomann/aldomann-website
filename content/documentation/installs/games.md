---
title: Games
toc: true
type: book
date: "2019-12-11T00:00:00Z"
draft: false

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---

## Enable Proton for Steam

[Proton](https://github.com/ValveSoftware/Proton) is a tool for use with the Steam client which allows games which are exclusive to Windows to run on the Linux operating system. It uses Wine to facilitate this.

1. Go to Account Settings.
2. Enable Steam Play.

## Age of Empires II: HD on Steam (Proton)

1. Install [Age of Empires II: HD](https://store.steampowered.com/app/221380/Age_of_Empires_II_2013/).

2. Rename `AoK.exe` to `Launcher.exe`:
    ```bash
    cd $HOME/.local/share/Steam/steamapps/common/Age2HD
    mv Launcher.exe Launcher_backup.exe
    cp AoK\ HD.exe Launcher.exe
    ```

*Notice that instead of `~/.local/share/Steam`, your Steam Library could be located in `~/.SteamLibrary`*.

## Civilization IV on Steam (Proton)

1. Install [Sid Meier's Civilization® IV](https://store.steampowered.com/sub/4323/). Notice that you'll only need to install the latest expansion (Beyond the Sword).

2. Remove the `8800` directory.

3. Recreate the Wine prefix by using the "Verify Integrity of Game Files" feature.

4. Install `msxml3`:
    ```bash
    WINEPREFIX=~/.local/share/Steam/steamapps/compatdata/8800/pfx WINE=~/.local/share/Steam/steamapps/common/Proton\ 3.7/dist/bin/wine winetricks msxml3
    ```

5. Install `msxml4`:
    ```bash
    WINEPREFIX=~/.local/share/Steam/steamapps/compatdata/8800/pfx WINE=~/.local/share/Steam/steamapps/common/Proton\ 3.7/dist/bin/wine winetricks msxml4
    ```

*Notice that instead of `~/.local/share/Steam`, your Steam Library could be located in `~/.SteamLibrary`*.
