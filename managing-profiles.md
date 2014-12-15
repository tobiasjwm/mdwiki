# Managing Profiles

NOTE: This is all mostly garbage, but I might finish it sometime.
## Using Server.app

### Set it up

Setting up Server app is well within your wheel house. Go do it. Better yet, do it in a VM. Set up Web Services and give it a cool domain name because it will be printed all over your Profiles.

1. Turn on the Profile Manager service.
2. Make sure that "Sign Profiles" is *uhchecked* so that we can make manual changes if we want.

### Built-in Settings

1. Find your settings
2. Make your changes
3. Save your file
4. Download the file
5. Give it a good name


### Custom Settings

Search Google for good settings. Looking into old MCX settings is a good way to go.

1. Edit the setting.
2. Turn off any other configured settings
3. Give it a good description under the **General** setting.
4. Scroll down to **Custom Settings** and click ***Configure***.
5. Click ***Add*** to add a field. Fill it out.
6. Save your file
7. Download the file
8. Give it a good name


#### Mangle the Menu Extras

You know those things that *EVERY* app is throwing icons into on the right side of the Menu Bar that are slowly taking over the place and leaving no room for *actual* menus. Take a look et the system items here:

	/System/Library/CoreServices/Menu\ Extras
	
Make a profile to remove the Time Machine icon from the Menu Bar. Here Greg Neagle shows us [where to find the settings](http://managingosx.wordpress.com/2008/02/12/timemachine-menu-extra-management/). Then you can look [at this](http://swytechnotes.wordpress.com/2013/11/05/time-machine-menubar-item-via-profiles/) to see how its done.


## Using Custom Plists

### Make a change, grab the plist

1. Make your change
2. Copy the Plist
3. Remove extraneous keys. (Better know what you are doing or you will have nothing to work with. Plists are easy to invalidate.)
4. Run it through `make-profile-pkg`


### But what if I don't know where the plist is?

That is what [fseventer](http://www.fernlightning.com/doku.php?id=software:fseventer:start) is for.


### What the hell changed in this plist?

Use FileMerge 

	opendiff /path/to/file1.plist /path/to/file2.plist
	
#### OMG! The files won't open!

You need to make FileMerge convert the binary plists.

	defaults write com.apple.FileMerge Filters -array-add \
	'{ Apply = 0; Display = 0; Extension = plist; Filter = \
	"/usr/bin/plutil -convert xml1 -o -  \$(FILE)"; }'

Sourced from [Jason Harris](http://jasonfharris.com/blog/2010/04/make-filemerge-diff-plist-files/).