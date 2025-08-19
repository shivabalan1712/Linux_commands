## 🖥️ Linux Process & System Management — Complete Reference
---
### ⚙️ Process Management
### 📌 Viewing Processes

- `ps` → Show processes

   - `ps` → Show processes in current shell

   - `ps -e` → Show all processes

   - `ps -f` → Full format (PPID, CMD, UID, etc.)

   - `ps aux` → Detailed list of all processes

`top` → Real-time process monitor

`htop` → Interactive process monitor (with colors, tree view)

`pidof process_name` → Get PID of a process

`pgrep process_name` → Search process by name

### 📌 Controlling Processes

- `kill PID` → Kill process

- `kill -9 PID` → Force kill

- `pkill process_name` → Kill by name

- `killall process_name` → Kill all instances of process

- Foreground & Background jobs

   - `command &` → Run process in background

   - `jobs` → List background jobs

   - `fg %1` → Bring job 1 to foreground

   - `bg %1` → Resume job 1 in background

   - `Ctrl+Z` → Suspend a running process

   - `disown %1` → Remove job from shell’s job table

### 📌 Scheduling Processes

- `at 10:00` → Schedule a job at 10:00 AM

- `atq` → List scheduled at jobs

- `atrm <job_id>` → Remove scheduled job

- `cron` → Repeated scheduled jobs

   - `crontab -e` → Edit cron jobs

   - `crontab -l` → List user’s cron jobs

   - Cron format:
   ```bash
   * * * * * command
   | | | | |
   | | | | └── Day of week (0-6, Sunday=0)
   | | | └──── Month (1-12)
   | | └────── Day of month (1-31)
   | └──────── Hour (0-23)
   └────────── Minute (0-59)
   ```

- `systemd timers` (modern replacement for cron)

- `systemctl list-timers` → List timers

### 🧑‍💻 User & Group Management

- `whoami` → Current user

- `who` → Who is logged in

- `w` → Detailed login info

- `id` → User ID and group IDs

- `adduser username` → Add new user

- `useradd username` → Alternative user creation command

- `passwd username` → Change password

- `usermod -aG group user` → Add user to group

- `groups username` → Show groups for a user

- `groupadd groupnam e` → Create new group

- `groupdel groupname` → Delete group

- `su username` → Switch user

- `sudo command` → Run as superuser

- `visudo` → Safely edit sudoers file

### 🖧 Networking Management

- `ifconfig` → Show network interfaces (deprecated)

- `ip a` → Show IP addresses

- `ip link` → Show network devices

- `ip route` → Show routing table

- `ping host` → Test connectivity

- `curl url` → Fetch data

- `wget url` → Download files

- `netstat -tulnp` → Show listening ports & processes (deprecated)

- `ss` -tulnp → Modern alternative to netstat

- `traceroute host` → Trace packet route

- `dig domain` → DNS lookup

- `nslookup domain` → DNS resolution

### 💾 Disk & File System Management

- `df -h` → Show disk usage

- `du -sh dir/` → Show directory size
 
- `lsblk` → Show block devices

- `mount /dev/sda1 /mnt` → Mount a filesystem

- `umount /mnt` → Unmount filesystem

- `blkid` → Show block device attributes

- `fdisk -l` → Partition listing

- `parted` → Disk partitioning tool

- `mkfs.ext4 /dev/sdb1` → Format partition

### 📊 System Monitoring & Performance
#### 📌 CPU & Memory

- `uptime` → Show system load averages

- `free -h` → Show memory usage

- `vmstat` → System performance summary

- `sar` → Historical performance stats (if sysstat installed)

#### 📌 Logs

- `dmesg` → Kernel ring buffer logs

- `journalctl` → Systemd logs

- `tail -f /var/log/syslog` → Live system logs

#### 📌 Hardware Info

- `uname -a` → Kernel info

- `lscpu` → CPU details

- `lsusb` → USB devices

- `lspci` → PCI devices

- `dmidecode` → Hardware details (BIOS, system info)

#### 🔧 System Control (Init / Systemd)

- `systemctl status` → Show systemd status

- `systemctl list-units` → Show running services

- `systemctl start service` → Start a service

- `systemctl stop service` → Stop a service

- `systemctl restart service` → Restart a service

- `systemctl enable service` → Enable service at boot

- `systemctl disable service` → Disable service at boot

- `shutdown -h now` → Shutdown immediately

- `shutdown -r now` → Reboot immediately

- `reboot` → Reboot system

- `halt` → Halt system

### 📦 Package Management
#### Debian/Ubuntu

- `sudo apt update` → Update package index

- `sudo apt upgrade` → Upgrade all packages

- `sudo apt install pkg` → Install package

- `sudo apt remove pkg` → Remove package

#### RHEL/CentOS/Fedora

- `sudo yum install pkg / dnf install pkg` → Install package

- `sudo yum update / dnf update` → Update packages

- `sudo yum remove pkg` → Remove package

#### OpenSUSE (zypper)

- `sudo zypper install pkg` → Install package

- `sudo zypper update` → Update packages

- `sudo zypper remove pkg` → Remove package

### 🔐 Security & Access Control

- `chmod 755 file` → Change permissions

- `chown user:group file` → Change ownership

- `umask` → Default permission mask

- `ufw enable` → Enable firewall (Ubuntu)

- `ufw allow 22` → Allow SSH

- `iptables -L` → List firewall rules

- `firewall-cmd --list-all` → FirewallD active rules 