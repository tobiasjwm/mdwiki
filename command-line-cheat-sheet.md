# Command Line Cheat Sheet

## Purpose

The following is a list of commands that I have learned and found useful. This document began as a running list of commands and continues to be so. I have begun cleaning up the document and providing a consistent style, but you may find many formatting mistakes. Rest assured that the work is good quality. Of course, always use extreme caution when using `sudo`. Virtual machines make good playgrounds if you worry about blowing things up. 

## Scope

This document references shell commands for the [BASH Shell](https://en.m.wikipedia.org/wiki/Bash_(Unix_shell)), the default shell for Mac users. If you know enough to set an alternative shell, you don't need this reference. 

## References

Many external references are made in this document and are hyperlinked to their original sources. Her are some other materials you may find helpful. 

### Books

[Take Control of the Command Line with Terminal](http://www.takecontrolbooks.com/command-line)

### Websites

Craig Hockenberry has some [great Terminal tips](http://furbo.org/2014/09/03/the-terminal/) at his website [furbo.org]().
If you need to work on networking in the terminal, the [Krypted.com]() article [Mac Network Commands Cheat Sheet](http://krypted.com/mac-security/mac-network-commands-cheat-sheet/) has what you need. 
[Der Flounder](http://derflounder.wordpress.com/), Rich Trouton's blog about Mac management.  
[Managing OS X](http://managingosx.wordpress.com/), Greg Neagle's blog about Mac management.  


## Shortcuts

### Navigation

- `!!` = Repeat a command. This is incredibly useful when you typed a command and forgot to use `sudo`.

	```bash
	$ tmutil disable
	tmutil: disable requires root privileges.
	$ sudo !!
	sudo tmutil disable
	```
	
- `!$` = reuse last item of previous command

	```bash
	$ cat text.txt
	$ rm !$ # this will remove text.txt
	```

- `..` = go up one directory 
	- `../..` = go up two directories
- double-tab for list
- wild cards 
	- `\*` - infinite number of characters
	- `?` - single character

### Tab completion
*When typing file paths, it is both faster and more accurate to use tab completion. Start typing a path and then press tab. If you have a unique character at the end of your typing the item will be completed. If it is a file, the file will be completed including extension. If it is a directory, it will be completed through the `/`.*

*If you have several folders or files in the current directory with similar names, double-tap the tab key to view a list of files that begin with the characters you have typed.*

```bash
$ cd ~/Documents/a {tab-tab}
a.txt	ab.txt	abc.txt
```


### Keyboard Shortcuts

- ***up & down arrows*** = scroll through your command history
- ***ctrl+C*** = cancel a command
- ***ctrl+A*** = move cursor to beginning of line
- ***ctrl+E*** = move cursor to end of line
- ***opt+arrow key*** = move cursor forward or backwards a word
- ***ctrl+U*** = delete from cursor to beginning
- ***ctrl+K*** = delete from cursor to end
- ***ctrl-W*** = Delete 1 Previous Word
- ***ctrl-L*** = Clear Screen
- ***ctrl+R*** = search command history
	- begin typing and suggestions are made
	- Craig Hockenberry suggests the following `bind` commands addied to your `.profile` to give you a better history experience. `"\e[A"` is the escaped binding for up-arrow. when you add this, you could type `ssh` then up-arrow to cycle through all previous `ssh` commands.

	```bash
	bind '"\e[A":history-search-backward'
	bind '"\e[B":history-search-forward'
	```


## Bash Commands


### pwd
*Print working directory. This returns the path to the folder you are in.*

```bash
$ pwd
/Users/me
```


### clear
*Pushes command line up to top of screen, giving you a clean slate in your terminal window.*


### touch
*Create an empty document*

```bash
touch /path/to/file.txt
```

*Touch can also be used to update file modify date on an existing file.*


### cp 
*Copy a file to a new location. Requires two arguments; file path and path to new location. Destination does not require file name, just directory.*

```bash
cp /path/to/file.txt /path/to/copy/file.txt
```

### mv
*Move a file to a new location. Requires two arguments; file path and path to new location. `mv` can be dangerous. If anything goes wrong such as a power loss or an error during transfer, your file is toast.*

```bash
mv /path/to/file.txt /path/to/copy/file.txt
```


### ls

*list contents of directory*

#### Ordered  list

```bash
$ ls -l
drwxr-xr-x   8 user  staff   272 Oct  9 10:59 profiles
drwxr-xr-x  14 user  staff   476 Nov 20 13:43 src
```

#### Show invisible files

```bash
$ ls -lA
-rw-r--r--@ 1 user  staff      12292 Aug 11 11:36 .DS_Store
-rw-r--r--  1 user  staff          0 Sep  1  2012 .localized
drwxr-xr-x  8 user  staff        272 Jul 31 15:00 Recordings
```

#### Write a directory list to a file

*The following will write out all files in a directory including all files in all subdirectories.*

	ls -R > ~/Desktop/file-list.txt
	
#### Other operators
- `-e`: show ACLs
- `-@`: show extended attributes

### lsof
*List of running processes.*

This has one very useful function: find a process using an external drive. This comes in handy when you cannot eject a disk because it "is in use by another application". Use the following to identify the process then use `kill` to knock it out.

```bash
$ lsof | grep /Volumes/Data
Microsoft Word
```


### top 
- show running processes
- `-o` (order), use with cpu or rsize 


### kill
- with PID (Process ID)
- add `-9` to force

#### Find a PID and kill an app

```bash
$ ps ax | grep -i {APPNAME} | grep -v grep
$ kill -HUP {PID}
```

	
### killall 
*Kill an app with it's process name. Make sure to use quotes on the name.*

```bash
sudo killall "Mail"
```

### open 
#### Open apps 
	
```bash
open /System/Library/CoreServices/Applications/Network\ Utility.app
```

#### Open a document

```bash
open -e /path/to/file.txt
```

	
### opendiff
- Use **FileMerge.app*** to graphically compare or merge file or directories.
- Once open in **FileMerge.app***, you can save a merged version

```bash
opendiff modified.txt original.txt
```
	

### ln
- create hard links
- Use `-s` for symbolic links

```bash
ln -s /System/Library/CoreServices/Applications/Network\ Utility.app \  
/Applications/Utilities/Network\ Utility.app
```


### softwareupdate

- `--CatalogURL` let's you specify a catalog file
- `softwareupdate -l --CatalogURL <URL>` to list available updates from a specific catalog
- `-i -a` to install all updates
- `-i <name>` to install specific updates
- *Reboot manually when done*

##### Turn off software update checks

```bash
sudo softwareupdate --schedule off 
```


### tmutil
*Make changes to Time Machine settings*

##### Turn off Time Machine 

```bash
sudo tmutil disable
```

### netstat 
- *show network status*
- -r = show routing tables
- -n = show network addresses


### df
- *display free disk space*
- `-H` "Human-readable" output. Using base 10 for sizes. 
- `-h` "Human-readable" output. Using base 2 for sizes. 
- `-h` - help: have syntax help pop-up


### ssh
- Secure Shell
- log into the command line on a remote computer
- Use the format "USER@ADDRESS"
- `-p` allows using an alternate port

```bash
ssh -p 222 gadmin@192.168.1.1
```

When you approve ssh to systems, the get saved into a file at ~/.ssh/known_hosts. When using DHCP without assignments, you can run into conflicts. Use the following command to clear out the entries and get a fresh start.

```bash
ssh-keygen -R http://ip.address.here
```

Source: [Rich Trouton](https://twitter.com/rtrouton/status/543120764816609280)


### pmset

- *Power Management System*
- `-b` = change battery settings
- `-c` = change charger settings
- `-u` = change UPS settings
- `-a` = change all
- [man page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/pmset.1.html)

```bash
pmset -c sleep 0 #Sets sleep on AC power to OFF
```

## Search

- `which` = find the location of a command in your $PATH
- `find` -- *search* -name [-iname for non-case-sensitive search]
- `locate` -- *uses DB for search*, only updated ~ once a week [-i for case insensitive]
	- update the DB: `/usr/libexec/locate.updatedb` 
	- only indexes user-owned files
		- run with `sudo` to index everything, lasts through next index


## User Changes

### Get Current User

```bash
/usr/bin/who | /usr/bin/awk '/console/ { print $1 }'
```
  
From [Lauren](http://laurendc.net/) via [Twitter](https://twitter.com/laurendc/status/498559126977654785)


### Remove a user from the `admin` group.

	/usr/sbin/dseditgroup -o edit -d $USER -t user admin


From [Greg Neagle](http://managingosx.wordpress.com) via [this post](http://managingosx.wordpress.com/2010/01/14/add-a-user-to-the-admin-group-via-command-line-3-0/)


### Disable Automatic Login

```bash
#!/bin/bash
defaults delete /Library/Preferences \
com.apple.loginwindow autoLoginUser
rm /etc/kcpassword
```

From [Topher Kessler](http://www.macissues.com/author/tkesslermac-com/) via [this CNET article](http://www.cnet.com/news/how-to-disable-automatic-log-in-via-the-command-line-in-os-x/)


## Other Commands

### Logout all GUI users

	sudo pkill loginwindow

From [StackExchange](http://apple.stackexchange.com/questions/126761/way-to-logout-a-user-from-the-command-line-in-os-x-10-9)

### Replace text on files in a folder

	perl -pi -w -e 's/REPLACE_THIS/WITH_THIS/g;' *.txt
	
From [Lifehacker](http://lifehacker.com/5810026/quickly-find-and-replace-text-across-multiple-documents-via-the-command-line)

### Run a speedtest

	curl http://speedtest.wdc01.softlayer.com/downloads/test10.zip > /dev/null


### Get Current User

	/usr/bin/who | /usr/bin/awk '/console/ { print $1 }'

  
From [Lauren](http://laurendc.net/) via [Twitter](https://twitter.com/laurendc/status/498559126977654785)


### Check subfolders for git repos

```bash
for file in ./*; do if [[ -e "$file"/.git ]]; then echo "$file = True"; \
else echo "$file = False"; fi; done
```

From Rusty Myers via [Twitter](http://twitter.com/thespider/status/497934367520727040)




## Variables

- Apple Developer Portal [reference page](http://developer.apple.com/mac/library/documentation/DeveloperTools/Conceptual/SoftwareDistribution/Install_Operations/Install_Operations.html#//apple_ref/doc/uid/10000145i-CH14-SW1)
- Arguments
- $1: Full path to the installation package the Installer application is processing.
- $2: Full path to the installation destination.
- $3: Installation volume (or mountpoint) to receive the payload.
- $4: The root directory for the system.
- Environment variables
- $SCRIPT_NAME: Filename of the operation executable.
- $PACKAGE_PATH: Full path to the installation package. Same as $1.
- $INSTALLER_TEMP: Scratch directory used by Installer to place its temporary work files. Install operations may use this area for their temporary work, too, but must not overwrite any Installer files. The Installer application erases this directory at the end of the install.
- $RECEIPT_PATH: Full path to a temporary directory containing the operation executable. This is a subdirectory of $INSTALLER_TEMP. This location may vary between installs. The executable can use this path to locate other files in the package.


## Text Editors

### nano

Note! nano is a command line editor.

- **Save:** To save the current file, press ***Control-O*** (WriteOut).

- **Quit:** To quit nano, press ***Control-X*** (Exit). If you’ve made any changes to the document that you haven’t yet saved, nano prompts you to save the file before exiting. Press ***N*** to discard changes and quit immediately, ***C*** to cancel and stay in nano, or ***Y*** to save changes and exit. If you do save changes, nano verifies that you want to keep the existing file name (if you don’t, you can type a new one). Press Return after verifying the file name.

- **Find:** To find text within the file, press ***Control-W*** (Where Is). Type the text you’re searching for (case doesn’t matter) and press Return. The cursor jumps to the next spot in the document where that string appears. Repeat this procedure to do additional searches.

- Those commands alone should enable you to do almost everything you need to do in nano. 

- To learn about additional nano features and shortcuts, press ***Control-G*** to view its online help”

#### Open a document

	nano /path/to/file.txt



### vim
- **Find:** To find text within the file, press ***Control-W*** (Where Is). Type the text you’re searching for (case doesn’t matter) and press Return. The cursor jumps to the next spot in the document where that string appears. Repeat this procedure to do additional searches.

Note! vim is a command line editor.

- `vim` is an incredibly powerful text editor in the cli. It is modal, meaning there are "modes" that have different implications for the keyboard depending on what mode you are in. Unlike a word processor, `vim` works in a navigation mode by default. Striking the ***J***, ***K***, ***L***, and ***;*** keys will move the cursor left down, up, and right respectively. Striking ***I*** places you into *insert* mode, changing the keyboard mode to place text into the document like a typical editor. Striking the ***esc*** key exits you to the navigation mode.

#### Open a document

	vi /path/to/file.txt


### tail

Note! nano is a command line editor.

- *shows the end of a file*
- `-n` [*number of lines*] plus a value

	tail -n 10 /var/log/system.log


### TextEdit

#### Open a document

	open -e /path/to/file.txt


### TextWrangler

Attention: Triggering TextWrangler from the cli requires installing the [TextWrangler Command Line Tools](http://www.barebones.com/support/textwrangler/cmd-line-tools.html).

#### Open a document

	edit /path/to/file.txt


## Single-user Mode

Add a new admin account: rm /var/db/.AppleSetupDone

