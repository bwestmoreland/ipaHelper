ipaHelper
==========

### NAME ###

**ipaHelper** -- script to help with examining and resigning ipa files

### SYNOPSIS ###

**ipaHelper get \[** *mobileprovision files...*  **\]**  
**ipaHelper certs \[** *substring* **\]**  
**ipaHelper profile \[** *ipa or mobileprovision file* **\] \[** *options* **\]**  
**ipaHelper info \[** *ipa or Info.plist file* **\] \[** *options* **\]**  
**ipaHelper summary \[** *ipa file* **\]**  
**ipaHelper verify \[** *ipa file* **\]**  
**ipaHelper resign \[** *ipa file* **\] \[** *options* **\]**  
**ipaHelper account \[** *options* **\]**  
**ipaHelper upload \[** *ipa file* **\]**  
**ipaHelper help \[** *-v* **\] \[** *commands* **\]**

### DESCRIPTION ###
       
#### GET ####

**ipaHelper get \[** *mobileprovision files...*  **\]**

Moves *mobileprovision files* into the working directory.
If no profiles are specified, all .mobileprovision files in the Downloads folder are moved.

#### CERTS ####

**ipaHelper certs \[** *substring* **\]**

Displays information on all certificates in the keychain.
If *substring* is provided, only certificates containing this *substring* are displayed.

#### PROFILE ####

**ipaHelper profile \[** *ipa or mobileprovision file* **\] \[** *options* **\]**

Checks the profile of *ipa file*, or shows the information about *mobileprovision file*
If no *mobileprovision* or *ipa file* is provided, the first (alphabetically) ipa file in the working directory is used. If no options are present, a summary of the provisioning profile is displayed.

**Profile Options**

**-v, --verbose**  
display the entire profile in xml format

**-e, --entitlements**  
display the entitlements on the profile

**-k** *key* **, --key** *key*  
return the value for *key* in the profile

**-l, --list**  
list all keys in the profile

**-i, --id**  
display the application identifier

**-c, --certificate**  
display the certificate name

**-t, --team**  
display the team name on the certificate

**-x, --expiration**  
display the expiration date for the profile

#### INFO ####

**ipaHelper info \[** *ipa or Info.plist file* **\] \[** *-E* **\] \[** *options* **\]**

Checks the Info.plist of *ipa file*, or shows the information about *Info.plist file*
If no *Info.plist* or *ipa file* is provided, the first (alphabetically) ipa file in the working directory is used.
If no options are present, a summary of the Info.plist is displayed.

**Info Options:**

**-E, --edit**  
edit the Info.plist in vim

**-v, --verbose**  
display the entire Info.plist in xml format

**-k** *key* **, --key** *key*  
return the value for *key* in the Info.plist

**-l, --list**  
list all keys in the Info.plist

**-i, --identifier**  
display the CFBundleIdentifier

#### SUMMARY ####

**ipaHelper summary \[** *ipa file* **\]**

Displays profile and info.plist information about *ipa file*.
If no ipa file is provided the first (alphabetically) ipa file in the working directory is used.

#### VERIFY ####

**ipaHelper verify \[** *ipa file* **\]**

Checks to make sure the necessary code signing components are in place for *ipa file*.
If no ipa file is provided the first (alphabetically) ipa file in the working directory is used.

#### RESIGN ####

**ipaHelper resign \[** *ipa file* **\] \[** *options* **\]**

Removes  the  code  signature from *ipa file*, and replaces it either with the first profile (alphabetically) in the directory with *ipa file* or a specified profile.
Resigns *ipa file* using the certificate on the profile and entitlements matching the profile, zips the resigned ipa file with the output filename.  If no output filename is provided, \[*ipa filename*\]-resigned.ipa is used.
If no *ipa file* is provided, the first (alphabetically) ipa file in the working directory is used.

**Resign Options:**

**-p profile , --profile profile**  
use profile for resigning the ipa

**-o** *filename* **, --output** *filename*  
resign the ipa file as *filename* instead of \[*ipa filename*\]-resigned.ipa

**-d, --double-check**  
display information about the ipa, its Info.plist, and the provisioning profile and have be given an option to continue with the resign or quit

#### ACCOUNT ####

**ipaHelper account \[** *options* **\]**

Displays information about which certificates are linked with which iTunesConnect accounts.

**Account Options:**

**-g** *certificate* **, --get** *certificate*  
returns the iTunesConnect account linked to *certificate*

**-s** *certificate account* **, --set** *certificate account*  
Links *certificate* to the iTunesConnect *account*

**-r** *certificate* **, --remove** *certificate*  
Removes the link between *certificate* and its iTunesConnect account

#### UPLOAD ####

**ipaHelper upload \[** *ipa file* **\]**

Uploads *ipa file* to iTunesConnect.  Asks for an iTunesConnect username if none is linked to the ipas certificate. Asks for a password for this account.  If no *ipa file* is provided, the first (alphabetically) ipa file in the working directory is used.

#### HELP ####

**ipaHelper help \[** -v **\] \[** *commands...*  **\]**

Displays usage information for the commands.

If *-v* option is present it shows the usage information for all of the commands.

### AUTHOR ###

Marcus Smith
