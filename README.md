# dwm: dynamic window manager

dwm is an extremely fast, small, and dynamic window manager for X.

This is my fork, primarily for my own use.
Here's the [dwm homepage](https://dwm.suckless.org/) and
[upstream git repo](https://git.suckless.org/dwm).


## Modifications

- [pertag](https://dwm.suckless.org/patches/pertag/) (without bar):
  Keeps `layout`, `mwfact`, and `nmaster` per tag instead of global.
- [save floats](https://dwm.suckless.org/patches/save_floats/):
  Remembers size and position of every floating window and window in
  floating layout mode.
- [vanitygaps](https://dwm.suckless.org/patches/vanitygaps/):
  Adds (inner) gaps between client windows and (outer) gaps between
  windows and the screen edge in a flexible manner.
- [noborder](https://dwm.suckless.org/patches/noborder/):
  Removes the border when there is only one window visible.
- [alpha](https://dwm.suckless.org/patches/alpha/):
  Allow translucent bars, keeping the text on it opaque.  Fixes
  transparent borders bug when using a compositor (like picom).
- [hide vacant tags](https://dwm.suckless.org/patches/hide_vacant_tags/):
  Prevents drawing vacant (no clients) tags on the bar.  Stops drawing
  empty rectangles on the bar for non-vacant tags as there is no need.
- Resize hints, borders, and gaps all vanish in monocle layout, but are
  present (when set in config) in all other layouts.
- [actualfullscreen](https://dwm.suckless.org/patches/actualfullscreen/):
  Toggle fullscreen for a window.
- [xrdb](https://dwm.suckless.org/patches/xrdb/):
  Read colors from `xrdb` at run time.


## Requirements

In order to build dwm you need the Xlib header files.


## Installation

Edit `config.mk` to match your local setup (dwm is installed into the
`/usr/local` namespace by default).

Afterwards enter the following command to build and install dwm (if
necessary as root):

    $ make clean install


## Configuration

After an initial build you'll be able to configure dwm by editing the
`config.h` file.


## Running

Add the following line to your `.xinitrc` to start dwm using `startx`:

    exec dwm

In order to connect dwm to a specific display, make sure that the
`DISPLAY` environment variable is set correctly, e.g.:

    DISPLAY=foo.bar:1 exec dwm

(This will start dwm on display `:1` of the host `foo.bar`.)

You can display your own string in the bar using:

    $ xsetroot -name "foo"
