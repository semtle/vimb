---
title:  vimb - commands
layout: default
meta:   vimb browser ex commands
active: commands
---

# vimb commands

## open
{:#open}

\:o[pen] [URI]
: Open the give URI into current window. If URI is empty the configured
  `home-page` is opened.

\:t[abopen] [URI]
: Open the give URI into a new window. If URI is empty the configured
  `home-page` is opened.

## key mapping

Key mappings allow to alter actions of key presses. Each key mapping is
associated with a mode and only has effect when the mode is active. Following
commands allow the user to substitute one sequence of key presses by another.

Syntax: *:{m}map {lhs} {rhs}*

Note that the lhs ends with the first found space. If you want to use space
also in the {lhs} you have to escape this with a single '\' like shown in the
examples. Standard key mapping commands are provided for these modes m:

- n Normal mode: When browsing normally.
- i Insert mode: When interacting with text fields on a website.
- c Command Line mode: When typing into the vimbs command line.

Most keys in key sequences are represented simply by the character that you see
on the screen when you type them. However, as a number of these characters have
special meanings, and a number of keys have no visual representation, a special
notation is required.

As special key names have the format \<...\>. Following special keys can be
used \<Left\>, \<Up\>, \<Right\>, \<Down\> for the cursor keys, \<Tab\>,
\<Esc\>, \<CR\>, \<F1\>-\<F12\> and \<C-A\>-\<C-Z\>.

\:nm[ap] {lhs} {rhs}
\:im[ap] {lhs} {rhs}
\:cm[ap] {lhs} {rhs}
: Map the key sequence lhs to rhs for the modes where the map command applies.
  The result, including rhs, is then further scanned for mappings. This allows
  for nested and recursive use of mappings.

  - `:cmap <C-G>h /home/user/downloads/`
    Adds a keybind to insert a file path into the input box. This could be
    useful for the ':save' command that could be used as ':save ^Gh'.
  - `:nmap <F1> :set scripts=on<CR>:open !glib<Tab><CR>`
    This will enable scripts and lookup the first bookmarked URI with the tag
    'glib' and open it immediately if F1 key is pressed.
  - `:nmap \ \  50G;o`
    Example which mappes two spaces to go to 50% of the page, start hinting
    mode.

\:nn[oremap] {lhs} {rhs}
\:ino[remap] {lhs} {rhs}
\:cno[remap] {lhs} {rhs}
: Map the key sequence lhs to rhs for the mode where the map command applies.
  Disallow mapping of rhs, to avoid nested and recursive mappings. Often used
  to redefine a command.

\:nu[nmap] {lhs}
\:iu[nmap] {lhs}
\:cu[nmap] {lhs}
: Remove the mapping of lhs for the applicable mode.

## bookmarks

\:bma [TAGS]
: Save the current opened uri with TAGS to the bookmark file.

\:bmr [URI]
: Removes all bookmarks for given URI or if not given the current opened page.

## shortcuts
{:#shortcuts}

Shortcuts allows to open URL build up from a named template with additional
parameters. If a shortcut named 'dd' is defined, you can use it with ':open dd
list of parameters' to open the generated URL.

Shortcuts are a good to use with search engines where the URL is nearly the
same but a single parameter is user defined.

\:shortcut-add SHORTCUT=URI
: Adds a shortcut with the SHORTCUT and URI template. The URI can contain
  multiple placeholders `$0-$9` that will be filled by the parameters given when
  the shortcut is called. The parameters given when the shortcut is called
  will be split into as many parameters like the highest used placeholder.

  - `:shortcut-add dl=https://duckduckgo.com/lite/?q=$0`
    to setup a search engine. Can be called by ':open dl my search phrase'.
  - `:shortcut-add gh=https://github.com/$0/$1`
    to build urls from given parameters. Can be called ':open gh fanglingsu
    vimb'.

\:shortcut-remove SHORTCUT
: Remove the search engine to the given SHORTCUT.

\:shortcut-default SHORTCUT
: Set the shortcut for given SHORTCUT as the default. It doesn't matter if the
  SHORTCUT is already in use or not to be able to set it.

## settings

\:se[t] VAR=VALUE
: Set configuration values named by VAR. To set boolean variable you should
  use 'on', 'off' or 'true' and 'false'. Colors are given as hexadecimal value
  like '#f57700'.

\:se[t] VAR?
: Show the current set value of variable VAR.

\:se[t] VAR!
: Toggle the value of boolean variable VAR and display the new set value.

## queue
{:#queue}

The queue allows to mark URLs for later reding (something like a read it later
list). This list is shared between the single instances of vimb. Only available
if vimb has been compiled with QUEUE feature.

\:qpu[sh] [URI]
: Push URI or if not given current URI to the end of the queue.

\:qu[nshift] [URI]
: Push URI or if not given current URI to the beginning of the queue.

\:qp[op]
: Open the oldest queue entry in current browser window and remove it from the
  queue.

\:qc[lear]
: Removes all entries from queue.

## misc

\:sh[ellcmd] CMD
: Runs given shell CMD syncron and print the output into inputbox. The CMD can
  contain multiple '%' chars that are expanded to the current opened uri. Also
  the '~/' to home dir expansion is available.

  Example: ``:shellcmd echo "`date` %" >> myhistory.txt``

\:s[ave] [PATH]
: Download current opened page into configured download directory. If PATH is
  given, download under this file name or path. Possible value for PATH are
  'page.html', 'subdir/img1.png', '~/downlod.html' or absolute paths
  '/tmp/file.html'.

\:q[uit]
: Close the browser.

\:e[val] JAVASCRIPT
: Runs the given JAVASCRIPT in the current page and display the evaluated
  value.

  Example: `:eval document.cookie`

\:no[rmal][!] [CMDS]
: Execute normal mode commands CMDS. This makes it possible to execute normal
  mode commands typed on the input box. If the '!' is given, mappings will not
  be used.

  Example: `:set scripts!|no! R`

\:ha[rdcopy]
: Print current document. Open a GUI dialog where you can select the printer,
  number of copies, orientation, etc.