---
title: "How to Format Your SD Card on Steam Deck"
date: 2022-07-17T23:15:43+02:00
draft: false
---

Quick guide on how to easily format SD cards for Steam Deck.

{{<figure
    src="sd_cards.jpg"
    alt="a bunch of microSD cards waiting to get used by your Steam Deck"
    >}}

Table of contents:

- [Is it worth it to get a microSD storage expansion for your Deck?](#is-it-worth-it-to-get-a-microsd-storage-expansion-for-your-deck)
- [Quick Guide: Formatting your microSD card on Steam Deck](#quick-guide-formatting-your-microsd-card-on-steam-deck)
- [How to make SD Card the preferred install location](#how-to-make-sd-card-the-preferred-install-location)
- [How to install EmuDeck to microSD card instead of internal SSD](#how-to-install-emudeck-to-microsd-card-instead-of-internal-ssd)
- [Migrating microSD card contents](#migrating-microsd-card-contents)

## Is it worth it to get a microSD storage expansion for your Deck?

While it's great to have a large internal SSD in your Steam Deck, the practical performance difference of using a microSD for expansion is negligible, especially when using a fast A2 class SD card. Games basically load just as quickly off the SD card, which is great!

Expanding your Steam Deck storage with a fast microSD card is super easy and delivers a ton of bang for your buck. The way SteamOS handles those cards, you can hot-swap them without issue too. That means you can just eject it and swap it for another card, then load your game from a secondary or tertiary (or more, if you're planning for a desert island setup!) card within seconds.

## Quick Guide: Formatting your microSD card on Steam Deck

It's incredibly simple!

1. You can do this from **Game Mode**, no need to enter Linux Desktop Mode.
2. Insert your microSD card.
3. Press the `STEAM` button to show the menu, navigate to `System`, then scroll down a bit until you see `System Settings`.
4. Select `Format` in the `Format SD Card` section.
5. That's it! Your card will now be formatted correctly and contain a rudimentary folder structure so that Steam can populate the card with games.

## How to make SD Card the preferred install location

1. Press the `STEAM` button to show the menu
2. Go to `Storage` and select your SD Card from the top two toggles
3. Press `X` to set default, if not already selected.

## How to install EmuDeck to microSD card instead of internal SSD

1. Make sure you first format your SD card as described above (or manually, it needs to be ext4 or btrfs formatted)
2. Run the EmuDeck installer and follow the instructions.

---

{{< alert "twitter" >}}

Don't forget to [follow me](https://twitter.com/handheldquest) on Twitter.

{{< /alert >}}

---

## Migrating microSD card contents

If you already have a bunch of stuff on a smaller card and you're hoping to migrate all of your data to a larger card, then [this is the guide for you]({{< ref "/posts/steam-deck-copy-microsd-card-contents-to-larger-drive">}}).