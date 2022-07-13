---
title: "How to mirror / clone Steam Deck microSD to new SD card"
date: 2022-07-13T18:10:02+02:00
updated: 2022-07-13T23:50:00+02:00
draft: false
---

## I bought a larger SD card for my Steam Deck - how to transfer everything without breaking apps / games?

You already installed a bunch of games to your microSD on Steam Deck, maybe EmuDeck or other emulation setup and a bunch of ROMs and perhaps games from itch.io, using the Heroic launcher and a whole bunch of other stuff to your 256 GB SD card.

But then you realise that SD cards are cheap. You buy a 512 GB A2 microSD or even a 1TB card.

How can you move / migrate your data from the old SD card to the new one?

## Cloning a microSD card in SteamOS (Linux): Prerequisites

**What you will need**

- Steam Deck
- old microSD card
- new microSD card (equal in capacity, or larger)
- USB-C microSD card reader (or a USB-A card reader and a USB-C adaptor)
- alternatively: a USB-C dock featuring a SD Card Reader (that's what I used)

**Handy to have**
- external Keyboard
- external Mouse

**Duration**

It took me about 45 minutes to clone a 256 GB microSD to a new 512 GB drive I bought at a sale, then a few minutes for extra setup.

{{<figure
    src="steam-deck-konsole-dd-tool-clone-microsd-progress.jpg"
    alt="Steam Deck cloning old microSD to larger microSD Drive using DD Tool in Desktop Mode"
    caption="cloning in progress"
    href="steam-deck-konsole-dd-tool-clone-microsd-progress.jpg"
    >}}


## Steps

### Step 1: Format the new card

1. Remove the OLD card from your Steam Deck after safely ejecting it.
2. Insert the NEW card in the SD card slot.
3. Press the Steam button to enter the menu, go to `System -> System Settings -> Format SD Card`
4. Once done and it shows up in the `Storage` menu, you can remove the card from the slot.
5. Now reinsert your OLD card.

### Step 2: Figure out the names of your devices (drives) in Konsole

Using the Start Menu, launch `Konsole` (Terminal Emulator).

> *Note: if you have not yet set your sudo password, now is the time to set that up. Simply enter the command `passwd` and hit return. Then configure your password of choice, this will be your superuser/root password for the future, we'll need it in a sec.*

Now we need to determine which drive is which.

Run the `lsblk` command to get an overview of your drives and partitions. Take note of the name based on the size of the device, that should help you identify it.

Example:

- my OLD microSD is called **/mmcblk0** (in SD Slot)
- my NEW microSD is called **/sdb** (in card reader dock)

{{< alert >}}
**Important!** Your microSD devices might be called differently, so don't just copy my example. Or you'll have a bad time.
{{< /alert >}}

### Step 3: Run the "dd" utility for a perfect 1:1 clone

Now we can start cloning.

{{< alert >}}
**Important!** Make sure you have your charger hooked up, as this will take a while!
{{< /alert >}}

Enter the following command in `Konsole`:

```bash
sudo dd if=/dev/$OLDCARDNAME of=/dev/$NEWCARDNAME status=progress bs=100M
```

{{< alert >}}
**Important!** replace `$OLDCARDNAME` and `$NEWCARDNAME` (no dollar sign!) with the respective names of the old and new cards. The order matters.
{{< /alert >}}


What this does: This will clone the drive (and all partitions) specified in `if` to the drive specified in `of`, while displaying `progress` (nice!) and the bs=100M setting will help speed up the process to your microSD's max write speed.

It might take a while, up to a couple hours if you're cloning a large drive.

When the process is complete, continue to the next step.

{{<figure
    src="identify_partition.png"
    alt="Steam Deck cloning old microSD to larger microSD Drive using DD Tool in Desktop Mode"
    caption="my microSD write speed is maxed out"
    href="identify_partition.png"
    >}}

### Step 4: Reboot and resize partition to fill drive

If you are migrating to a larger drive, we need to reboot for the linux kernel to report the correct size for the drive and free space available, so that we can resize the partition to the full extent of the drive. Otherwise it will retain the size of the old drive we cloned. Not useful!

Usually Linux doesn't need a lot of reboots, but this is one of the cases where you need to restart.

1. Simply reboot from the power menu of SteamOS Desktop mode.
2. After reboooting, the Steam Deck will return to Game Mode. Go back to Desktop Mode.
3. Open `KDE Partition Manager` from the Start menu. 
4. Identify your new microSD drive and select the partition we cloned onto it. Click "Resize/Move" and drag the right border of the rectangle to fill up the empty space to the right. Alternatively you can set "Free space after" to zero. Click "OK". *(if Partition Manager complains about having the drive mounted, unmount the drive using the command `sudo umount /dev/$NEWCARDNAME`)*
5. Click "Apply" at the top left. This process should be fairly quick.
6. Now you can safely eject both microSD cards and insert your new, freshly cloned drive in the microSD slot of your Steam Deck.
7. Congratulations, enjoy your perfect clone! All of your applications and games, including emulation should work right out of the box.

{{<figure
    src="resize_partition_after_reboot.png"
    alt="Steam Deck cloning old microSD to larger microSD Drive using DD Tool in Desktop Mode"
    caption="resizing the partition after rebooting"
    href="resize_partition_after_reboot.png"
    >}}

---

{{< alert "twitter" >}}

Don't forget to [follow me](https://twitter.com/handheldquest) on Twitter.

{{< /alert >}}


---

### Troubleshooting

Q: I rebooted but I still can't resize my new drive's partition to fill up the empty space, what's happening?

A: You could try unmounting the drive using
```bash
sudo umount /dev/$NEWCARDNAME
```
(remember: we can figure out the name of the drive using `lsblk`) and running

```bash
sudo resize2fs /dev/$NEWCARDNAME
```
to try and expand the partition via the Terminal. It might come back with additional instructions, in which case follow those and run it again.