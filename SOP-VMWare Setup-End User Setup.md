# SOP - VMWare Fusion 

## End-User Virtual Machine Setup 


### Purpose

This document outlines the steps needed when deploying VMware and Windows for an end user


### Scope



### Procedure Description

#### On the GM Cloud Mini Server
1. Create a folder for the company if it does not exist in `/Users/gadmin/BTSync/{company}`.
2. **COPY** the `/Users/gadmin/Documents/Virtual Machines/Windows 7 x64_base image` to the company folder by *option-clicking* the file and dragging it to the company's folder.
	- Rename the file by replacing "base image" with Company name
	- This can be also be done in the Terminal:

	```bash
	cp /Users/gadmin/Documents/Virtual\ Machines.localized/Windows\ 7\ x64_base\ image.vmwarevm \
	/Users/gadmin/BTSync/{company}/Windows\ 7\ x64_{company}.vmwarevm
	```

3. Open **VMware Fusion** *Do not open the file from the Finder.*
	- Go to ***Window*** *> Virtual Machine Library*.
	- Drag-n-drop the new file to the left Sidebar of the Virtual Machine Library window.
	- Right-click on the file and choose *Get Info* from the pop-over window.
	- Change the name to match the name you gave to the vm file. i.e. "Windows 7 x64_FEIC"
4. Startup the machine and choose ***I copied it*** when prompted.

#### In the Virtual Machine

##### Create the new user
1. ***Start*** *> Control panel > User Accounts > Add or remove accounts*.
2. Click on *Create a new account*
	- Account Name: User's full name
	- Standard User

##### Add a password for the user
1. Select the user
2. Click on *Create a password*
3. Add a password. This should be the same as the users Mac password but it *should not* contain any special characters.
	- Always remember to add "Call GlobalMac IT" for the password hint.

##### Change computer description and name
1. ***Start*** *> Computer > Right-click and choose Properties*
2. Click *Change Settings*.
3. Computer Description: 
      - Format: "Company shortname" – 'Full Name' VM"
      - Ex: **DSI-Howard Wolfe VM**
4. Computer Name:
	- Click on ***Change…***, next to "To rename this computer…"
	- Change *Computer Name:* "Company shortname-'User first and last initials'-VM"
	- ex: DSI-HW-VM
	- Click ***OK***
	- Dismiss restart message
	- Click on ***Apply***
	- Click ***Restart Later***
5. Create or update the Virtual Machine configuration in CW.

Attention: This is a good time to run Windows upgrades.

##### Activate Windows

Note: depending on the purchasing cycle, this step may need to be completed after the VM is installed on the client machine.

1. Go to the bottom of the open System window and click on "Activate Now"
2. Choose "Activate Windows online now"
3. Enter the Product Key
	- Cut and paste it from the user's config file in Connectwise
	- Click next to verify and activate
	- Once activated, restart the system

##### Configure performance modifications
1. Login to the new user account
2. Right-click on Desktop > Personalize
3. Choose *Windows Classic*
4. Click on ***Start*** > Right-Click on *Computer* and choose *Properties*.
5. Click on *Advanced System Settings* on the left hand side.
6. Click on ***Advanced*** *> Performance >* ***Settings…***
7. Choose *Adjust for best performance*
8. Click ***OK***
9. If needed, go to the "SOP – Vmware – {Client}" file to perform any additional mods needed by the client
10. Shut down the machine
11. Go to ***Virtual Machine*** > Settings… > General* and reclaim space by clicking ***Clean up Virtual Machine*** once more.
12. Once cleaned up, close the Settings and Virtual Machine windows.
13. Right-click on the Virtual Machine in the Virtual Machine Library window and choose *Delete*.
14. Click ***Keep File*** in the sheet.
15. Quit **VMWare Fusion**.

Note: We should create a wiki page that links to the client specific setups and link to that in step 9.

##### Transfer file to the user's computer from the GM Cloud Mini
1. Open **BitTorrent Sync** from Applications
2. Click on ***My Sync*** *> Add Folder* In the BTSync Toolbar.
3. Click on ***Generate*** to create a shared secret.
4. Copy the Shared Secret and paste it somewhere for safe keeping.
4. Click on ***Choose*** and navigate to the folder enclosing the VM.
5. Remote in to the client's computer that is getting Windows
6. Download and install BTSync from our RMM tool or [direct from BitTorrent](http://www.bittorrent.com/sync/download)
6. Open BitTorrent Sync
7. In the ** BitTorrent Sync** window, click on the Action Menu in the upper-right and choose "Enter a key".
8. Paste the secret and click Next
9. On the next window, click ***Choose***, then navigate to the Shared folder and create a folder titled "Virtual Machines".
10. Click on ***Select Folder to Sync***.

Hint: Leave the user logged in. It will take some time to download the file.

#### After transfer is complete

##### Disable BitTorrent Sync

1. Log into the client computer and verify transfer is complete.
2. Mouse over the folder in the BitTorrent Sync window and choose the menu button on the right.
3. Choose *Disconnect*.
4. Quit BitTorrent Sync.
5. Go to ***System Preferences*** *> Users & Groups > Login Items* and remove BitTorrent Sync if it is there.

##### Remove the Sync Folder on the Server

1. Connect to the GlobalMac IT Cloud Mini
2. Launch BitTorrent Sync
3. Click on Folders
4. Choose the folder that had been synced, click on it, then click on the "-" at the bottom left top disconnect it. 

#### Set up Virtual Machine on Client machine

1. Install VMware Fusion on the client computer via our RMM tool.
2. Launch VMWare Fusion on the client computer.
3. Enter serial to register VMware Fusion.

Warning! Depending on how carefully you followed this process, permissions may not be correct on the Virtual Machine after transfer. If you receive a warning that you cannot open the VM, use the following process to fix permissions.

##### Change the VM's permissions for the new user
1. Open **Terminal.app**.

	```bash
	$ su gadmin
	# enter the gadmin password when prompted
	$ cd /Users/Shared/Virtual\ Machines/
	$ ls –la # This lists files in the directory.
	$ sudo chown –R [USER]:wheel [NAME OF FILE]
	```

Note: Everything below this line needs further review and cleanup.

  6. Open VMware . File > Open and select the VM machine in the Shared folder.
  7. Click on Settings in VM BEFORE opening the Vm
    1. General > Start automatically when VMware Fusion Starts
    2. Sharing > Add the users root folder and any other specific, commonly used folders (Box, Dropbox, etc)
    3. Processors and Memory
      1. Processors > set to half the processors
      2. RAM > set to 2GB minimum, up to half of available RAM, depending on needs of the user.

    4. Startup the machine > Upgrade if prompted (if the base image was created on an earlier version of VMware)
    5. Choose "I copied it" if prompted.
    6. Once booted, shut down the machine, quit VMware Fusion and LOGOUT of the admin account then close ARD.

  8. Printer setup
    1. Add details here as needed

  9. Contact the end user for training
    1. Add Vmware Fusion to the dock
    2. Open the file the initial time and set to automatically open (just in case this setting is user specific)
    3. Show them how it works and how to use it.





1. Client Education Points
  1. Only work in VM on the applications you need to use.
  2. Do NOT use for email or web browsing beyond the apps you have to access in Internet Explorer. 


### REFERENCES

Attention: Add some references!

### Document History

Created: 	25 Apr 2014  
Author: 	Tom Lambotte  

Modified:	16 Sep 2014  
By:		Tobias Morrison  
Changes:	Formatted as Markdown document. Reviewed process and made changes to BitTorrent Sync processes as interface was recently overhauled.

