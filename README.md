# dosthol - Do something on LAN

Skript to do something with remote virtual machines
Written primarily for Proxmox VE >=v4.x

All thanks and credits to Oliver Jaksch

Discussion: [Proxmox forum](https://forum.proxmox.com/threads/update-wake-and-other-on-lan-for-vms-v0-3.26381/)

## Linux install

```sh
# Update package list:
apt-get update

# Installation dependency:
apt install gawk socat xxd vim

# Change file permissions
cp dosthol.service.app /etc/systemd/system/dosthol.service

# Change file permissions
chmod +s /etc/systemd/system/dosthol.service

# enable dosthol
systemctl enable dosthol

# status dosthol
systemctl status dosthol
```
## Usage

```
 dostholc - The dosthol client, v0.7
 Call it with at least two parameters, like 'dostholc -f FUNCTION -m MAC'
 Possible parameters are
 -f | --function	(one of wakeup|shutdown|poweroff|suspend|resume|reboot|reset (n/a for lxc))
 -m | --mac		(MAC address in the form of 11:22:33:44:55:66)
 -v | --verbose		(0 for no output (default), 1 for some output)
 -i | --ip		(255.255.255.255 (default) for broadcast on actual subnet - or enter another IP or subnet)
```
Example:
```sh
./dostholc.sh -f wakeup -m AA:BB:CC:DD:EE:FF -i 192.168.0.100 -v 1
```

## Dependencies

- PVE v4.x
- vim
- socat
- gawk
- xxd