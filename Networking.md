# 🌐 Linux Networking & Communication — Complete Reference

---

## 📌 1. Basic Connectivity

* **Check if a host is reachable**

  ```bash
  ping google.com
  ```

  Sends ICMP packets and shows response times.

  * `ping -c 5 google.com` → Send exactly 5 pings.
  * `ping -i 2 google.com` → Send ping every 2 seconds.

* **Trace the path packets take**

  ```bash
  traceroute google.com
  ```

  Shows each hop from your machine to the destination. Useful for diagnosing routing issues.

* **Continuous traceroute + ping (interactive)**

  ```bash
  mtr google.com
  ```

  Combines `ping` + `traceroute` in real time (requires installation).

---

## 📌 2. IP & Interface Management

* **Old method (still used in some distros):**

  ```bash
  ifconfig
  ```

  Shows network interfaces, IP addresses, MAC addresses.

* **Modern tool (`ip` command):**

  ```bash
  ip a        # Show all IP addresses
  ip addr show eth0   # Show IP of eth0
  ip link show        # Show all network interfaces
  ip route            # Show routing table
  ip route add default via 192.168.1.1
  ```

  More powerful than `ifconfig`.

* **Enable / Disable interfaces:**

  ```bash
  sudo ip link set eth0 up
  sudo ip link set eth0 down
  ```

* **DHCP renewal:**

  ```bash
  sudo dhclient eth0
  ```

  Gets a fresh IP from DHCP server.

---

## 📌 3. DNS & Hostname

* **Check system hostname:**

  ```bash
  hostname
  ```

* **Set hostname (modern):**

  ```bash
  sudo hostnamectl set-hostname new-server
  ```

* **DNS queries:**

  ```bash
  nslookup google.com
  dig google.com
  dig google.com +short   # Just IP
  ```

* **Reverse lookup (IP → domain):**

  ```bash
  dig -x 8.8.8.8
  ```

* **Check `/etc/hosts` mappings:**

  ```bash
  getent hosts google.com
  ```

---

## 📌 4. File Transfer Between Systems

* **Secure Copy (SCP):**

  ```bash
  scp file.txt user@192.168.1.10:/home/user/
  ```

  Copies a file to a remote server.

  * Recursive copy:

    ```bash
    scp -r folder/ user@host:/path/
    ```

* **Secure FTP (SFTP):**

  ```bash
  sftp user@host
  sftp> put localfile
  sftp> get remotefile
  ```

* **Rsync (more efficient sync):**

  ```bash
  rsync -avz file.txt user@host:/path/
  rsync -avz /local/dir user@host:/remote/dir
  ```

  Only transfers changed parts of files. Great for backups.

---

## 📌 5. Remote Access (SSH)

* **Login to remote system:**

  ```bash
  ssh user@192.168.1.10
  ```

* **Use custom port:**

  ```bash
  ssh -p 2222 user@host
  ```

* **Run single remote command:**

  ```bash
  ssh user@host "ls -l /var/log"
  ```

* **Copy SSH key to remote for passwordless login:**

  ```bash
  ssh-copy-id user@host
  ```

* **Tunneling (forward local port to remote):**

  ```bash
  ssh -L 8080:localhost:80 user@host
  ```

  Now visiting `localhost:8080` connects to remote port 80.

---

## 📌 6. Socket & Port Monitoring

* **List open ports (old):**

  ```bash
  netstat -tulnp
  ```

  * `-t` → TCP
  * `-u` → UDP
  * `-l` → Listening
  * `-n` → Show numbers (not names)
  * `-p` → Show process

* **Modern replacement:**

  ```bash
  ss -tulnp
  ```

* **See which process is using a port:**

  ```bash
  lsof -i :80
  ```

  Shows PID and process using port 80.

* **Test if a port is open:**

  ```bash
  nc -zv host 22
  ```

  Checks if SSH (22) is open on host.

* **Listen on a port (debugging):**

  ```bash
  nc -l 1234
  ```

  Starts a listener on port 1234.

---

## 📌 7. Downloading & Communication

* **Download file (wget):**

  ```bash
  wget https://example.com/file.zip
  ```

* **Download with resume support:**

  ```bash
  wget -c https://example.com/file.zip
  ```

* **Using curl:**

  ```bash
  curl https://example.com
  curl -I https://example.com    # Headers only
  curl -O https://example.com/f1.zip   # Save with filename
  curl -o myfile.zip https://example.com/f1.zip  # Save as myfile.zip
  ```

* **Post data (like API testing):**

  ```bash
  curl -X POST -d "name=shiva&role=dev" https://example.com/api
  ```

---

## 📌 8. Firewalls & Security

### 🔹 UFW (Uncomplicated Firewall — Ubuntu/Debian)

* Enable firewall:

  ```bash
  sudo ufw enable
  ```
* Allow ports:

  ```bash
  sudo ufw allow 22/tcp
  sudo ufw allow 80/tcp
  sudo ufw allow 443/tcp
  ```
* Check status:

  ```bash
  sudo ufw status verbose
  ```

### 🔹 Iptables (older, low-level)

* List rules:

  ```bash
  sudo iptables -L -n -v
  ```
* Allow port:

  ```bash
  sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
  ```
* Block IP:

  ```bash
  sudo iptables -A INPUT -s 1.2.3.4 -j DROP
  ```

### 🔹 FirewallD (Fedora/CentOS/RHEL)

* List rules:

  ```bash
  firewall-cmd --list-all
  ```
* Allow service:

  ```bash
  sudo firewall-cmd --add-service=http --permanent
  sudo firewall-cmd --reload
  ```

