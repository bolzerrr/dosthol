0.7.1.
- Added line and comment to set a default value for start to use the daemon with any WOL-client that can send a standard Magic Packet to wake up by MAC address

General
- Before enabling the service, test the script on the command line! (make it executable)
- Stop the running process with CTRL-Z
- Kill the process (otherwise no further instance can be started due to used address)#	v0.7 (2020-12-02) - Fixup dependency check, added Reboot command, changed from GPLv2 to GPLv3

0.6 (2020-12-02) - Check for missing dependencies

0.5 - nothing changed

0.4 - nothing changed

0.3 (2016-03-11) - Parameter parsing, help extended, some beautifyings

0.2 (2016-03-07) - Renamed dosthol to dosthold, created client dostholc, finished more commands, turned to socat

0.1 (2016-03-06) - Initial work; starting virtual machines per wake-on-lan works