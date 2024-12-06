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

Here I'll input my name, email, GitHub username, some aliases to be able to type less and do more, and connect Git to the OS X Keychain so I don't have to type my username and password every time I want to push to GitHub.

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

## System Settings
Update these later!
Here are a few preferences I like to set:
- **Security and Privacy > FileVault >** On (makes sure SSD is securely encrypted)
- **Security and Privacy > Firewall >** On (extra security measure)
- **Security and Privacy > General >** App Store and identified developers
- **File Sharing >** Off
- **Users & Groups > Login Items >** Spectacle, Flux (I like these to open on startup)
### General
### Appearance
### Control Centre
### Desktop & Dock
### Privacy & Security

What else am I missing?
* Desktop wallpapers—How to make them sync across devices?
* Finder settings
* Dock settings—make smaller, move to the left, instant pop up
* Mouse — increase pointer & scroll speeds, set side buttons, etc.
* Keyboard — modifier keys
* Time machine backup