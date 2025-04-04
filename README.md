# How I set up a new machine (README)

**Motivation:** The follow spec details how I set up a brand new macOS computer, for writing, software development, and everyday productivity. I maintain it to streamline the process each time I do it.

**Last updated:** 12 Nov 2024
## Info
* Stored at [ohong/new-machine-setup](https://github.com/ohong/new-machine-setup)
  * https://github.com/ohong/new-machine-setup/blob/master/Brewfile
* Filename: `~/dev/new-machine-setup/Brewfile`
* Current OS: macOS Sequoia 15.1
## Changelog
### Nov 2024
* Added a changelog
* Removed the screenshots, unnecessary
* No longer using (remove from Brewfile):
  * Alfred, replaced by Raycast
  * Atom, replaced by VS Code & Cursor
  * Google Chrome, replaced by Arc browser
  * iTerm, replaced by Warp
  * Magnet, replaced by Raycast (Window Management)
  * Dropbox, just use the web interface, or Google Drive or iCloud storage
  * Fantastical, replaced by Notion Calendar
  * Spark, replaced by Superhuman
  * TunnelBear, replaced by NordVPN
* Added new apps I use now under “Applications” & to the Brewfile
* Removed step of adding `brewup` alias to my bash profile
* Removed steps for installing Node JS, npm, Ruby, composer, virtual hosts. I just don’t use them enough to justify doing on every fresh setup.
* Removed section on customising iTerm, I just use Warp now
* Removed section on changing OS defaults from command line
* Shortened section on SSH & combined it with GitHub set up
* Added all Finder & System Settings changes
## Applications
All via the `Brewfile` `cask` and `mas` commands.
### Essential
* [x] Arc — web browser
* [x] Bear — Markdown notes
* [x] Notion — personal database / 2nd brain
* [x] 1Password — password manager
* [x] Raycast — launcher
* [x] Things 3 — task manager
### Programming
- [x] Visual Studio Code
- [x] Cursor — AI code editor
- [x] Windsurf — another AI code editor
- [x] Linear — project management
- [x] Postman — API testing tool
- [x] Warp — Terminal replacement
### Other
- [x] AppCleaner
- [x] Bartender 5 — menu bar organiser
- [x] CheatSheet
- [x] Clay
- [x] Cubby
- [x] DaisyDisk
- [x] Descript
- [x] Discord
- [x] Limitless
- [x] LINE
- [x] Logi Options+
- [x] Loom
- [x] MacWhisper
- [x] NordVPN
- [x] Notion Calendar
- [x] Numi
- [x] One Thing
- [x] Perplexity
- [x] Poe
- [x] Raindrop
- [x] Rewind
- [x] Rize — AI time tracking
- [x] RODE Connect
- [x] Screen Studio
- [x] Shortcat
- [x] Slack
- [x] Spotify
- [x] Streamlabs — Live streaming
- [x] Superhuman
- [x] Texts — Unified inbox for messages
- [x] Wispr Flow — Voice dictation
- [x] Zoom
## Install via command line
### Homebrew (macOS package manager)
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### Mac App Store (mas)

The Mac App Store command line interface, or [mas-cli](https://github.com/mas-cli/mas), will allow you to install from the App Store.
```bash
brew install mas
```

If you haven't already logged into the App Store, you can do so now.

```bash
mas signin email@email.com
```

#### Brewfile

`Brewfile` lists all the programs I want on my machine and install them in a bundle. It is in this repository.

Simply run this command to install the bundle:

```bash
brew bundle install
```

Alternatively, I can bundle install from a Brewfile hosted on my GitHub, without creating a local copy:
```bash
curl -fsSL https://raw.githubusercontent.com/ohong/new-machine-setup/blob/master/Brewfile | brew bundle --file=-
```

### GitHub & SSH
* [Generate a new SSH key and add it to to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
* [Add the new SSH key to my GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

#### Config - `~/.gitconfig`

```bash
touch ~/.gitconfig
```

Here I'll input my name, email, GitHub username, some aliases to be able to type less and do more:

```bash
[user]
    name = First Last
    email = email@email.com
[github]
    user = username
[alias]
    a = add
    ca = commit -a
    cam = commit -am
    s = status
    pom = push origin master
    pog = push origin gh-pages
    puom = pull origin master
    puog = pull origin gh-pages
    cob = checkout -b
```

With the above aliases, I can run `git s` instead of `git status`, for example.

### Change settings via command line
Hide all icons on desktop:
```
defaults write com.apple.finder CreateDesktop false;killall Finder
```

Remove Dock delays:
```
defaults write com.apple.dock autohide-delay -float 0; defaults write com.apple.dock autohide-time-modifier -int 0;killall Dock
```

Disable disk warnings:
```
sudo defaults write /Library/Preferences/SystemConfiguration/com.apple.DiskArbitration.diskarbitrationd.plist DADisableEjectNotification -bool YES && sudo pkill diskarbitrationd
```

Change screenshot default to JPG (smaller files vs. PNG):
```
defaults write com.apple.screencapture type jpg
```

Make hidden app icons transparent in Dock:
```
defaults write com.apple.Dock showhidden -bool TRUE && killall Dock
```
## Sync app settings
- [x] Export the latest Raycast “Settings & Data”, then import into new machine.
### Browser extensions
- [x] 1Password
- [x] uBlock Origin (N.B. no long compatible with Chromium after June 2025)
- [x] Archive Page
- [x] Raindrop.io
## Finder
- [x] General -> Don’t show any items on the desktop, New Finder windows show: Documents, Sync Desktop & Documents folders
- [x] Sidebar: Show ohong (Home), Recents, Applications, Downloads, dev
- [x] Advanced -> When performing a search: Search the Current Folder
- [x] Change to List view
- [x] For each file, show: Name, Date Modified, Size, Kind
- [x] View -> Show Path Bar, Show Status Bar
- [x] Customise Toolbar: add Airdrop & Share
- [x] Make my own “Recents” folder: New Smart Folder -> Opened within last 7 days, NOT Applications
## System Settings
### Network
- [x] Set service order, prioritise Ethernet connection over WiFi
- [x] Firewall: ON
### General
- [x] Switch to 24-hour time & show 24h time on Lock Screen
* Open at Login:
  - [x] Bartender 5
  - [x] CheatSheet
  - [x] Raycast
  - [x] Rewind
  - [x] Supercharge
  - [x] Things Helper
### Appearance
- [x] Show scroll bars: When scrolling
- [x] Click in the scroll bar to: Jump to the spot that’s clicked
### Control Centre
- [x] Clean up, remove Spotlight Search et al.
### Desktop & Dock
- [x] Make dock smaller, small magnification
- [x] Move to left of the screen
- [x] Minimise windows using Scale Effect
- [x] Minimise windows into application icon = ON
- [x] Automatically hide and show the Dock = ON
- [x] Show recent apps = OFF.
- [x] Tiled windows have margins = OFF
- [x] Default web browser = Arc
* Hot corners:
  - [x] Top-left (+ Cmd) = Lock Screen
  - [x] Bottom-left (+ Cmd) = Notification Centre
  - [x] Top-right = Desktop
  - [x] Bottom-right = Mission Control
### Displays
- [x] More Space
- [x] Night Shift: Turn on from Sunset to Sunrise
### Privacy & Security
- [x] FileVault: ON (makes sure SSD is securely encrypted)
- [x] Allow applications from: App Store and Known Developers
### Login Password
- [x] Use Apple Watch to unlock
### Keyboard
- [x] Fastest key repeat rate, shortest delay until repeat
- [x] Keyboard Shortcuts -> Spotlight -> Deselect shortcuts
- [x] Remap Modifier Keys:
  - [x] Caps Lock = Escape
  - [x] For external keyboards: swap Option <> Command
- [x] Text Input -> Edit: Turn OFF correct spelling, capitalise words, etc. Keep add full stop with double-space.
### Mouse
- [x] Max pointer & scroll speeds
- [x] Side buttons to move between desktop
- [x] Wheel click = Cmd + W (close tab / window)
- [x] Scroll direction = Standard

---
## Sandbox
What else am I missing?
* Desktop wallpapers—How to make them sync across devices?
* Brew packages I’m testing: 
* Apps testing: [Supercharge](https://sindresorhus.com/supercharge), [Windsurf](https://codeium.com/windsurf) (Cursor competitor)