# 🐧 Linux Firewall Lab: UFW (Uncomplicated Firewall)

## Objective
Block insecure services (Telnet on port 23), allow secure access (SSH on port 22), verify their effect, and document the process.

---

## Steps Performed

### 1. Enable UFW
```bash
sudo ufw enable
```
Expected Result:
```code
Firewall is active and enabled on system startup
```
### 2. Check Firewall Status
```bash
sudo ufw status verbose
```
Expected Result:
```code
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip
```
### 3. Configure Rules
```bash
sudo ufw deny 23/tcp
sudo ufw allow 22/tcp
sudo ufw deny 21/tcp
```
Expected Result:
```code
Rule added
Rule added (v6)
```
### 4. Verify Rules
```bash
sudo ufw status
```
Expected Result:
```Code
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
23/tcp                     DENY        Anywhere
21/tcp                     DENY        Anywhere
22/tcp (v6)                ALLOW       Anywhere (v6)
23/tcp (v6)                DENY        Anywhere (v6)
21/tcp (v6)                DENY        Anywhere (v6)
```
### 5. Test the Rules
Telnet Test (should fail)
```bash
telnet localhost 23
```
Expected Result:
```Code
Trying ::1...
Connection failed: Connection refused
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
SSH Test (should succeed)
```
SSH Test (should succeed)
```bash
ssh kali@localhost
```
Expected Result:
```Code
kali@localhost's password:
Linux kali 6.12.38-kali-amd64 ...
Last login: Wed Nov 19 13:26:10 2025 from ::1
```
Note: If SSH fails, ensure the SSH server is installed and running:
```bash
sudo apt install openssh-server -y
sudo systemctl start ssh
sudo systemctl enable ssh
```
