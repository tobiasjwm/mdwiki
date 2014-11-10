# XKPasswd

## Install

*Requires that `git` is installed on target system.*

```bash
cd /usr/local/
sudo git clone https://github.com/bbusschots/xkpasswd.pm.git
```

## Update

```bash
cd /usr/local/xkpasswd.pm
sudo git fetch
```


## Usage

### Commands

Note: These commands all assume XKPasswd was installed in `/usr/local/xkpasswd.pm/`, if you install it elsewhere, update the path within the commands.

To see a list of defined presets use:

    perl -e 'use lib "/usr/local/xkpasswd.pm/";use XKPasswd; \
	print join ", ", XKPasswd->defined_presets(); print"\n";'

To see the details of a preset use a command of the form (replacing `WEB32` with which ever preset you want to view):

    perl -e 'use lib "/usr/local/xkpasswd.pm/";use XKPasswd; my $xkpasswd = \
	XKPasswd->new("/usr/local/xkpasswd.pm/sample_dict.txt", "WEB32"); \
	print $xkpasswd->status();'

To generate a password using a preset you can use a command of the form (replacing `WEB32` with which ever preset you want to view):

    perl -e 'use lib "/usr/local/xkpasswd.pm/";use XKPasswd; \
	print xkpasswd("/usr/local/xkpasswd.pm/sample_dict.txt", "WEB32")."\n";'
	

### Create a Password Generation Script

Note: `xkpasswd.pm` is a perl module. Scripts are written in perl. Don't forget to call perl in the she-bang `#!/usr/bin/perl`.

1. Open **TextWrangler.app** and enter the following:

```perl
#!/usr/bin/perl
use lib '/usr/local/xkpasswd.pm/';
use XKPasswd;
my $password_generator = XKPasswd->new('/usr/local/xkpasswd.pm/sample_dict.txt', 'APPLEID');
print $password_generator->password()."\n";
```

2. Save this with the name `xkpasswd.pl`
3. Open `Terminal.app` and make it executable:

```bash
$ cd /path/to/directory
$ chmod 755 xkpasswd.pl
```

Want to see what is under the hood? Add the following line on line 5:

	print $password_generator->status()."\n";

This will present you with the recipe that was used to generate the password. This is great for testing new overrides.


#### Check your work

See if your overrides are making good passwords. Microsoft has a [password check website](https://www.microsoft.com/en-gb/security/pc-security/password-checker.aspx)

## Create an Automator Service

1. Open **Automator.app**.
2. Choose **Service**.
3. In the Services section, set the *Service Receives* drop down to **no input** and leave the *in* drop down as **any application**.
4. Add the *Run Shell Script* action to the Workflow area.
5. Change the *Shell:* drop down to **/usr/bin/perl**.
6. Paste your override script into this area.
*Do not include the she-bang or any comments in your script in the Automator action.*
7. Add *Copy to Clipboard* action to the Workflow area.
8. Save the Service with a logical name.

The service is saved in `~/Library/Services/foo.workflow`


## GMIT Usage


### GMIT Password Overrides

- Box requires 8 characters and 2 numbers
- User system passwords must be under 16 characters to meet the ConnectWise limit

#### MozyPro Override

```bash
#!/usr/bin/perl

# This xkpasswd override uses the APPLEID preset to generate a password 
# with two padding characters, two numbers, three words with seperators.

use lib '/usr/local/xkpasswd.pm/';
use XKPasswd;
my $config_overrides = {
	num_words => 3,
	padding_characters_after => 1,
	padding_characters_before => 1,
	padding_digits_after => 1,
	padding_digits_before => 1,
	case_transform => 'ALTERNATE',
	word_length_max => 5,
	word_length_min => 4,
};
my $password_generator = XKPasswd->new('/usr/local/xkpasswd.pm/sample_dict.txt', 'APPLEID', $config_overrides);
# print $password_generator->status()."\n"; # uncomment for testing in the command line
print $password_generator->password()."\n";
```

#### User Passwords 

```bash
#!/usr/bin/perl

# This xkpasswd override uses the XKCD preset to generate a password 
# with 3 words, alternating case, no separators and 15 characters.

use lib '/usr/local/xkpasswd.pm/';
use XKPasswd;
my $config_overrides = {
	case_transform => 'ALTERNATE',
	num_words => 3,
	word_length_max => 5,
	word_length_min => 5,
	separator_character => 'NONE',
};
my $password_generator = XKPasswd->new('/usr/local/xkpasswd.pm/sample_dict.txt', 'XKCD', $config_overrides);
# print $password_generator->status()."\n"; # uncomment for testing in the command line
print $password_generator->password()."\n";
```


## Resources

[GitHub Repo](https://github.com/bbusschots/xkpasswd.pm)

[Beginner's Guide](https://www.bartbusschots.ie/s/2014/08/16/xkpassws-2-absolute-beginners-guide/)

[Create an Automator Service](https://www.bartbusschots.ie/s/2014/08/16/xkpasswd-2-service-with-automator/)