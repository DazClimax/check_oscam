# check_oscam

Icinga / Nagios Plugin for checking Entitlement of an paytv subscription on a running oscam server.

  - check entitlement
  - select reader
  - select subscription

This text you see here is *actually* written in Markdown! To get a feel for Markdown's syntax, type some text into the left window and watch the results in the right.

### Version
1.0

### Installation

Copy to your plugin folder

```sh
$ git clone https://github.com/DazClimax/check_oscam.git
```

### Define plugin in icinga

```sh
object CheckCommand "oscam" {
           import "plugin-check-command"

           command = [ PluginDir + "/check_oscam" ]

           arguments = {
                   "-H" = "$oscam_hostname$"
                   "-u" = "$oscam_user$"
                   "-p" = "$oscam_password$"
                   "-r" = "$oscam_reader$"
                   "-i" = "$oscam_subscription$"
                   "-w" = "$oscam_warningtime$"
                   "-c" = "$oscam_criticaltime$"
           }

           vars.oscam_hostname = "$address$"
}
```

### Use plugin

```sh
object Service "Entitlement NAME" {
         import "generic-service"
         host_name = "OSCAM"
         check_command = "oscam"
         vars.sla = "24x7"
 
          vars += {
         oscam_user = "USERNAME"
         oscam_password = "PASSWORD"
         oscam_reader = "READERNAME"
         oscam_subscription = "SUBSCRIPTIONID"
         }
 }
```

License
----

GPLv3

   [DazClimax]: <https://github.com/DazClimax>
   [git-repo-url]: <https://github.com/DazClimax/check_oscam.git>
