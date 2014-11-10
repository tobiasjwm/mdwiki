# Homebrew

[Homepage](http://brew.sh)


## Install Homebrew

    ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"


## FAQ


### How do I update my local packages?

First update the formulae and Homebrew itself:

    brew update

You can now find out what is outdated with:

    brew outdated

Upgrade everything with:

    brew upgrade

Or upgrade a specific formula with:

    brew upgrade $FORMULA


### How do I uninstall old versions of a formula?

By default, Homebrew does not uninstall old versions of a formula, so
over time you will accumulate old versions. To remove them, simply use:

    brew cleanup $FORMULA

or clean up everything at once:

    brew cleanup

to see what would be cleaned up:

    brew cleanup -n


### How do I uninstall Homebrew?

If you installed to `/usr/local` then you can use the script in [this gist](https://gist.github.com/1173223) to uninstall — it will only remove Homebrew and the stuff Homebrew installed leaving anything else in `/usr/local` alone.

Provided you haven’t put anything else in Homebrew’s prefix (`brew --prefix`), you can generally just `rm -rf` that directory. This is because Homebrew won’t touch files outside its prefix.


### How do I uninstall a formula?

If you do not uninstall all of the versions that Homebrew has installed, Homebrew will continue to attempt to install the newest version it knows about when you do (`brew upgrade`). This can be surprising.

To remove a formula entirely, you may do

    brew uninstall formula_name --force

Be careful as this is a destructive operation and unfortunately, in Homebrew 0.9.5 it seems that Homebrew does not support the `--dry-run` option.

### Where does stuff get downloaded?

    brew --cache

Which is usually: `/Library/Caches/Homebrew`

### Add /usr/local/bin to your path
*This works on Mountain Lion*

    launchctl setenv PATH "/usr/local/bin:$PATH"

[More details here](http://stackoverflow.com/questions/135688/setting-environment-variables-in-os-x/5444960#5444960), including how to set this across reboots.  
If you’re pre-Mountain Lion, [here’s an official alternative](http://developer.apple.com/library/mac/#qa/qa1067/_index.html).