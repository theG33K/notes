
# My Minimal KDE on Fedora Adventure: A Tech Blogger's Guide

![A sleek, modern desktop showing the Fedora and KDE logos side-by-side](https://i.imgur.com/7lG06rL.png)

Hey everyone, and welcome back to the blog! Today, I'm diving into a topic that's near and dear to my heart: crafting the perfect desktop environment. Specifically, I'm going to walk you through how to install a *minimal* KDE Plasma desktop on a fresh Fedora installation.

## Why Go Minimal?

You might be asking, "Why not just install the KDE spin of Fedora?" And that's a great question! The default KDE spin is fantastic, but it comes with a lot of pre-installed applications and services. For those of us who like to have complete control over our systems, a minimal install is the way to go. You start with a bare-bones system and add only the components you need. The result? A lightning-fast, bloat-free desktop that's tailored to your exact workflow.

## Prerequisites

Before we begin, you'll need a few things:

*   **The Fedora Netinstall ISO:** You can grab this from the official Fedora website.
*   **A USB drive:** We'll use this to create a bootable installer.
*   **An internet connection:** The Netinstall ISO downloads the packages during installation, so you'll need to be online.

## The Installation Dance

This is where the magic happens. We're going to use the Fedora installer to lay the foundation for our minimal KDE desktop.

### Step 1: Booting Up

Boot from the USB drive you created. You'll be greeted by the Fedora installer.

![A screenshot of the initial Fedora installer screen, showing language selection.](https://i.imgur.com/gOQ5Z3j.png)

### Step 2: The "Minimal Install" Option

This is the most important step. On the "Software Selection" screen, make sure you select **"Minimal Install"**. This will give us a bare-bones system with no graphical interface.

![A screenshot of the Fedora installer's "Software Selection" screen, with "Minimal Install" highlighted.](https://i.imgur.com/Y1h3dJ7.png)

### Step 3: Patience is a Virtue

The installer will now do its thing. Since we're downloading the packages from the internet, this might take a little while. Go grab a coffee!

![A time-lapse of a coffee cup emptying, with the Fedora installation progress bar in the background.](https://i.imgur.com/hJ8v6pL.png)

## Bringing KDE to Life

Once the installation is complete, you'll reboot into a command-line interface. Don't be scared! This is where we'll install KDE Plasma.

### Step 4: The Command Line

First, we need to install the KDE Plasma desktop. Run the following command:

```bash
sudo dnf groupinstall "KDE Plasma Workspaces"
```

This will download and install the core KDE packages.

### Step 5: Enabling the Graphical Interface

Next, we need to tell the system to boot into the graphical interface by default. Run this command:

```bash
sudo systemctl set-default graphical.target
```

### Step 6: The Grand Finale

Reboot your system, and you should be greeted by the beautiful KDE Plasma desktop!

![A stunning screenshot of a clean, minimal KDE Plasma desktop with a simple wallpaper and a single terminal window open.](https://i.imgur.com/S3g7vjW.png)

## And That's a Wrap!

And there you have it! A minimal KDE Plasma desktop on Fedora, ready for you to customize to your heart's content. I hope you found this guide helpful. If you have any questions, feel free to drop a comment below. Until next time, happy hacking!
