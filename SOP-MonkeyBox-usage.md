# MonkeyBox Notes

## Work Flow

Before starting, sort configurations in to two categories; Device/User and Company. Device/User configurations will be linked to a device and include items such as User Account, Mozy, Daylite User, etc. Company configurations include Daylite and Billings Pro licenses, Corporate Apple ID, Web Hosting log ins, etc.

### Manual entry for Device/User

1. Create Contact
2. Create Device
	- Connect Contact during creation
3. Add Device password 
4. Add service accounts (Box, Mozy, etc.)


### Semi-automated Input

1. Create Client
2. Set up Watchman Monitoring integration using [this method](https://support.monkeybox.com/knowledgebase/articles/350844-watchman-monitoring-general-information).
3. Import Contacts using CSV import from **Contacts** tab.
4. After a Watchman sync, open a device and connect the user.
5. Add Device password.
6. Add service accounts (Box, Mozy, etc.).


### General Passwords and Notes

Company-wide software licenses (Daylite, Billings Pro) should be entered as **General Notes** from the **Notes and Files** tab.  Service passwords for Rackspace Archives, web hosting, etc. should be entered as **General Passwords** from the **Password** tab.  
Any item that has an expiration date should be entered from the **Services** tab. This would include Printer leases, Meraki Service Licenses, etc.


## Contacts

### Import via CSV

MonkeyBox supports importing via cdv file. The following is the template for upload. Be sure to use all columns and that all headers are typed *exactly* as shown. A template document can be downloaded from the MonkeyBox site.

| first_name | last_name | email | phone | notes |
|------------|-----------|-------|-------|-------|
| Jane       | Doe       | jane.doe@email.com | 555-555-1212 | `<p>Notes are in HTML format</p>` |


### Notes
> **Mobile Phone:** 216-555-1212
> **Position:** President  
> **Location:** Back Office 


## Devices

### Macs

#### Naming
{User first name, last initial} - {Company acronym} - {System type}

	Andrea D - OCS - MM02

Note: Device configurations should be automatically imported via **Watchman**.

#### Notes
> **Unique Software:** ScanSnap  
> **Unique Hardware:** USB3 hub/Ethernet Adapter, Label Printer


### Printers

#### Naming
Printer - {Make & Model}

	Printer - Sharp MX-3140N

*Network information must be completed for all network-connected printers.*


#### Notes

> **Service Vendor:**
> **Vendor Contact:**
> **Driver download:** 
> **Scanning:** (FTP, email)


### Modems

#### Naming
Modem - {Make & Model} - {Service Type}

	Modem - Netopia - DSL

#### Notes

> **Description:** Black box with 4 green lights


## Passwords

Add passwords for Applications and services that are installed on a device from its Device Record by clicking ***Add a password to this device*** in the **Device Passwords** box.

### User Account

#### Naming
User - {user name} - {type}

	User - Alex Lester - Standard


### Daylite

There are two Daylite configurations: Daylite User and Daylite Server. Daylite Server is handled in a Note.

#### Naming
Daylite User - {user name}

	Daylite User - Alex Lester


### Box

#### Naming
Box - {user name}

	Box - Alex Lester

#### Notes
> **Shared Folders:**
> **Sync Folders:**


### Mozy

#### Naming
Mozy - {user name}

	Mozy - Alex Lester

#### Notes
> **File Exceptions:**

Note: This one will rarely be used if we are doing our job.


### Rackspace

#### Naming
Email - {user name}

	Email - Alex Lester

If the user has more than one email domain, add the domain identity to the end of the name for secondary accounts.

	Email - Alex Lester - HDBusiness Law

### FileVault Key

Add this if FileVault is active and using a personal key. Place the key into the encrypted password field. Skip the user name field.

#### Naming
FileVault - {user name}

	FileVault - Jason Damicone


### Meraki Dashboard

*This should be connected to the Meraki Device configuration.*

#### Naming
Meraki Dashboard - {user}

	Meraki Dashboard - Stuart Horwitz

#### Notes
> **Network Name:**  


### Wireless Networks/SSIDs

*This should be connected to the Meraki Device configuration.*

#### Naming
Wireless Network - {SSID/Network Name}

	Wireless Network - THG Law
	
**User Name:** *populate this field with the SSID/Netwrok Name.*

	
#### Notes
> **Security Type:** 
> **Subnet:** *Use CIDR address.*


### Rackspace Archiving

Rackspace Archiving accounts should be set up and *General Passwords* in the password tab. They should not be associated with a device.

#### Naming
Rackspace Archiving - {Company Name}

	Rackspace Archiving - The Horwitz Group

#### Notes
> **Customer name:**  
> **Account #:**  
> **Domains:**  *Use bullets for multiple domains.*



## Notes and Files

### Software Licenses

Note: If you add software licenses for applications that are installed on a device from its Device Record by clicking ***Add a note to this device*** in the **Additional notes and files** box, a link will be created between the two.

#### Naming

#### Notes
> **License Key:**  
> **Installed system:**  
> **Product ID:**


### QuickBooks 

#### Naming
QuickBooks - {Company} - {type}

	QuickBooks - UHC - Enterprise v15

#### Notes
> **Licence Number:**
> **Product Number:**
> **Number of Users:**
> **Download Link:**
> **Support Site:**
> **Customer #:**


### Daylite Server 

#### Naming
App - Daylite Server - {Company Name}

	App - Daylite Server - The Horwitz Group


#### Notes
> **Database Name:**  
> **Public Address:**  
> **Local Address:**
> **Serial:**
> **License:**
> **Version:**
> **Registered to:**
> **Quantity:**


### Billings Pro Server 

#### Naming
App - Billings Pro Server - {Company Name}

	App - Billings Pro Server - The Horwitz Group


#### Notes

*Most Billings Pro installs* will not *use Switchboard and instead use the* Advanced setup *that includes Public and local addresses. Do not include the unused items in the note.*

> **Switchboard ID:**  
> **Switchboard Password:**   
> **Public Address:**  
> **Local Address:**
> **Serial:**
> **License:**
> **Version:**
> **Registered to:**
> **Quantity:**


### Rackspace

#### Naming

Rackspace - {Company Name}

	RingCentral - Horwitz

#### Notes

> **Admin Contact Info:**  
> **Phone Number:**  
> **Numeric Password:**  
> **Security Question:**  
> **Answer:** Cleveland  



## Services

Services are a special item like Devices; they can have passwords, notes and files attached.

1. Add a description using the naming convention {Service} - {Company}. If the service is associated with a specific user, include their name at the end, i.e. {Service} - {Company} - {User}.

Vendor Management forms: Create the Service, attach a File, add important info (support phone #) in note.


### Meraki Service Agreements

Note: Make sure to create a password configuration for the Dashboard account. From the Service Agreement, click on ***Add a service Provider password*** to add the login credentials.

> **Meraki Order #:**
> **Dashboard License Key:**
> **GMIT PO #:**
> **Ingram PO #:**
> **Agreements:** *Use bullets for multiple entries*
> **Serial #:**


### Domain Registrar

Create the Services configuration and save it, then enter the config and click on ***Add a service Provider password*** to add the login credentials.

#### Naming
{registrar} - Domain Registrar

	GoDaddy - Domain Registar

#### Notes
> **Account #:**  
> **Domains:**  Use bullets for multiple domains
> **Support #:**


## Other Configurations

You will find that most configuration cases fit logically into MonkeyBox's simple fields and a note box that can reasonably display the necessary custom needs. The question will arise as to whether to use a note or a password. Any custom item that has an associated user name/password combination should be created with a password item.


## Watchman Integration

- Create logical names that will match other services
- Once Group is in Watchman, create the link in MonkeyBox
- Watchman calls hardware systems "Clients" and MonkeyBox calls Company entries "Clients". Keep this in mind as your read through this.

1. Create the *Client* in MonkeyBox by clicking ***+ New client*** in the toolbar.
2. Add the client name and a description of the client's work.
3. Click ***Save***.
4. Click ***Manage*** *> Client* in the toolbar.
5. Click ***Edit*** next the the client name.
6. Click in the text box next to **Watchman Client Group**, which is actually a drop-down menu. Choose the company group in the drop-down menu.
7. Click ***Update Clients***.

If you want to grab all the clients from Watchman right away you can force a sync.

9. Click on the Watchman home button in the upper-left.
10. Choose the client from the client drop-down.
11. Click on ***Devices**.
12. In the right sidebar, locate the **Watchman Monitoring Sync Status* section and click ***Sync now***.
13. Enjoy a beverage.


## Document History

Created:	17 Sep 2014  
Author:		Tobias Morrison

Modified: 	05 Oct 2014  
By:		Tobias Morrison  
Changes: 	Added "Watchman Integration" section  
