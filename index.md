---
title:  Vimb - Vim Browser
layout: default
meta:   vimb the vim browser is a fast, keyboard driven and lightweight web-browser
active: home
---

# vimb - a vim-like webkit browser

[vimb][] is a fast and lightweight web browser based on the webkit web browser
engine and the gtk toolkit. vimb is modal like the great vim editor and also
easily configurable during runtime. vimb is mostly keyboard driven and does
not detract you from your daily work.

## screenshots

There isn't really much to see for a browser that controlled via keyboard and
a single inputbox, but following images may give a impression of they way vimb
makes you more productive in your work.

[![link hinting](media/tn/vimb-hints.png "link hinting (688x472 33kB)"){:width="300"}{:height="206"}](media/vimb-hints.png)
[![setting completion of vimb](media/tn/vimb-completion.png "completion of settings (688x472 11kB)"){:width="300"}{:height="206"}](media/vimb-completion.png)

## features

- modal like vim
- vim oriented [keybindings][]
- follow links via keyboard [hints][]
- read it later [queue][] to collect URIs for later use
- tagged bookmarks
- cookie support
- userscripts support
- customer stylesheet support
- completions for commands, url history, bookmarks, boorkamrk tags, variables
  and search queries
- [history][] for commands, url and search queries
- open textareas with configurable editor
- user defined url [shortcuts][] with up to 9 placeholders
- xembed - so vimb can be used together with [tabbed][]
- run shell commands from inputbox

## install

1. Download the sources

   - You can get vimb from github with following command.
   
         git clone git://github.com/fanglingsu/vimb.git vimb
   
   - Or you can download the latest releases as [tar.gz][tgz] or as [zip][].

2. Edit `config.mk` to match your local setup.

3. Edit `config.h` to match you personal preferences.

   The default Makefile will not overwrite your customised `config.h` with the
   contents of `config.def.h`, even if it was updated in the latest git pull.
   Therefore, you should always compare your customised `config.h` with
   `config.def.h` and make sure you include any changes to the latter in your
   `config.h`.

4. Run following command to compile and install vimb (if necessary last one as
   root).

       make clean && make
       make install

## dependencies

- libwebkit >= 1.3.10
- libgtk+-2.0
- libsoup-2.4

## contribute

If you find a misbehaviour or have feature requests use the
[issue tracker][bug] provided by github or via [mailing list][mail].

## alternatives

- [vimprobable][] this was the initial inspiration for the vimb browser and has
  a lot of features in common
- [surf][] a really minimalistic browser of the suckless project. No runtime
  configuration.

[zip]:         https://github.com/fanglingsu/vimb/archive/master.zip "vim browser download zip"
[tgz]:         https://github.com/fanglingsu/vimb/archive/master.tar.gz "vim browser download tar.gz"
[bug]:         https://github.com/fanglingsu/vimb/issues "vimb browser - issue tracker"
[surf]:        http://surf.suckless.org/
[vimb]:        https://github.com/fanglingsu/vimb "vimb vimlike webbrowser sources"
[vimprobable]: http://sourceforge.net/apps/trac/vimprobable/
[tabbed]:      http://tools.suckless.org/tabbed/
[keybindings]: keybindings.html
[hints]:       keybindings.html#hinting
[history]:     keybindings.html#history
[queue]:       commands.html#queue
[shortcuts]:   commands.html#shortcuts
[mail]:        https://lists.sourceforge.net/lists/listinfo/vimb-users "vimb - mailing list"