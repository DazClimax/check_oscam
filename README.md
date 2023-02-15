# check_oscam

Icinga / Nagios Plugin for checking Entitlement of an paytv subscription on a running oscam server.

  - check entitlement
  - select reader
  - select subscription

### Version
1.1

### Release notes
Small bugfix wrong character for id parameter, function help print s instead of i.
Reduce date function and add version to script.

### Installation

Copy to your plugin folder

```sh
git clone https://github.com/DazClimax/check_oscam.git
```

### Define plugin in icinga

```sh
object CheckCommand "COMANDNAME" {
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
         host_name = "HOSTNAME"
         check_command = "COMANDNAME"
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
