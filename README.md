# dosthol – Do something on LAN

Script to perform actions on remote virtual machines via LAN packets  
Written primarily for Proxmox VE ≥ v4.x

All thanks and credits to Oliver Jaksch

Source repository:  
https://github.com/bolzerrr/dosthol

Discussion: Proxmox forum  
https://forum.proxmox.com/threads/update-wake-and-other-on-lan-for-vms-v0-3.26381/

---

## Linux / Proxmox Install

### 1. Install dependencies

```sh
apt update
apt install gawk socat xxd vim git
```

---

### 2. Checkout source code

```sh
cd /root
git clone https://github.com/bolzerrr/dosthol.git
cd dosthol
```

---

### 3. Install scripts

```sh
install -m 0755 dosthold.sh /usr/local/bin/dosthold.sh
install -m 0755 dostholc.sh /usr/local/bin/dostholc.sh
```

---

### 4. Install systemd service

```sh
cp dosthol.service.app /etc/systemd/system/dosthol.service
chown root:root /etc/systemd/system/dosthol.service
chmod 0644 /etc/systemd/system/dosthol.service
```

The unit file must **not** be executable and must **not** have setuid/setgid bits.

---

### 5. Enable and start service

```sh
systemctl daemon-reload
systemctl enable --now dosthol.service
systemctl status dosthol.service
```

---

## Usage

```
dostholc – The dosthol client, v0.7
 -f | --function   wakeup | shutdown | poweroff | suspend | resume | reboot | reset
 -m | --mac        MAC address (11:22:33:44:55:66)
 -i | --ip         255.255.255.255 (default broadcast)
 -v | --verbose    0 | 1
```

Example:

```sh
dostholc.sh -f wakeup -m AA:BB:CC:DD:EE:FF -i 192.168.0.255 -v 1
```

---

## Uninstall

```sh
systemctl stop dosthol.service
systemctl disable dosthol.service
rm -f /etc/systemd/system/dosthol.service
systemctl daemon-reload

rm -f /usr/local/bin/dosthold.sh
rm -f /usr/local/bin/dostholc.sh
```

(Optional) Remove source checkout:

```sh
rm -rf /root/dosthol
```

---

## Dependencies

- Proxmox VE ≥ 4.x
- socat
- gawk
- xxd
- vim
- git

