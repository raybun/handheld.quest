---
title: "Where are my Steam Deck Screenshots Saved?"
date: 2022-07-27T15:20:52+02:00
draft: false
---

Where does Steam Deck (SteamOS) store screenshots taken in Game Mode?

{{<figure src="kingdom_two_crowns.jpg" href="kingdom_two_crowns.jpg">}}

## Why I needed to manually retrieve screenshots from the Deck

When playing with multiple profiles on Steam Deck, there seems to be a bug in the Steam Client preventing screenshot upload for the non-primary users. Fortunately, the Steam Deck being a linux device and openly accessible, it's quite easy to get to your screenshots (e.g. for sharing purposes) without having to send them to the cloud first.

## Steam Screenshot Path on Steam Deck

`/home/deck/.local/share/Steam/userdata/<ACCOUNT_ID>/760/remote/<TITLE_ID>/screenshots`

Hint: `ACCOUNT_ID` and `TITLE_ID` are variables. Replace accordingly.

You can navigate to that folder via Dolphin:

{{<figure src="screenshot_path.png" href="screenshot_path.png">}}

And then send the files over to your PC/Mac, for instance using **Warpinator**.

Alternatively, you can set up SSH access to your Steam Deck and fetch the files directly from your other machine. I have a [quick Steam Deck SSH guide]({{<ref "how-to-ssh-steam-deck">}}) if you're interested in using e.g. FileZilla to access your Steam Deck File System. It's nice because it also works in Game Mode.