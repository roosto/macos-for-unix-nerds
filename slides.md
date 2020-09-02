# macOS & Unix: Two Great Tastes that Taste Great Together! #

---

## Why? ##

* Mid-90s Apple is circling the drain, their OS is a shared memory disaster
* In order to save its bacon, and have a shot at a modern OS, Apple buys NeXT in 1996 (guess who the founder & CEO of NeXT is 🤔)
* macOS né Mac OS X is adapted from NeXTSTEP, which is based off of BSD Unix (BSD is different from linux, b/c GNU)

Now the Mac has a lovely unix underpinning 🎉😎🥳🎊

---

## GUI → CLI Tips ##

* Drag a file onto the terminal to get its path put on the command line
* In the Finder `⇧⌘G` gives a dialogue box to open a location, that can use tab completion.
* Pressing `/` or `⇧⌘G` in any file picker dialogue will give you the same file location dialogue box.
* Show/hides hidden files in a save dialogue box, or in the Finder: `⇧⌘.` (more on this later)

---

## Text Editing ##

System-wide support for many [GNU readline shortcuts][Readline shortcuts]

Most text editing areas in macOS, from file save to web forms will support Readline shortcuts. Many interactive unix programs also support/use readline, so learning these shortcuts is quite useful.

---

## Homebrew ##

The only sane way to install 3rd party unix software on your mac

* Homebrew installs unix utilities properly, inside `/usr/local`
* You should _always_ be wary of an installer that wants your administrator password
* You should almost w/o exception **refuse** to use a command line installation process that wants to be run with `sudo`
* See the [project’s home][Homebrew Project website]

For primers on about the filesystem hierarchy & organization (it’s actually not just chaos). See the manual entry for `hier(7)` or the [Wiki article on the Unix filesystem][Unix filesystem: Conventional directory layout]

---

## Terminal.app ##

Good old sturdy, Terminal.app

* There are many terminal emulators, but this one ~~is mine~~ comes installed on my system
* It’s really mostly good enough

---

## Terminal.app, digging in … ##

Preferences
* meta key setup
* alternate color schemes/font sizes for presentations

Marks & Bookmarks
* setting bookmarks
* navigating between marks
* selecting between marks

---

## Terminal.app, digging in …  m0ar … ##

Searching
* searching with selection
* pasting with selection

Selecting
* columnar selecting with `⌥` dragging

Touch Bar
* man page
* up/down
* bookmark
* color picker (¿why?)

---

## Specific Utilities ##

Now we are entering the realm of CLI → GUI interaction, aka the good stuff

---

### `pbpaste(1)` and `pbcopy(1)` ###

* `pbpaste`: output contents of the “pasteboard” to `STDOUT`
* `pbcopy`: write `STDIN` to the “pasteboard”
* `pbmunge` hashtag-humblebrag on [my custom function for pasteboard manipulation][pbmunge.bash gist]

---

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

## `defaults write` ##

Coming back to showing hidden files. Maybe you’ve seen these?

    defaults write com.apple.finder AppleShowAllFiles YES # this is one is gross


    defaults write com.apple.screencapture location ~/Screenshots

* These can be found out and about on the web
* Be wary of them
    * they get out of date a lot
    * some are dangerous; e.g., turning off Gatekeeper
    * some are redundant to GUI settings

I use [a logging script][log_defaults_writes.bash gist] little technique to record any writes that I make, so that I have some idea of what broke ~~if happen to~~ when I inevitably break something.

---

### `mdfind` ###

Search spotlight database.

    mdfind -name query # search file names only
    mdfind -0 # ASCII NUL after each file for piping output to other utils like `xargs -0`
    mdfind -onlyin ../path/to/dir # limit search to specified directory

---

### Quick Look ###

Open Quick Look from the command line. (This is one you might want to make an alias for).

    qlmanage -p my-pretty-picture.jpg
    alias qlook='qlmanage -p' # create bash alias

Apple Support has [a primer on Quick Look][macOS Sierra: Quick Look], in case you don’t know about.

[TidBITS has more on Quick Look][TidBITS on Quick Look], including plugins for other file types.

---

### `say(1)` ###

Text to speech from the command line.

If there is [an xkcd cartoon][xkcd on say(1)] on the topic, you know that it’s worth knowing about.

### `caffeinate` ###

Keep your mac from sleeping, or wake it if it is asleep. (Like `ssh` into your mac and run this)

[Brett Terpstra on caffeinate(1)][Brett Terpstra on caffeinate(1)]

---

## Made with Mac ##

Tools I used to make this

### KeyCastr ###

The lovely toast messages of my keyboard input, as I type are provided by the [Open Sourced KeyCastr App][KeyCastr project on GitHub]

### Marp ###

The [Marp Project][Marp project website] provides a pretty good Markdown → SPA tool for making simple slide decks.



---

[Homebrew Project website]: https://brew.sh/
[Brett Terpstra on open(1)]: http://brettterpstra.com/2014/08/06/shell-tricks-the-os-x-open-command/
[Readline shortcuts]: https://kapeli.com/cheat_sheets/Bash_Shortcuts.docset/Contents/Resources/Documents/index
[Unix filesystem: Conventional directory layout]: https://en.wikipedia.org/wiki/Unix_filesystem#Conventional_directory_layout
[log_defaults_writes.bash gist]: https://gist.github.com/roosto/af674e123f4cd51be776d9d339a59f2f
[pbmunge.bash gist]: https://gist.github.com/roosto/3a18e2466b058d7ee250793a1926743e
[xkcd on say(1)]: https://xkcd.com/530/
[Brett Terpstra on caffeinate(1)]: http://brettterpstra.com/2014/02/20/quick-tip-caffeinate-your-terminal/
[TidBITS on Quick Look]: http://tidbits.com/article/16254
[Homebrew]: http://brew.sh
[macOS Sierra: Quick Look]: https://support.apple.com/kb/ph25575
[KeyCastr project on GitHub]: https://github.com/keycastr/keycastr
[Marp project website]: https://marp.app/

