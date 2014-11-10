# Git

## Install and Update to latest version Git on Mac OSX 10.9 Mavericks


Install Git on OSX 10.9 Mavericks by getting the latest version from the **[Git home page][2] **or from the direct [OSX latest link][3].

This will download the latest version of Git to your desktop/download area as a **dmg** file.

Open the dmg file,  then **Control/Right** Click the **git.pkg** file to install.

When Git is installed check in the Terminal, launch the **Terminal** from /Applications/Utilities and check the version:

    git --version

And the version is displayed

    git version 2.0.1

To see where it is located

    which git

And the location is shown

    /usr/local/git/bin/git

## Upgrading Git from a previous version to the latest 2.0.1

If you have previously installed Git you can upgrade to the latest version by uninstalling the previous install using the **uninstall.sh** file with the installation.

Go through the same process of downloading and mounting and the **.dmg**  - then launch the Terminal.

Then just drag and drop the **uninstall.sh** file on a Terminal window and hit **enter,** follow the prompts and **then** install the lastest version of Git by opening and installing the Git package. Your previous Git configuration settings and working repositories **remain** intact.

## Upgrading Git in Xcode

If you have Xcode already installed and have installed **command line** tools then you alreay have Git, probably an older version which is distributed with Xcode this is installed in:

    /usr/local/bin

To run the lastest version which by following the initial instructions is filed here:

    /usr/local/git/bin/git

You need to [add this latter path to your **shell path **][7]to take precedence over the other path, the path will be set in either **.bashrc** or **.bash_profile** in your home directory.

So add in


    /usr/local/git/bin

to the path similar to the below:


    export PATH="/usr/local/git/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:$PATH"

Restart or reload the Terminal and the newer Git version will now be used.

## Using Git

```
/* Set up Git Configuration */

git config \--global user.email "neil@coolestguidesontheplanet.com"

git config \--global user.name "Neil Gee"

git config \--global core.editor "vi"

git config \--global color.ui true

/* See Git configuration */

git config \--list

/* to initialise a local repository */

git init

/* adds a file to the repo */

git add

/* commit the change to git */

git commit -m "Message goes here"

/* see the commits */

git log

/* Git has a 3 Tier Architecture: Working - Staging Index - Respository

Changes to files are put in a Checksum SHA-1 hash 40digit value containing parent hash, author and message.

HEAD is the latest commit of the checked out branch */

/* Basic Commands */

git status /* the command 'git status' tells which files are not added or committed from Working to Staging to Repository */

git commit -m "" /* Commits and changes to all files that are in Staging Tier into Repository */

git diff /* show changes between Working and Repository, no file supplied shows all files */

git diff \--staged /* shows changes between Staged and Respository */

git rm file.txt /* will remove file from working then git commit -m "" to move to Repo */

git mv /* rename or move files - then git commit -m "" to move to Repo */
 
git commit -am "text goes here" /* adds all files straight to Repo from Staging if they have changes - meaning they skip git add */

git checkout \-- file.txt /* restore Repo file to Working Directory using current branch */

git reset HEAD file.txt /* Move a Stage file out of Stage back to Working */

git commit \--amend -m "message" file.txt /* Change last commit to Repo (only last one can change) */

/* Reverting --soft --mixed --hard */

git log /* gets the sha1s so you can see the coomits where you want to back to */

git reset \--soft sha /* changes Repo but not STaging or Working */

git reset \--mixed sha /* changes Repo and STaging but not Working */

git reset \--hard sha /* changes all 3 Tiers */

git clean -f /* remove untracked files from Working */

.gitignore /* ignores files to track in Working / track the .gitignore file */

Global Ignore /* create in home folder */

.gitignore_global

/* Add in */

.DS_Store

.Trashes

.Spotlight_V100

git config \--global core.excludesfile ~/.gitignore_global /* add to gitconfig */

/* Stop tracking changes */

rm \--cached file.txt /* leaves copy in Repo and Working */

 
/* Track Folders changes

Add an invisble file to a folder like .gitkeeper then add and commit */

/* Commit Log */

git ls-tree HEAD

git ls-tree master

git log \--oneline

git log \--author="Neil"

git log \--grep="temp"

/* Show Commits */

git show dc094cb /* show SHA1 */

/* Compare Commits

Branches */

git branch /* Show local branches * is the one we are on */

git branch -r /* Shows remote branches */

git branch -a /* Shows local and remote */

git branch newbranch /* creates a new branch */

git checkout newbranch /* switch to new branch */

git checkout -b oldbranch /* creates and switches to new branch */

/* Diff in Branches */

git diff master..otherbranch /* shows diff */

git diff \--color-words master..otherbranch /* shows diff in color */

git branch \--merged /* shows any merged branches */

/* Rename Branch */

git branch -m oldname newname

/* Delete Branch */

git branch -d nameofbranch

/* Merge Branch */

git merge branchname /* be on the receiver branch */

/* Merge Conflicts between the same file on 2 branches are marked in HEAD and other branch */

git merge \--abort /* Abort basically cancels the merge */

/* Manually Fix Files and commit

The Stash */

git stash save "text message here"

git stash list /* shows whats in stash */

git stash show -p stash@{0} /* Show the diff in the stash */

git stash pop stash@{0} /* restores the stash deletes the tash */

git stash apply stash@{0} /* restores the stash and keeps the stash */

git stash clear /* removes all stash */

git stash drop stash@{0}

/* Remotes

You fetch from the remote server, merge any differences - then push any new to the remote - 3 branches work remote server branch, local origin master and local master

Create a repo in GitHub, then add that remote to your local repo */git remote add origin https://github.com/neilgee/genesischild.git /* origin can be named whatever followed by the remote */

git remote /* to show all remotes */

git remote remove origin /* to remove remote */

git remote rm origin /* to remove remote */

/* Push to Remote from Local */

git push -u origin master

/* Cloning a GitHub Repo - create and get the URL of a new repository from GitHub, then clone that to your local repo, example below uses local repo named 'nameoffolder' */

git clone https://github.com/neilgee/genesischild.git nameoffolder

/* Push to Remote from Local - more - since when we pushed the local to remote we used -u parameter then the remote branch is tracked to the local branch and we just need to use... */

git push

/* Fetch changes from a cloned Repo */

git fetch origin /* Pulls down latest committs to origin/master not origin, also pull down any branches pushed to Repo

Fetch before you work

Fetch before you pull

Fetch often */

/* Merge with origin/master */

git merge origin/master

/* git pull = git fetch + git merge

Checkout/Copy a remote branch to local */git branch branchname origin/branchname /* this will bring the remote branch to local and track with the remote */

/* Delete branch */

git branch -d branchname

/* Checkout and switch branch and track to remote */

git checkout -b nontracking origin/nontracking

/* Remove remote branch */

git push origin \--delete branch
```

[view raw][8] [git.css][9] hosted with ❤ by [GitHub][10]



[1]: http://coolestguidesontheplanet.com/install-update-latest-version-git-mac-osx-10-9-mavericks/#disqus_thread
[2]: http://git-scm.com/ "git home page"
[3]: http://git-scm.com/download/mac
[4]: http://coolestguidesontheplanet.com/wp-content/uploads/2014/03/osx-mavericks-git-2.png
[5]: http://coolestguidesontheplanet.com/wp-content/uploads/2014/03/osx-git-190-install.png
[6]: http://coolestguidesontheplanet.com/wp-content/uploads/2013/12/upgrading-git-osx.png
[7]: http://coolestguidesontheplanet.com/add-shell-path-osx/ "What it is and How to Modify the Shell Path in OSX 10.9 Mavericks using Terminal"
[8]: https://gist.github.com/neilgee/9442209/raw/git.css
[9]: https://gist.github.com/neilgee/9442209#file-git-css
[10]: https://github.com
[11]: http://coolestguidesontheplanet.com/wp-content/uploads/2014/05/nodejs-npm-120x120.jpg
[12]: http://coolestguidesontheplanet.com/installing-node-js-osx-10-9-mavericks/ "Installing node.js on OSX 10.9 Mavericks"
[13]: http://www.coolestguyplanettech.com/wp-content/plugins/yet-another-related-posts-plugin/default.png
[14]: http://coolestguidesontheplanet.com/install-and-configure-wget-on-os-x/ "Install and Configure wget on OS X Mavericks 10.9 and fix SSL GNUTLS error"
[15]: http://coolestguidesontheplanet.com/wp-content/uploads/2013/09/ruby.png
[16]: http://coolestguidesontheplanet.com/upgrading-ruby-osx/ "Upgrading to Ruby 2 on OSX 10.8 Mountain Lion"
[17]: http://coolestguidesontheplanet.com/wp-content/uploads/2013/12/home-brew-osx-lion-package-manager.png
[18]: http://coolestguidesontheplanet.com/setting-up-os-x-mavericks-and-homebrew/ "Installing Homebrew on OS X Mavericks 10.9, Package Manager for Unix Apps"
[19]: http://coolestguidesontheplanet.com/install-mcrypt-php-mac-osx-10-9-mavericks-development-server/ "How to Install mcrypt for php on Mac OSX 10.9 Mavericks for a Development Server"
[20]: http://coolestguidesontheplanet.com/category/osx/ "View all posts in OS X"
[21]: http://coolestguidesontheplanet.com/category/web-dev/ "View all posts in WebDev"
  