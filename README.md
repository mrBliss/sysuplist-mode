# sysuplist-mode

Emacs Major mode for Yaourt's update selection

## Commentary:

Yaourt is a 3rd party package manager for Arch Linux that also
builds packages from the AUR.  Arch Linux, being a rolling release
distro, often has lots of updates.  One doesn't always want to
install all of the updates.  Yaourt provides a nice way to quickly
deactivate the unwanted updates.  This is done by modifying a text
file opened in the default editor (chosen via $EDITOR).  This file
is called the `sysuplist`, hence the name of this mode.

A snippet from an example sysuplist:

    #######################...
    # Package upgrade only (new release):                 (1)
    #######################...
    core/krb5 # 1.9.1-2 2 -> 3
    # The Kerberos network authentication system
    core/grub # 0.97-17 17 -> 20
    # A GNU multiboot boot loader
    community/exaile # 0.3.2.2-1 1 -> 3
    # A full-featured media player for GTK+
    ...

Updates can be deactivated by commenting them out, i.e. by putting a
`#` in front of them.

The sysuplist files can be quite hard to read because they are
quite dense and have little whitespace.  That's why this mode was
written; to provide colouring, extra whitespace and convenient
bindings for quickly activating or deactivating updates.

After opening a sysuplist file, extra newlines are added between
the updates (the terms: updates, packages and items all mean the
same thing), with the aim of avoiding confusion as to whether a
description of an update belongs to the update above or below it.
This means the file is modified right after the user opens it.

The headers indicating new sections are made read-only (via
text-properties).  For an example of a header, see (1) in the
snippet above.  The user is not supposed to type any text in the
sysuplist file except for the `#`s.  For this reason, the whole
buffer is made read-only.  But this can be turned off (and on
again) with C-x C-q.

The navigation code is quite fragile.  When the user starts to
manually edit a sysuplist file, some features might stop working
properly.

Extra newlines are added every time after opening a sysuplist
files.  But sysuplist files are meant to be edited only once, so
this should not be an issue.


## Dependencies:

No known dependencies.  This mode was written for Emacs 23(.3),
compatibility with other versions cannot be guaranteed.  No exotic
features are used, so it should work with most versions.


## Installation:

Make sure to place `sysuplist-mode.el` somewhere in the load-path
and add the following lines to your `.emacs` file:

    (autoload 'sysuplist-mode "sysuplist-mode.el"
       "Major mode for selection Yaourt updates" t)


## Customization:

There is only setting that can be configured:
`sysuplist-switch-mark-unmark`, this variable indicates whether
'marking' means 'commenting out' or 'commenting in'.

## Usage:

Open a sysuplist file and be greeted with colours and welcome
whitespace.  Users should only use the following bindings:

  * Move between items with `n` and `p`.
  * Move between sections with `N` and `P`.
  * Mark an item with `m` and remove the mark with `u`.
  * Toggle an item between marked an unmarked with `t`.
  * Toggle all items with `T`: marked items become unmarked, and vice
    versa.

## Bugs:

Submit your bug reports to <dewinant@gmail.com>. Thanks.



Copyright (C) 2011 Thomas Winant <dewinant@gmail.com>
