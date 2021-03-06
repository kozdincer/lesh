[lesh](http://kaan.ozdincer.com/) - the friendly/milli interactive shell [![Build Status](https://travis-ci.org/fish-shell/fish-shell.svg?branch=master)](https://travis-ci.org/fish-shell/fish-shell)
================================================

fish is a smart and user-friendly command line shell for OS X, Linux, and the rest of the family. fish includes features like syntax highlighting, autosuggest-as-you-type, and fancy tab completions that just work, with no configuration required.

For more on fish's design philosophy, see the [design document](http://fishshell.com/docs/current/design.html).

## Quick Start

fish generally works like other shells, like bash or zsh. A few important differences can be found at <http://fishshell.com/docs/current/tutorial.html> by searching for the magic phrase "unlike other shells".

Detailed user documentation is available by running `help` within fish, and also at <http://fishshell.com/docs/current/index.html>

## Building

fish requires a C++11 compiler. It builds successfully with g++ 4.8 or later, or with clang 3.3 or later.

fish can be built using autotools or Xcode. autoconf 2.60 or later, as well as automake 1.13 or later, are required to build from git versions. These are not required to build from released tarballs.

fish depends on a curses implementation, such as ncurses. The headers and libraries are required for building.

fish requires PCRE2 due to the regular expression support contained in the `string` builtin. A copy is included with the source code, and will be used automatically if it does not already exist on your system.

fish requires gettext for translation support.

Building the documentation requires Doxygen 1.8.7 or newer.

### Autotools Build

    autoreconf --no-recursive [if building from Git]
    ./configure
    make [gmake on BSD]
    sudo make install

### Xcode Development Build

* Build the `base` target in Xcode
* Run the fish executable, for example, in `DerivedData/fish/Build/Products/Debug/base/bin/fish`

### Xcode Build and Install

    xcodebuild install
    sudo ditto /tmp/fish.dst /
    
## Milli Build
    make milli

## Help, it didn't build!

If fish reports that it could not find curses, try installing a curses development package and build again.

On Debian or Ubuntu you want:

    sudo apt-get install build-essential ncurses-dev libncurses5-dev gettext autoconf

On RedHat, CentOS, or Amazon EC2:

    sudo yum install ncurses-devel

## Runtime Dependencies

fish requires a curses implementation, such as ncurses, to run.

fish requires PCRE2 due to the regular expression support contained in the `string` builtin. A bundled version will be compiled in automatically at build time if required.

fish requires a number of utilities to operate, which should be present on any Unix, GNU/Linux or OS X system. These include (but are not limited to) hostname, grep, awk, sed, which, and getopt. fish also requires the bc program.

Translation support requires the gettext program.

Usage output for builtin functions is generated on-demand from the installed manpages using `nroff` and `ul`.

Some optional features of fish, such as the manual page completion parser and the web configuration tool, require Python.

In order to generate completions from man pages compressed with either lzma or xz, you may need to install an extra Python package. Python versions prior to 2.6 are not supported.  To process lzma-compresed manpages, backports.lzma is needed for Python 3.2 or older. From version 3.3 onwards, Python already includes the required module.

## Packages for Linux

Instructions on how to find builds for several Linux distros are at <https://github.com/fish-shell/fish-shell/wiki/Nightly-builds>

## Switching to fish

If you wish to use fish as your default shell, use the following command:

	chsh -s /usr/local/bin/fish

chsh will prompt you for your password, and change your default shell. Substitute "/usr/local/bin/fish" with whatever path to fish is in your /etc/shells file.

Use the following command if you didn't already add your fish path to /etc/shells.

    echo /usr/local/bin/fish | sudo tee -a /etc/shells

To switch your default shell back, you can run:

	chsh -s /bin/bash

Substitute /bin/bash with /bin/tcsh or /bin/zsh as appropriate.

You may need to logout/login for the change (chsh) to take effect.

## Contributing Changes to the Code

See the [Guide for Developers](CONTRIBUTING.md).

## Contact Us

Questions, comments, rants and raves can be posted to the official fish mailing list at <https://lists.sourceforge.net/lists/listinfo/fish-users> or join us on our [gitter.im channel](https://gitter.im/fish-shell/fish-shell) or IRC channel [#fish at irc.oftc.net](https://webchat.oftc.net/?channels=fish). Or use the [fish tag on Stackoverflow](https://stackoverflow.com/questions/tagged/fish).

Found a bug? Have an awesome idea? Please open an issue on this github page.
