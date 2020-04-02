# dwm: dynamic window manager

dwm is an extremely fast, small, and dynamic window manager for X.
This is a patched and hacked fork of it, primarily for my own use.
Here's the [dwm homepage](https://dwm.suckless.org/) and
[upstream git repo](https://git.suckless.org/dwm).


## Modifications

You may be interested in this
[dwm fork with toggleable patches](https://github.com/bakkeby/dwm-vanitygaps).


### Patches applied

- [pertag](https://dwm.suckless.org/patches/pertag/) without bar
  ([diff](https://dwm.suckless.org/patches/pertag/dwm-6.1-pertag_without_bar.diff)): 
  Keeps `layout`, `mwfact`, and `nmaster` per tag instead of global.
- [savefloats](https://dwm.suckless.org/patches/save_floats/)
  ([diff](https://raw.githubusercontent.com/bakkeby/dwm-vanitygaps/master/patches/dwm-savefloats-configurable-6.2.diff)):
  This patch saves size and position of every floating window and window
  in floating layout mode, for if it's made floating again.
- [vanitygaps](https://dwm.suckless.org/patches/vanitygaps/)
  ([diff](https://dwm.suckless.org/patches/vanitygaps/dwm-vanitygaps-20190508-6.2.diff)):
  Inspired by i3-gaps this allows for toggleable, smart, flexible gaps
  between windows.
- [noborder](https://dwm.suckless.org/patches/noborder/)
  ([diff](https://dwm.suckless.org/patches/noborder/dwm-noborder-6.1.diff)):
  Removes the border when there is only one window visible.
- [alpha](https://dwm.suckless.org/patches/alpha/)
  ([diff](https://dwm.suckless.org/patches/alpha/dwm-alpha-20180613-b69c870.diff)):
  Allow dwm to have translucent bars, while keeping all the text on it
  opaque.  (Also fixes a compton border transparency bug.)


### Hacks

- Resize hints, borders, and gaps all vanish in monocle layout, but are
  present (when set in config) in all other layouts.


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

If you'd like to reload dwm without closing applications (good for
debugging, testing config), run dwm in a while loop:

    while true
    do
        dwm
    done

Now quitting dwm (`mod1+shift+q` by default) will instead reload it,
preserving your applications but resetting tags.  If you wish to kill
dwm:

    $ sudo killall xinit

You can display your own string in the bar using:

    $ xsetroot -name "foo"
