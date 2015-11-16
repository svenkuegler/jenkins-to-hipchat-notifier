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

 2. Edit the script __notify-by-hipchat__ and add your Auth_Token and Room-ID.

 3. Add the following lines to your __commands.cfg__
 
 ```
 # 'notify-host-by-hipchat' command definition
define command{
        command_name    notify-host-by-hipchat
        command_line    /bin/echo "Notification Type: $NOTIFICATIONTYPE$\n\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | /home/ubuntu/notify-by-hipchat/notify-by-hipchat $HOSTSTATE$ "Host"
        }

 # 'notify-service-by-hipchat' command definition
 define command{
        command_name    notify-service-by-hipchat
        command_line    /bin/echo "Notification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$\n" | /home/ubuntu/notify-by-hipchat/notify-by-hipchat $SERVICESTATE$ "Service"
        }

 ```
 
 3. Add the HipChat Command to your __contact.cfg__.  
 For Example:
 
 ```
 define contact{
       name                            generic-contact
       service_notification_options    w,u,c,r,f,s
       host_notification_options       d,u,r,f,s
       service_notification_commands   notify-service-by-email,notify-service-by-hipchat
       host_notification_commands      notify-host-by-email,notify-host-by-hipchat
       register                        0
       service_notification_period     24x7
       host_notification_period        24x7
}
 ```
 
 


