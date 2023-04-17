---
title: "Where Is My Save Game on Steam Deck? (Paths & Locations)"
date: 2022-07-16T18:09:11+02:00
draft: false
---
A list of common folders for save game data in SteamOS and Wine on Linux in general.

Table of contents:
- [Trouble finding your save game folders and files for Emulators, Windows games, Lutris and Heroic on Steam Deck?](#trouble-finding-your-save-game-folders-and-files-for-emulators-windows-games-lutris-and-heroic-on-steam-deck)
- [How to search for folders on Steam Deck (Desktop Mode)](#how-to-search-for-folders-on-steam-deck-desktop-mode)
- [Typical Save Game Folders / Paths on Steam Deck](#typical-save-game-folders--paths-on-steam-deck)
- [Copying files and folders to your PC or onto Steam Deck](#copying-files-and-folders-to-your-pc-or-onto-steam-deck)

## Trouble finding your save game folders and files for Emulators, Windows games, Lutris and Heroic on Steam Deck?

Sometimes you want to backup your save games from Steam Deck to PC, or maybe transfer saves *from* PC to the Deck for games that don't support cloud saves, or have been installed from one of the numerous third-party launchers, or manually via Lutris.

Windows games often use the `AppData` folder for save game storage. Where would you find that location on Linux, SteamOS?

{{<figure
    src="save_games_on_steam_deck.jpg"
    alt="using KFind on SteamOS"
    href="save_games_on_steam_deck.jpg"
    >}}

## How to search for folders on Steam Deck (Desktop Mode)

If you know the name of the folder you're looking for and have no clue where it might be located, a search might help you out. For instance, I was looking for the save path for Kingdom Two Crowns, knew that it would live inside `%AppData%` and the folder would be called `/KingdomTwoCrowns/Release`.

You could just search for that in *Dolphin*! Unfortunately my search process kept crashing, so I went with `KFind` (installed via `Discover`) and found my desired data.

## Typical Save Game Folders / Paths on Steam Deck

Often you are looking for a so-called **Prefix Folder**, Wine uses such folders to contain all of the configuration and windows bits and pieces needed for compatibility, like a registry.

They can live in various places across the file system, SteamOS also has a dedicated `compatdata` folder.

For reference, here are some paths you might want to check out if you're searching for the equivalent path for %AppData% and similar. You'll find that often the whole path structure (e.g. C:\Program Files\Blobotron) is mirrored in your file system on linux.

Tip: You can copy the paths from below and paste them into Dolphin's Path bar by clicking on the breadcrumb navigation, then pasting.

**Steam compatdata folder (useful for games installed with steam)**

```bash
/home/deck/.steam/steam/steamapps/compatdata/
```

To identify the correct subfolder here, look up the game in question on the steam store (web), the ID will be in the URL of the game like so:

`https://store.steampowered.com/app/**504230**/Celeste/`

**Wine default prefix folder (useful for Lutris and similar)**
```bash
 /home/deck/.wine/drive_c/users/deck/
```

**Heroic default prefix folder**
```bash
 /home/deck/Games/Heroic/Prefixes/
```

**RetroArch (EmuDeck) save folder**
```bash
/home/deck/.var/app/org.libreto.RetroArch/config/retroarch/saves/
```

**Symlinks to save folders for EmuDeck (SD Install)**
```bash
/run/media/mmcblk0p1/Emulation/saves/
```

{{< alert >}}
To view hidden files and folders in the **Dolphin** file manager on SteamOS, press `Ctrl + H` or select `View -> Show Hidden Files` in the menu. If you can't see the menu bar, hit the hamburger menu and look for `Show Menubar`.
{{< /alert >}}

## Copying files and folders to your PC or onto Steam Deck

To transfer files back and forth between your Desktop computer and Steam Deck, I can recommend using **Warpinator**.

Install the **Windows client** [from e.g. this GitHub Releases Page](https://github.com/slowscript/warpinator-windows/releases) (or another implementation) and get the Steam Deck client via the **Discover** store.

*Warpinator* will allow you to drag and drop folders into the Application and accept the transfer on the other side, as long as both devices are on the same network.

---

{{< alert "twitter" >}}

Don't forget to [follow me](https://twitter.com/handheldquest) on Twitter.

{{< /alert >}}
