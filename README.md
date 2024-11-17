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
## Applications
All via the `Brewfile` `cask` and `mas` commands.
### Essential
* [ ] Arc — web browser
* [ ] Bartender 5 — menu bar organiser
* [ ] Bear — Markdown notes
* [ ] Notion — 2nd brain
* [ ] 1Password — password manager
* [ ] Raycast — launcher
* [ ] Things 3 — task manager
### Programming
- [ ] Cursor — AI code editor
- [ ] Linear — project management
- [ ] Postman — API testing tool
- [ ] Visual Studio Code
- [ ] Warp — a better terminal
### Other
- [ ] AppCleaner
- [ ] CheatSheet
- [ ] Clay
- [ ] Cubby
- [ ] DaisyDisk
- [ ] Descript
- [ ] Discord
- [ ] Limitless
- [ ] LINE
- [ ] Logi Options+
- [ ] Loom
- [ ] MacWhisper
- [ ] NordVPN
- [ ] Notion Calendar
- [ ] Numi
- [ ] One Thing
- [ ] Perplexity
- [ ] Poe
- [ ] Raindrop
- [ ] Rewind
- [ ] Rize — AI time tracking
- [ ] RODE Connect
- [ ] Screen Studio
- [ ] Shortcat
- [ ] Slack
- [ ] Spotify
- [ ] Streamlabs — Live streaming
- [ ] Superhuman
- [ ] Texts — Unified inbox for messages
- [ ] Wispr Flow — Voice dictation
- [ ] Zoom
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

`Brewfile` lists all the programs I want on my machine and install them in a bundle.

Open Terminal, which will be in your home folder by default (`/Users/you`). Create the file.

```bash
touch Brewfile
```

Below are the entire contents of my `Brewfile`, which will install all the above programs with a single command.

```js
brew '1password-cli'
brew 'ata'
brew 'cask'
brew 'gh'
brew 'git'
brew 'htop'
brew 'imagemagick'
brew 'mailsy'
brew 'mas'
brew 'mpv'
brew 'python'
brew 'speedtest-cli'
brew 'wifi-password'
brew 'yt-dlp'

cask '1password'
cask 'appcleaner'
cask 'arc'
cask 'automattic-texts'
cask 'bartender'
cask 'cheatsheet'
cask 'clay'
cask 'cursor'
cask 'daisydisk'
cask 'descript'
cask 'discord'
cask 'limitless'
cask 'linear-linear'
cask 'logi-options+'
cask 'loom'
cask 'macwhisper'
cask 'nordvpn'
cask 'notion'
cask 'notion-calendar'
cask 'numi'
cask 'poe'
cask 'postman'
cask 'raindropio'
cask 'raycast'
cask 'rewind'
cask 'rize'
cask 'rode-connect'
cask 'screen-studio'
cask 'shortcat'
cask 'slack'
cask 'spotify'
cask 'streamlabs'
cask 'superhuman'
cask 'thingsmacsandboxhelper'
cask 'visual-studio-code'
cask 'zoom'
cask 'chatgpt'

mas 'Bear', id: 1091189122
mas 'FuzzyTime', id: 950297057
mas 'Kindle', id: 302584613
mas 'LINE', id: 539883307
mas 'One Thing', id: 1604176982
mas 'Perplexity', id: 6714467650
mas 'Things', id: 904280696
```

Now simply run this command to install the bundle.

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
- [ ] Export the latest Raycast “Settings & Data”, then import into new machine.

### Browser extensions
- [ ] 1Password
- [ ] uBlock Origin (N.B. no long compatible with Chromium after June 2025)
- [ ] Archive Page
- [ ] Raindrop.io

## System Settings
Update these later!
Here are a few preferences I like to set:
- **Security and Privacy > FileVault >** On (makes sure SSD is securely encrypted)
- **Security and Privacy > Firewall >** On (extra security measure)
- **Security and Privacy > General >** App Store and identified developers
- **File Sharing >** Off
- **Users & Groups > Login Items >** Spectacle, Flux (I like these to open on startup)
### General
* Switch to 24-hour time & show 24h time on Lock Screen
* Open at Login: 
### Appearance
### Control Centre
### Desktop & Dock
* Make dock smaller, small magnification
* Move to left of the screen
* Minimise windows using Scale Effect
* Automatically hide and show the Dock = ON
* Show recent apps = OFF
* Tiled windows have margins = OFF
* Default web browser = Arc
* Hot corners:
  * Top-left (+ Cmd) = Lock Screen
  * Bottom-left (+ Cmd) = Notification Centre
  * Top-right = Desktop
  * Bottom-right = Mission Control

### Privacy & Security

What else am I missing?
* Desktop wallpapers—How to make them sync across devices?
* Finder settings
* Mouse
  * Max pointer & scroll speeds
  * Side buttons to move between desktop
  * Wheel click = Cmd + W (close tab / window)
  * Scroll direction = standard
* Keyboard
  * Fastest key repeat rate, shortest delay until repeat
  * Remap modifier keys: Caps Lock = Escape, (for external keyboards) Option = Command, Command = Option
  * Spotlight: Deselect shortcuts
* Time machine backup
---
## Sandbox
* Brew packages I’m testing: 
* Apps testing: [Supercharge](https://sindresorhus.com/supercharge), [Windsurf](https://codeium.com/windsurf) (Cursor competitor)
* Turn on unlock with Apple Watch 
- keyboard > keyboard shortcuts > modifier keys: map caps lock to escape
- Displays: More space