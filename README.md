pkexecMan V1.0 (9/Aug/2020) bash script

 Script written by Bruce Steers https://github.com/BruceSteers

What is it? 
A text based bash script for linux systems that use the new policy-kit for 
running gui applications as root from a non terminal environment. 
Ie. from a menu or a desktop launcher. 
If you have used GKSU in the past before it disappeared and pkexec became the alternative 
but don't know how to configure pkexec then you will want this script.

with GKSU you could just set a launchers command to gksu /path/appname and 
the app would launch fine as root after asking you for your password. 
pkexec on the other hand is a bit more complicated as you have to set up a 
policy file for pkexec and add allowed apps to it before it will work.

That's where this app comes in. 
Once an app has been added, for example '/user/bin/pluma' (the default MATE text editor)
You can then create a desktop launcher or menu item setting the command as...
pkexec pluma %U
Then a password requester will open before the app and elevate to SuperUser mode.

Features. -- 
Creates a new pkexec policy file if one does not exist or will load your existing one if you have one.

With no arguments it uses Zenity to be a complete manager for your pkexec allowed apps list.
Provides a list of existing entries.
From there you can add new items, delete existing items, edit description/message fields.

Can be used non interactively via terminal or another script of your own using arguments 
so you could include the script in your own package and use it to configure your own app.


 pkexecMan
 Launch with no args to use zenity dialogs to manage all pkexec run actions.
 main commands <list|add|delete=name>

pkexecMan add , auto add command, zenity will ask for any non-filled fields unless -noz argument given
 then dafaults will be used (-p path must be supplied if -noz used)

pkexecMan list , lists actions by name

pkexecMan del="name" , deletes rule of given name

-q , quiet. suppresses terminal messages except warnings.
-l , same as list
-a , same as add
-del=name , same as delete=name

Additional parameters for 'add' command.. 

 -p="/full path/to file", supply full path to exe to add
 
 -d="Description field", default is <filename> application file

 -m="Message field", message given when asked for password, default is
 <filename> requires SuperUser access
 
 -noz , suppress non critical Zenity requesters asking for non filled in fields
 uses defaults for description and message but -p path must be given.
 
 Eg.
pkexecMan -a :use zenity requesters to fill in all fields, add the selected command and exit
pkexecMan -a -q -noz -p="/usr/bin/pluma" :auto add pluma to list silently using defaults and exit
pkexecMan :show the manager, lists all actions with modify, add or delete options"

