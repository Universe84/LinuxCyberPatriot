# LinuxCyberPatriotToDo

- Read README
- Do Forensic Questions First (Info can be lost if not done first)
- Remove Bad Software (FreeCiv) or any of these programs (nmap zenmap apache2 nginx lighttpd wireshark tcpdump netcat-traditional nikto ophcrack)
- Update Services Specified in the README
- $Word means replace it with the needed thing
## Install Updates

```
apt-get update && apt-get upgrade && apt-get dist-upgrade
```

## Install/Enable Firewall

```
sudo apt-get install ufw && ufw enable
```
- Make sure its running 
```
sudo ufw status
```

## SSH settings
```
/etc/ssh/sshd_config
```
- Settings
```
PermitRootLogin no
ChallengeResponseAuthentication no
PasswordAuthentication no
UsePAM no
PermitEmptyPasswords no
```
- Add Port 22 to Firewall (Only Accept Local Connections)
```
sudo ufw allow from 202.54.1.5/29 to any port 22
```
- No keepalive or unattended sessions
```
ClientAliveInterval 300
ClientAliveCountMax 0
```
- Disable obsolete rsh settings
```
IgnoreRhosts yes
```
- Check sshd_config file for correctness before restart
```
sudo sshd -t
```
## Lock Root User
```
passwd -l root
```
## Secure Users
- Set up Auditing
```
apt-get install auditd && auditctl -e 1
```
Go to 
```
/etc/lightdm/lightdm.conf 
```
```
allow-guest=false
```
## GUI Stuff
- In the GUI set Update Manager->Settings->Updates->Check for updates:->Daily
- Turn off automatic login
## Ports
-See Active Ports
```
sudo ss -ln
```
- Neccessary Ports: 80 & 443 (https, https)
- Potential Threats: 20-21, 23, 135, 411-412 (ftp, telnet, remote desktop, peer-peer)
-Close Port
```
sudo lsof -I :$port
```

