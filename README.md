Notify by HipChat
=====
Send your Nagios notices to HipChat Room

## Configure HipChat
 1. Login to www.hipchat.com with a Admin Account.
 2. Add an Integration
 3. Copy your Room-ID and Auth_Token

## Configure Nagios

 1. Install the Script.

 ```
 $ cd ~
 $ git clone https://github.com/svenkuegler/notify-by-hipchat.git
 ```

 _Notice! This is only an Example. You allready can upload the script to any other Location._

 2. Edit the script __notify-by-hipchat__ and add your API-Key.

 3. Add the following lines to your __commands.cfg__
 
 ```
 ...
 ```
 
 3. Add the HipChat notification to your __contact.cfg__
 
 ```
 ...
 ```
 
 


