# macOS & Unix: Making the World’s Best Desktop Even Better #

## General Tips ##

1. Drag a file onto the terminal to get its path put on the command line
2. In the Finder `⇧⌘G` gives a dialogue box to open a location, that can use tab completion.
3. Pressing `/` or `⇧⌘G` in any file picker dialogue will give you the same file location dialogue box.
4. Show/hides hidden files in a save dialogue box: `⇧⌘.`

## Text Editing ##

System-wide support for many [GNU readline shortcuts][Readline shortcuts]

Many interactive unix programs support/use readline, so learning these shortcuts is quite useful.

TODO: rails console invocation

## Homebrew ##

You need this. Like now.

Why are you waiting? [Install Homebrew][Homebrew]

Homebrew installs unix utilities properly, inside `/usr/local`. You should _always_ be wary of an installer that wants your administrator password and be especially wary of any command line installation process that whats you to use `sudo`.

TODO: 

## Specific Utilities ##

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
    open -a Safari https://daringfireball.net/ # open a url
    open -a MyFavoriteEditor -W -n # -W: wait until quit, -n: open new instance. This is suitable to use for your VISUAL or EDITOR
    open -R path/to/my/file.jpg # reveal this item in the finder

More [from Brett Terpstra on `open(1)`][Brett Terpstra on open(1)]

### `say(1)` ###

Text to speech from the command line.

If there is [an xkcd cartoon][xkcd on say(1)] on the topic, you know that it’s worth knowing about.

### `caffeinate` ###

Keep your mac from sleeping, or wake it if it is asleep.

    defaults write com.apple.screencapture location ~/Screenshots

[TidBITS has more on Quick Look][TidBITS on Quick Look], including plugins for other file types.

### `mdfind` ###

Search spotlight database.

    mdfind -name query # search file names only
    mdfind -0 # ASCII NUL after each file for piping output to other utils like `xargs -0`
    mdfind -onlyin ../path/to/dir # limit search to specified directory

### Quick Look ###

Open Quick Look from the command line. (This is one you might want to make a bash alias for).

    qlmanage -p my-pretty-picture.jpg
    alias qlook 'qlmanage -p' # create bash alias

Apple Support has [a primer on Quick Look][macOS Sierra: Quick Look], in case you don’t know about.

[Brett Terpstra on open(1)]: http://brettterpstra.com/2014/08/06/shell-tricks-the-os-x-open-command/
[Readline shortcuts]: https://kapeli.com/cheat_sheets/Bash_Shortcuts.docset/Contents/Resources/Documents/index
[xkcd on say(1)]: https://xkcd.com/530/
[Brett Terpstra on caffeinate(1)]: http://brettterpstra.com/2014/02/20/quick-tip-caffeinate-your-terminal/
[TidBITS on Quick Look]: http://tidbits.com/article/16254
[Homebrew]: http://brew.sh
[macOS Sierra: Quick Look]: https://support.apple.com/kb/ph25575

Readline shortcuts:
https://kapeli.com/cheat_sheets/Bash_Shortcuts.docset/Contents/Resources/Documents/index

KeyCastr:
https://github.com/keycastr/keycastr

defaults write com.apple.finder AppleShowAllFiles -bool TRUE

killall Finder

Talk about `sips`

https://osxdaily.com/2013/04/03/keep-track-of-defaults-write-commands-used-in-mac-os-x-automatically/

Here is a random cli tool that I like. It’s on Homebrew as trash:
https://hasseg.org/trash/


