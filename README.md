# st - simple terminal

This project is fork of [st (simple terminal)](https://st.suckless.org/) with some additional features:

* Compatibility with `Xresources` and `pywal` for dynamic colors.
* Default and as fallback [biual](https://github.com/samedamci/biual-dot-conf) colors otherwise.
* Transparency/alpha support, which is also adjustable from `~/.Xresources`.
* Default font is system "`mono`" at 15pt, meaning the font will match your system font.
* [Useful keybindings](#keybindings) for everyday use

## Installation

Make sure you have [dependencies](#dependencies) installed before you install st.

```shell
$ git clone https://github.com/samedamci/st
$ cd st
$ sudo make clean install
```

On OpenBSD, be sure to edit `config.mk` first and remove `-lrt` from the `$LIBS` before compiling.

### Dependencies

Probably you have some required packages on your system already. "No" means that it is recommended as it is needed for some patches, but they aren't needed to make `st` work.

| Required? | Package name | Description
|-----------|--------------|------------
| Yes       | git          | Distributed version control system
| Yes       | make         | Build utility
| Yes       | libx11       | X11 client-side library
| Yes       | libxft       | FreeType-based font drawing library for X
| Yes/No    | fontconfig   | Library for configuring fonts, required for default build as it asks for your system `mono` font
| No        | dmenu        | Generic menu for X, used for selecting urls and for entering unicode codepoint to convert it to glyph which will be pasted into st
| No        | xurls        | Extract urls from plain text, used together with dmenu to select urls

## Keybindings

###### Clipboard
* `Ctrl+Shift+c` - Copy from clipboard
* `Ctrl+Shift+v` - Paste from clipbard
* `Ctrl+Shift+p` - Paste from primary selection

###### Scroll
* `Alt+k/j/↑/↓` - Scroll one line back/forward
* `Shift+Scroll` - Scroll using mouse back/forward
* `Alt+u/d/PageUp/PageDown` - Scroll one page back/forward

###### Resize
* `Ctrl+Alt+k/j/↑/↓` - Increase/decrese font size
* `Alt+Home` - Return to default font size

## Xresources

For many key variables, this build of `st` will look for X settings set in
either `~/.Xdefaults` or `~/.Xresources`. You must run `xrdb` on one of these
files to load the settings, for example: `xrdb ~/.Xresources`.

For example, you can define your desired fonts, transparency or colors:

```
*.background: #0a0a30
*.foreground: #9b9cb5
*.alpha: 150

*.color0:     #0a0a30
*.color1:     #aa2f46
…

*.font:	Liberation Mono:pixelsize=12:antialias=true:autohint=true
```

The `alpha` value (for transparency) goes from `0` (transparent) to `255`
(opaque).
