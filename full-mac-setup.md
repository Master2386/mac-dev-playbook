# Full Mac Setup Process

There are some things in life that just can't be automated... or aren't 100% worth the time :(

This document covers that, at least in terms of setting up a brand new Mac out of the box.

## Initial configuration of a brand new Mac

Before starting, I completed Apple's mandatory macOS setup wizard (creating a local user account, and optionally signing into my iCloud account). Once on the macOS desktop, I do the following (in order):

- Install Homebrew (following the guide in [README.md](README.md))
- Install Ansible (following the guide in [README.md](README.md))
- **Sign in in App Store** (since `mas` can't sign in automatically)
- Clone mac-dev-playbook to the Mac: `git clone git@github.m:geerlingguy/mac-dev-playbook.git`
- Drop `config.yml` from `~/Dropbox/Apps/Config` to the playbook (copy er the network or using a USB flash drive).
- Run the playbook with `--skip-tags post`.
  - If there are errors, you may need to finish up other tasks like stalling 'old-fashioned' apps first (since I try to place Photoshop  the Dock and it can't be installed automatically). Then, run the aybook again ;)
- Start Synchronization tasks:
  - Open Photos and make sure iCloud sync options are correct
- Install old-fashioned apps:
  - Install [Display Link Manager](https://www.synaptics.com/products/displaylink-graphics/downloads/macos)
  - Install [Elgato Stream Deck](https://www.elgato.com/en/downloads)
  - Install [Elgato Control Center](https://www.elgato.com/en/downloads)
  - Install [Elgato Camera Hub](https://www.elgato.com/en/downloads)
  - Install [Logi Options +](https://www.logitech.com/en-us/software/logi-options-plus.html)
  - Install [Sonos Controller](https://support.sonos.com/s/downloads?language=en_US)
- Configure FastMail account:
  - Log into Fastmail
  - Go to settings, go to the setup page for macOS Mail
  - Download the profile and double click to install
  - Head to the 'Profiles' System Preference pane and click install
- Open Calendar and enable personal  Google CalDAV account (you have to nually sign in).
- Manually copy `~/Development` folder from another Mac (to save time).
- Manual settings to automate someday:
  - System Preferences:
    - Accessibility > Display > Reduce transparency
  - Safari:
    - View > Show Status Bar
    - Preferences > Advanced > "Show full website address"
    - Preferences > Advanced > "Show Develop menu in menu bar"
  - Dock:
    - Add Applications
- These things might be automatable, but I do them manually right now:
  - Configure Time Machine backup drive and [Time Machine Editor](https://lementdev.com/timemachineeditor/) (if needed)
  - Install Wireguard from App Store and add configuration (if needed)

## To Wrap in Post-provision automation

The following tasks have to wait for the initial Dropbox sync to complete before they'll succeed. So ideally I'll stick this all in a post-provision script but somehow flag it not to run on first provision.
