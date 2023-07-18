---
title: "How to SSH into Steam Deck (Setup Guide)"
date: 2022-07-27T14:15:52+02:00
draft: false
---

How to configure remote access to Steam Deck files and Shell remotely using SSH Daemon on SteamOS.

{{<figure src="filezilla.png" href="filezilla.png">}}

SSH is a convenient way to access the Terminal or, via SFTP, securely access your Steam Deck's file system from a remote computer, such as your Desktop or Laptop. I find it handy for [grabbing my screenshots]({{<ref "steam-deck-screenshot-location">}}).

Setting up SSHD is pretty quick.

## How to SSH into your Steam Deck

1. Open up Konsole, the SteamOS Terminal emulator, in Desktop Mode.
2. If you haven't done so yet, enter `passwd` so that you will be prompted to set a password for the default `deck` user. 
3. Enable SSHD by running the following command:
   
   `sudo systemctl start sshd`
4. If you'd like for SSHD to run even after reboots:
   
   `sudo systemctl enable sshd`

Now you can connect to your Steam Deck using any SSH/SFTP client.

I like using <a href="https://filezilla-project.org/" target="_blank">FileZilla</a> for file transfers, it's quick and easy. Use port 22 and your Steam Deck's hostname, as well as `deck` for the user and the password we configured earlier.

{{<alert>}}
Take care not to delete or move system files.
{{</alert>}}

{{< gamepromo >}}

## How to disable SSH Daemon

1. Open up Konsole, the SteamOS Terminal emulator, in Desktop Mode.
2. Stop SSHD by running the following command:
   
   `sudo systemctl stop sshd`
3. Disable SSHD by running the following command:
   
   `sudo systemctl disable sshd`