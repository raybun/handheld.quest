---
title: "Developing a Game with Steam Deck in Mind"
date: 2024-01-26T15:56:41+01:00
draft: false
cover: "*workdesk*"	
---

The Steam Deck is a Dev Dream come true. I've always dreamt of making a game for a handheld console, but this is better. Let me tell you why.

Long story short: They say **"build the thing you'd want to use yourself**" and that's how I ended up developing an action-roguelite game ([ahem, check it out on Steam if you're keen](https://store.steampowered.com/app/2207230/Black_Dragon_Mage/?utm_source=handheldquest&utm_medium=article_intro&utm_campaign=demo)) with the Steam Deck in mind, *starting as early as the prototype stage.*

**Today I wanted to share a few advantages of this approach and tell the story of my Steam Deck development journey.**

- [🧙‍♂️ How I ended up building a game with a "designed for Steam Deck" mentality](#️-how-i-ended-up-building-a-game-with-a-designed-for-steam-deck-mentality)
- [🚀 Performance Testing](#-performance-testing)
  - [Emulating a weaker system](#emulating-a-weaker-system)
  - [Looking deep into frametime](#looking-deep-into-frametime)
  - [No weird background processes or OS reinstalls needed](#no-weird-background-processes-or-os-reinstalls-needed)
- [🎨 Steam Deck makes for accessible design](#-steam-deck-makes-for-accessible-design)
- [💥 Small bumps on the road](#-small-bumps-on-the-road)
- [🕹️ Work and Play](#️-work-and-play)
- [💾 Deploying Directly to a Handheld](#-deploying-directly-to-a-handheld)
- [📦 Deploying via Steam](#-deploying-via-steam)
- [💖 Thank you for reading!](#-thank-you-for-reading)
  - [Watch the trailer:](#watch-the-trailer)
  - [Play the game:](#play-the-game)

{{<figure src="gameplay.gif">}}

## 🧙‍♂️ How I ended up building a game with a "designed for Steam Deck" mentality

When I bought the Deck right at launch, I played a variety of games and that inspired me to come up with a fantasy action rogue-lite that I would enjoy personally, for quick rounds, in a pick-up-and-play manner.

Throughout the development of my game, I learned a ton about the Steam platform, how to optimize my game for the Deck... and there's still so much to explore. 

Learning about various little tricks (like SSH access, where screenshots are stored, and how to grab a save game, all described on this site) also made me start this very blog, as a notebook of sorts.


## 🚀 Performance Testing
 
As **game developers,** we want our game to ideally run on a potato PC. So we need to test the game in a fitting environment.

But I don't own a potato PC, since I'm also a gamer. 😉 Even worse, my partner works in game art, so her machine can probably run three (not more, of course, limits of physics and all) instances of Crysis without breaking a sweat.

For small indie developers (or even solo indies), a big QA team and a range of hardware for testing is likely not within the budget. One option is to get a *cheap low-range desktop or laptop computer.*

**The Steam Deck is more versatile than a potato test PC,** it can replace proper mid-range gaming laptops, but can also be forced to run at lower performance levels. Genius!

{{<figure src="performance-throttle.jpg" caption="Limiting the CPU TDP and GPU Clock makes for great low-end testing">}}

### Emulating a weaker system

Using the **Performance Settings** panel, I can easily test various constellations of CPU and GPU limits. I can make sure that my game runs with the least amount of energy possible.

{{<figure src="performance-overlay.jpg" caption="No fan activity, solid 60 FPS, long battery life, happy user">}}

### Looking deep into frametime

The **Performance Overlay** aka **GAMESCOPE** gives me broad and detailed access to all stats I want to see as a dev and player about my game.

I can **throttle** the Steam Deck to perform like a lower-range device, or test how well my game runs at maximum capacity. This has allowed me to design for an accessible range of hardware and make sure that my game runs well whilst not draining the battery too quickly. Meanwhile, I can profile my game using my engine's profiler, but running on a standalone computer. Perfect.

### No weird background processes or OS reinstalls needed

Having the luxury of SteamOS as a test platform also means that **I don't have to worry about the little aches of the operating system itself.** It's containerized and not prone to random issues or slowdowns.

When I used other Windows machines as a testbed, I had to deal with Windows updates being disruptive or third-party software potentially interfering with performance.

{{<figure src="game-in-editor.jpg" caption="Testing with 1280x800px, the native Steam Deck resolution, in-engine">}}

## 🎨 Steam Deck makes for accessible design

Designing user interfaces that work on the Deck helps my design process. I can be pretty confident that (sometimes with minor modifications), the UI will be nicely readable and usable on a wide range of resolutions when scaled.

The Deck is also another screen (I own the LCD version) that helps me get a feel for how the game might look on other people's machines, regarding contrast ratio and in different glare and brightness scenarios.

Focusing on full controller compatibility first is also easier, in my humble opinion, than trying to tack on controller support later on during development. Adding keyboard and mouse support was pretty easy in my case, but of course that might vary by genre.

Listening to the game audio over the built-in speakers is also a great test for how intelligible the game's sounds will be on very simple setups. Can I heard the music properly? How is the SFX balance? How does it sound on headphones? Really easy to switch.

{{<figure src="the-proton-bugfix.jpg" caption="I found a bug in Proton, am I a real developer now?!">}}

## 💥 Small bumps on the road

Of course not everything is perfect. Sometimes SteamOS updates are just a little bit wonky and it's hard to figure out whether they broke something, or I did. Usually it's me, though. Haha.

I'm quite proud that [I discovered a bug in Proton](https://github.com/ValveSoftware/Proton/issues/6861) that caused the Start/Select buttons to be swapped for my game.

Not just my own game, though! It even affected games such as Starfield (*should I send Todd H. an invoice now? is that how it works? lmao*) and probably the bulk of Unity games.

It was a low-level input mapping issue that I reported directly to the Valve Proton team and a fix was deployed in Proton 8.0-5, so that you don't need to awkwardly press Select when you actually mean Start. I think this was my first contribution as a bug reporter to a project of this size, besides the Unity Engine bugs I've reported thus far.

{{<figure src="my-steam-library.jpg" caption="I mostly play in the living room these days. Deck docked or handheld.">}}

## 🕹️ Work and Play

Most indie devs I know, including yours truly, don't really enjoy games the same way anymore, due to work habits. That is not to say we don't love games, most of us do!

But it's **hard to separate the work mindset** (and furiously taking design notes on cool mechanics, juice elements and storytelling, often many pages while constantly pausing) and **the play mindset** if **all of your workday is spent in front of a game engine**, code editor / IDE or creating game art in blender and other tools.

With the Steam Deck and a **cozy corner** far away from my work desk (I work from home), I can actually relax and allow myself to absorb a game and become immersed, away from notifications. This is probably true for many others, even if you don't make games - this might be one of the biggest selling points of the Deck!

## 💾 Deploying Directly to a Handheld

The Steam Deck makes informal deployments ridiculously easy, you don't even need to be a Steam developer with an account - just pop your game build onto the Deck and add it as a non-steam game. Many of my gamedev friends didn't realise that was all it took. And I hope we'll see more Deck games thanks to that info. 😉

As a matter of fact, for at least half a year or so, this was all I did. 

I wrote a little bash script to *rsync* my game folder from my PC [to the Steam Deck over SSH]({{<ref "how-to-ssh-steam-deck">}}) whenever I rolled a fresh build of the game. Anyone can easily use a Windows (.exe) build from any engine and pick a custom Proton version, or even deploy a Linux-native build.

## 📦 Deploying via Steam

Later on, as playtesting began, I transitioned to using regular Steam builds and just pull the latest updates from Steam like a regular user, from the cloud. Did you know that the cloud is just a computer in someone else's basement?

Being able to jump between branches (e.g. trying out some new beta features) **without leaving Game Mode** is brilliant.

## 💖 Thank you for reading!

I hope that if you're an (aspiring) game developer, or you plan to be, or you have a gamedev friend that you'd like to inspire, that this article has **helped you see some of the insanely cool benefits and fun aspects of developing hand in hand with the Steam Deck.**

I think it's an amazing platform and I'm still a big fan of the device, using it every single day both for work and pleasure, still tinkering with it.

Shameless plug: If you want, [you can check out my game, Black Dragon Mage, via the free demo on Steam right now](https://store.steampowered.com/app/2207230/Black_Dragon_Mage/?utm_source=handheldquest&utm_medium=article_end&utm_campaign=demo). I think it turned out quite well and it still brings me joy both on Steam Deck and Desktop after 1.5 years of development.

### Watch the trailer:

{{< youtube gEwq9Jhulrk >}}

### Play the game:

<steam-app appid="2207230"></steam-app>

