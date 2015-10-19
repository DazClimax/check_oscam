# check_oscam

Icinga / Nagios Plugin for checking Entitlement of an paytv subscription on a running oscam server.

Usage:
   check_oscam -H <IP> -u <user> -p <password> -r <reader -s <id> [-w <days>] [-c <days>]
   check_oscam [-h | --help]

   Warning and critical values are optional, default warning is 14 days and default critial is 1 day all other values are needed
