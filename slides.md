# macOS & Unix: Two Great Tastes that Taste Great Together! #

---

## Why? ##

1. Mid-90s Apple is circling the drain, their OS is a shared memory disaster
2. In order to save its bacon, and have a shot at a modern OS, Apple buys NeXT in 1996 (guess who the founder & CEO of NeXT is 🤔)
3. macOS né Mac OS X is adapted from NeXTSTEP, which is based off of BSD Unix (BSD is different from linux, b/c GNU)

Now the Mac has a lovely unix underpinning 🎉😎🥳🎊

---

## GUI → CLI Tips ##

1. Drag a file onto the terminal to get its path put on the command line
2. In the Finder `⇧⌘G` gives a dialogue box to open a location, that can use tab completion.
3. Pressing `/` or `⇧⌘G` in any file picker dialogue will give you the same file location dialogue box.
4. Show/hides hidden files in a save dialogue box, or in the Finder: `⇧⌘.` (more on this later)

---

## Text Editing ##

System-wide support for many [GNU readline shortcuts][Readline shortcuts]

Many interactive unix programs support/use readline, so learning these shortcuts is quite useful.

TODO: rails console invocation (fix ctrl-y)
TODO: web form text editing

---

## Homebrew ##

The only sane way to install 3rd party unix software on your mac.

Why are you waiting? [Install Homebrew][Homebrew]

Homebrew installs unix utilities properly, inside `/usr/local`. You should _always_ be wary of an installer that wants your administrator password, and you should basically always refuse to use a command line installation process that want to be run with `sudo`

Learn a few things about the files hierarchy & organization (it’s actually not just chaos). See the manual entry for `hier(7)` or the [Wiki article on the Unix filesystem][Unix filesystem: Conventional directory layout]

---

## `defaults write` ##

Coming back to showing hidden files. Maybe you’ve seen this?

    defaults write com.apple.screencapture location ~/Screenshots
    defaults write com.apple.finder AppleShowAllFiles YES # this is one is gross

These can be found out and about and around. I would be wary of certain ones, b/c they get out of date all the time. Some are dangerous, like turning off Gatekeeper.

I use this little technique to record any writes that I make, so that I have some idea of what broke if I break something.

---

## Terminal.app ##

Good old sturdy, Terminal.app

There are many other terminal emulators, but this one comes installed on my system.

It’s mostly good enough.

---

## Terminal.app, digging in … ##

Preferences
* meta key setup
* alternate color schemes/font sizes for presentations

Marks & Bookmarks
* setting bookmarks
* navigating between marks
* selecting between marks

Searching
* searching with selection
* pasting with selection

Touch Bar
  * man page
  * up/down
  * bookmark
  * color picker (¿why?)

---

## Specific Utilities ##

Now we are entering the realm of CLI → GUI interaction, aka the good stuff

---

## Greatest Hits ##

### `pbpaste(1)` and `pbcopy(1)` ###

`pbpaste`: output contents of the “pasteboard” to `STDOUT`
`pbcopy`: write `STDIN` to the pasteboard

TODO: my own invention: `pbmunge`

### `open(1)` ###

Open a file or folder, as if it has been double clicked on in the Finder. Or a URL in the correct application.

Common uses:

    open . # open current working directory in Finder
    open -a Mail some-file.txt # open Mail.app, creating a new blank message with some-file.txt as an attachment
    open https://daringfireball.net/ # open a url
    open -a Safari https://daringfireball.net/ # open a url with a specific browser
    open -a Sublime -W -n # -W: wait until quit, -n: open new instance. This is suitable to use for your VISUAL or EDITOR
    open -R path/to/my/file.jpg # reveal this item in the finder

More [from Brett Terpstra on `open(1)`][Brett Terpstra on open(1)]

---

## Useful macOS Specific Features ##

### `mdfind` ###

Search spotlight database.

    mdfind -name query # search file names only
    mdfind -0 # ASCII NUL after each file for piping output to other utils like `xargs -0`
    mdfind -onlyin ../path/to/dir # limit search to specified directory

### Quick Look ###

Open Quick Look from the command line. (This is one you might want to make an alias for).

    qlmanage -p my-pretty-picture.jpg
    alias qlook 'qlmanage -p' # create bash alias

Apple Support has [a primer on Quick Look][macOS Sierra: Quick Look], in case you don’t know about.

[TidBITS has more on Quick Look][TidBITS on Quick Look], including plugins for other file types.

---

### `say(1)` ###

Text to speech from the command line.

If there is [an xkcd cartoon][xkcd on say(1)] on the topic, you know that it’s worth knowing about.

### `caffeinate` ###

Keep your mac from sleeping, or wake it if it is asleep.

---

## KeyCastr ##

The lovely toast messages of my keyboard input, as I type are provided by the Open Sourced KeyCastr App


---

[Brett Terpstra on open(1)]: http://brettterpstra.com/2014/08/06/shell-tricks-the-os-x-open-command/
[Readline shortcuts]: https://kapeli.com/cheat_sheets/Bash_Shortcuts.docset/Contents/Resources/Documents/index
[Unix filesystem: Conventional directory layout][https://en.wikipedia.org/wiki/Unix_filesystem#Conventional_directory_layout]
[xkcd on say(1)]: https://xkcd.com/530/
[Brett Terpstra on caffeinate(1)]: http://brettterpstra.com/2014/02/20/quick-tip-caffeinate-your-terminal/
[TidBITS on Quick Look]: http://tidbits.com/article/16254
[Homebrew]: http://brew.sh
[macOS Sierra: Quick Look]: https://support.apple.com/kb/ph25575
[KeyCastr project on GitHub]: https://github.com/keycastr/keycastr

