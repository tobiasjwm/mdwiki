# Using mcxToProfile 



## Install mcxToProfile

```bash
$ mkdir profiles
$ cd ./profiles
$ git clone https://github.com/timsutton/mcxToProfile.git
```


## Create profile

```bash
$ cd ~/profiles/mcxToProfile/
$ ./mcxToProfile.py --plist /path/to/plist -r --identifier SoftwareUpdateOff --manage Often
```


## Options

### Required Options

mcxToProfile requires both the `--plist` and `--identifier` options.


### Once/Often/Always management

Although the GUI apps for generating .mobileconfig files do not accommodate the MCX functions to give you the option of allowing the profile to make a change that later allows a user to make their own modifications, mcxToProfile adds this by adding the appropriate MCX keys during creation. Add the `--manage` option with the key you want.


### Other

Attention! It is important to always include the `-r` option in our profiles. If we hand off a client, we want their new provider to be able to remove these if they want.

- A profile can be made "Always removable" using `--removal-allowed` or `-r` (default is "Never removable")
- An organization name for the profile can be specified using `--organization` or `-g`
- A specific output filename for the .mobileconfig file can be specified using `--output` or `-o`


## Updating

If you attempt to install a profile with the same identifier, it will update the existing profile instead of installing another profile.

When creating an updated version of a profile, if you would like to simply replace the existing profile on a system, you need to be sure that you use the same identifier. The best way to do this is to use the `--identifier-from-profile` argument to guarantee a consistent identifier and UUID.


## Resources

[mcxToProfile GitHub page](https://github.com/timsutton/mcxToProfile)

[Krypted article](http://krypted.com/mac-security/manage-profiles-from-the-command-line-in-os-x-10-9/) on using `profiles` commands.


### Document History

Created:	09 Sep 2014  
Author:		Tobias Morrison

Modified:	22 Sep 2014
Author:		Tobias Morrison
Changes:	Added most of the useful info in the document.