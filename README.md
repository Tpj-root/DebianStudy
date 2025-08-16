# DebianStudy
Debian = a free, open-source Linux operating system made entirely from GNU tools + Linux kernel.


**simple one-line steps** to build from source on Debian:

1. **Get source**

```bash
apt source hexchat
```

2. **Install build deps**

```bash
sudo apt build-dep hexchat
```

3. **Enter folder**

```bash
cd hexchat-*
```

4. **Configure build**

```bash
meson setup builddir
```

5. **Compile**

```bash
ninja -C builddir
```

6. **Install (optional)**

```bash
sudo ninja -C builddir install
```





**Debian study quick list** in one-liners:

* **Update system** → `sudo apt update && sudo apt upgrade`
* **Install package** → `sudo apt install <pkg>`
* **Remove package** → `sudo apt remove <pkg>`
* **Search package** → `apt search <word>`
* **Show package info** → `apt show <pkg>`
* **Download source** → `apt source <pkg>`
* **Build deps** → `sudo apt build-dep <pkg>`
* **List files in pkg** → `dpkg -L <pkg>`
* **Find owner of file** → `dpkg -S /path/file`
* **List installed** → `dpkg -l`
* **Check service** → `systemctl status <service>`
* **Enable service** → `sudo systemctl enable <service>`
* **Start service** → `sudo systemctl start <service>`
* **Reboot** → `sudo reboot`
* **Shutdown now** → `sudo poweroff`
* **Switch user** → `su - <user>`
* **Show IP** → `ip a`
* **Show routes** → `ip r`
* **Ping test** → `ping -c 4 google.com`
* **DNS lookup** → `dig <domain>` or `nslookup <domain>`
* **Disk usage** → `df -h`
* **Dir usage** → `du -sh *`
* **Check memory** → `free -h`
* **Check CPU** → `lscpu`
* **List PCI devices** → `lspci`
* **List USB devices** → `lsusb`
* **Kernel info** → `uname -a`
* **OS release** → `cat /etc/os-release`
* **Find process** → `ps aux | grep <name>`
* **Kill process** → `kill -9 <pid>`
* **Monitor processes** → `top` or `htop`
* **Edit file** → `nano <file>`
* **Search text** → `grep "word" <file>`
* **Find file** → `find / -name <file>`
* **Archive tar** → `tar -czvf file.tar.gz dir/`
* **Extract tar** → `tar -xzvf file.tar.gz`
* **List tar** → `tar -tzf file.tar.gz`
* **Check logs** → `journalctl -xe`
* **Last boots** → `last -x`


**package building commands** (compile, make, dpkg-buildpackage)


* **Compile C** → `gcc -o app main.c`
* **Compile C99** → `gcc -std=c99 -o app main.c`
* **Run Makefile** → `make`
* **Clean build** → `make clean`
* **Verbose build** → `make V=1`
* **Check build deps** → `apt-rdepends <pkg>`
* **Build Debian pkg** → `dpkg-buildpackage -us -uc`
* **Install local .deb** → `sudo dpkg -i file.deb`
* **Fix missing deps** → `sudo apt -f install`
* **List services** → `systemctl list-units --type=service`
* **Disable service** → `sudo systemctl disable <service>`
* **Stop service** → `sudo systemctl stop <service>`
* **Boot logs** → `dmesg | less`
* **Disk list** → `lsblk`
* **Mount disk** → `sudo mount /dev/sdX /mnt`
* **Unmount disk** → `sudo umount /mnt`
* **Create user** → `sudo adduser <name>`
* **Delete user** → `sudo deluser <name>`
* **Group add** → `sudo addgroup <name>`
* **Add user to group** → `sudo usermod -aG <group> <user>`
* **Change passwd** → `passwd`
* **Check open ports** → `ss -tulpn`
* **Enable firewall** → `sudo ufw enable`
* **Allow port** → `sudo ufw allow 22`
* **Check firewall** → `sudo ufw status`


**network + security**

* **Current IP** → `hostname -I`
* **Default gateway** → `ip route | grep default`
* **Test port** → `nc -zv <host> <port>`
* **Show active connections** → `ss -tnp`
* **Trace route** → `traceroute <host>`
* **Download file** → `wget <url>`
* **Download curl** → `curl -O <url>`
* **Upload with scp** → `scp file user@host:/path/`
* **SSH login** → `ssh user@host`
* **SSH with key** → `ssh -i key.pem user@host`
* **Generate SSH key** → `ssh-keygen -t rsa -b 4096`
* **Copy SSH key** → `ssh-copy-id user@host`
* **Check listening services** → `lsof -i -P -n`
* **Block IP (iptables)** → `sudo iptables -A INPUT -s <ip> -j DROP`
* **Check firewall rules** → `sudo iptables -L -n -v`
* **Show sudo log** → `journalctl _COMM=sudo`
* **Check auth log** → `sudo less /var/log/auth.log`
* **Fail2Ban status** → `sudo fail2ban-client status`
* **Check open files** → `ulimit -n`
* **Set limit** → `ulimit -n 65535`
* **List cron jobs** → `crontab -l`
* **Edit cron jobs** → `crontab -e`



**storage + backup**

* **List partitions** → `fdisk -l`
* **Format ext4** → `sudo mkfs.ext4 /dev/sdX1`
* **Check disk health** → `sudo smartctl -a /dev/sdX`
* **Check inode usage** → `df -i`
* **Create swap file** → `sudo fallocate -l 2G /swapfile && sudo chmod 600 /swapfile && sudo mkswap /swapfile && sudo swapon /swapfile`
* **Check swap** → `swapon --show`
* **List UUIDs** → `blkid`
* **Mount by UUID** → `sudo mount UUID=<uuid> /mnt`
* **Add permanent mount** → edit `/etc/fstab`
* **Backup dir (tar)** → `tar -czf backup.tar.gz /path/to/dir`
* **Restore backup** → `tar -xzf backup.tar.gz -C /path/to/restore`
* **Clone disk (dd)** → `sudo dd if=/dev/sdX of=/dev/sdY bs=64K status=progress`
* **Zero free space** → `sudo dd if=/dev/zero of=zero.fill bs=1M; rm -f zero.fill`
* **Sync cache to disk** → `sync`
* **Check running kernel** → `uname -r`
* **Show loaded modules** → `lsmod`
* **Load module** → `sudo modprobe <module>`
* **Blacklist module** → add to `/etc/modprobe.d/blacklist.conf`
* **Check boot time** → `systemd-analyze`
* **Boot log summary** → `systemd-analyze blame`
* **Show hardware info** → `lshw -short`

**package building + developer workflow** 

* **Install dev tools** → `sudo apt install build-essential`
* **Install headers** → `sudo apt install linux-headers-$(uname -r)`
* **Download source** → `apt source <pkg>`
* **Get build deps** → `sudo apt build-dep <pkg>`
* **Compile pkg** → `dpkg-buildpackage -us -uc`
* **Check .deb info** → `dpkg -I file.deb`
* **List files in .deb** → `dpkg -c file.deb`
* **Install local .deb** → `sudo dpkg -i file.deb`
* **Rebuild index** → `sudo apt update`
* **Reconfigure pkg** → `sudo dpkg-reconfigure <pkg>`
* **Extract .deb** → `dpkg-deb -x file.deb outdir/`
* **Extract + control** → `dpkg-deb -R file.deb outdir/`
* **Build .deb** → `dpkg-deb --build outdir/`
* **Check lint** → `lintian file.deb`
* **Check shared libs** → `ldd ./binary`
* **Show needed symbols** → `nm ./binary | grep <func>`
* **Strip binary** → `strip ./binary`
* **Run configure** → `./configure && make && sudo make install`
* **Uninstall built pkg** → `sudo make uninstall`
* **Check env vars** → `printenv`
* **Set var (temp)** → `export VAR=value`
* **Set var (perm)** → add to `~/.bashrc`




**server + admin** (Apache, Nginx, MySQL, SSH, etc.)

* **Install Apache** → `sudo apt install apache2`
* **Start Apache** → `sudo systemctl start apache2`
* **Enable Apache** → `sudo systemctl enable apache2`
* **Apache status** → `systemctl status apache2`
* **Install Nginx** → `sudo apt install nginx`
* **Start Nginx** → `sudo systemctl start nginx`
* **Reload Nginx** → `sudo systemctl reload nginx`
* **Check ports** → `ss -tulpn | grep LISTEN`
* **Install MariaDB/MySQL** → `sudo apt install mariadb-server`
* **Start MariaDB** → `sudo systemctl start mariadb`
* **Secure MySQL** → `sudo mysql_secure_installation`
* **Login MySQL** → `mysql -u root -p`
* **Create DB** → `CREATE DATABASE testdb;`
* **Create User** → `CREATE USER 'user'@'localhost' IDENTIFIED BY 'pass';`
* **Grant rights** → `GRANT ALL PRIVILEGES ON testdb.* TO 'user'@'localhost';`
* **Flush** → `FLUSH PRIVILEGES;`
* **Install PHP** → `sudo apt install php libapache2-mod-php`
* **Check PHP** → `php -v`
* **Install SSH** → `sudo apt install openssh-server`
* **Start SSH** → `sudo systemctl start ssh`
* **Enable SSH** → `sudo systemctl enable ssh`
* **SSH status** → `systemctl status ssh`
* **Restart service** → `sudo systemctl restart <service>`
* **Check logs** → `sudo journalctl -u <service>`
* **Tail logs** → `sudo journalctl -f -u <service>`
* **Check boot logs** → `dmesg | less`

**Docker + virtualization**

* **Install Docker** → `sudo apt install docker.io`
* **Start Docker** → `sudo systemctl start docker`
* **Enable Docker** → `sudo systemctl enable docker`
* **Check Docker** → `docker --version`
* **List images** → `docker images`
* **List containers** → `docker ps -a`
* **Run container** → `docker run -it ubuntu bash`
* **Pull image** → `docker pull debian:latest`
* **Remove container** → `docker rm <id>`
* **Remove image** → `docker rmi <id>`
* **Stop container** → `docker stop <id>`
* **Start container** → `docker start -ai <id>`
* **Logs container** → `docker logs <id>`
* **Copy into container** → `docker cp file <id>:/path/`
* **Exec inside container** → `docker exec -it <id> bash`
* **Prune unused** → `docker system prune -a`
* **Build image** → `docker build -t myapp .`
* **Save image** → `docker save myapp > myapp.tar`
* **Load image** → `docker load < myapp.tar`

### Virtualization (KVM/VirtualBox)

* **Install KVM** → `sudo apt install qemu-kvm libvirt-daemon-system virt-manager`
* **Check VM support** → `egrep -c '(vmx|svm)' /proc/cpuinfo`
* **Start VM manager** → `virt-manager`
* **List VMs** → `virsh list --all`
* **Start VM** → `virsh start <vmname>`
* **Shutdown VM** → `virsh shutdown <vmname>`
* **Destroy VM (force off)** → `virsh destroy <vmname>`
* **Clone VM** → `virt-clone --original <vmname> --name newvm --file /var/lib/libvirt/images/newvm.qcow2`




**Debian networking + firewall (iptables, nftables, ufw)**

### 🔹 Networking

* **Show IP** → `ip addr show`
* **Show routes** → `ip route show`
* **Bring interface up** → `sudo ip link set enp3s0 up`
* **Bring interface down** → `sudo ip link set enp3s0 down`
* **Assign IP** → `sudo ip addr add 192.168.1.10/24 dev enp3s0`
* **Delete IP** → `sudo ip addr del 192.168.1.10/24 dev enp3s0`
* **Set default route** → `sudo ip route add default via 192.168.1.1`
* **Flush IPs** → `sudo ip addr flush dev enp3s0`
* **Check DNS** → `cat /etc/resolv.conf`
* **Test connectivity** → `ping -c 4 8.8.8.8`
* **Traceroute** → `traceroute google.com`
* **Speed test** → `curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python3 -`

### 🔹 Firewall (UFW)

* **Install ufw** → `sudo apt install ufw`
* **Enable ufw** → `sudo ufw enable`
* **Allow SSH** → `sudo ufw allow 22/tcp`
* **Allow HTTP** → `sudo ufw allow 80/tcp`
* **Allow HTTPS** → `sudo ufw allow 443/tcp`
* **Deny port** → `sudo ufw deny 23/tcp`
* **Delete rule** → `sudo ufw delete allow 22/tcp`
* **List rules** → `sudo ufw status numbered`
* **Reset firewall** → `sudo ufw reset`

### 🔹 Firewall (iptables)

* **List rules** → `sudo iptables -L -v -n`
* **Allow port 22** → `sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT`
* **Block IP** → `sudo iptables -A INPUT -s 1.2.3.4 -j DROP`
* **Block subnet** → `sudo iptables -A INPUT -s 192.168.1.0/24 -j DROP`
* **Drop all incoming** → `sudo iptables -P INPUT DROP`
* **Allow loopback** → `sudo iptables -A INPUT -i lo -j ACCEPT`
* **Save rules** → `sudo sh -c "iptables-save > /etc/iptables/rules.v4"`
* **Restore rules** → `sudo iptables-restore < /etc/iptables/rules.v4`

### 🔹 Firewall (nftables – newer)

* **List rules** → `sudo nft list ruleset`
* **Add table** → `sudo nft add table inet filter`
* **Add chain** → `sudo nft add chain inet filter input { type filter hook input priority 0; }`
* **Allow SSH** → `sudo nft add rule inet filter input tcp dport 22 accept`
* **Drop all else** → `sudo nft add rule inet filter input drop`
* **Save config** → `sudo nft list ruleset > /etc/nftables.conf`
* **Enable nftables** → `sudo systemctl enable nftables`

**Debian monitoring + performance tuning**

### 🔹 System Monitoring

* **Processes live** → `top`
* **Better top** → `htop`
* **Disk usage** → `df -h`
* **Dir size** → `du -sh *`
* **Memory usage** → `free -h`
* **CPU info** → `lscpu`
* **Kernel log live** → `dmesg -w`
* **System logs** → `journalctl -xe`
* **Follow logs** → `journalctl -f`
* **Last boots** → `last -x`
* **Uptime** → `uptime`

### 🔹 Performance Tools

* **I/O stats** → `iostat -xz 1`
* **Disk speed test** → `dd if=/dev/zero of=testfile bs=1G count=1 oflag=direct`
* **Check I/O usage** → `iotop`
* **Check open files** → `lsof | head`
* **Count open files** → `lsof | wc -l`
* **Who is logged in** → `w`
* **Who last logged** → `last`
* **Monitor network live** → `iftop -i enp3s0`
* **Bandwidth usage** → `nload`
* **Ping latency** → `ping -c 10 8.8.8.8`
* **Check CPU load** → `uptime | awk '{print $9,$10,$11}'`

### 🔹 System Control

* **Shutdown now** → `sudo poweroff`
* **Reboot now** → `sudo reboot`
* **Restart systemd** → `sudo systemctl daemon-reexec`
* **Reload systemd units** → `sudo systemctl daemon-reload`
* **List services** → `systemctl list-units --type=service`
* **Failed services** → `systemctl --failed`
* **Check boot time** → `systemd-analyze`
* **Boot delay details** → `systemd-analyze blame`
* **Critical chain** → `systemd-analyze critical-chain`





Disable auto logout in Debian. It depends on whether it’s **console (tty), desktop session, or lock screen**:

### 1. **For desktop (GNOME, XFCE, KDE etc.)**

* Open **Settings → Power**
* Set **Blank Screen / Suspend / Automatic Logout** → **Never**

### 2. **For system-wide idle logout (systemd-logind)**

Edit config:

```bash
sudo nano /etc/systemd/logind.conf
```

Set:

```
#KillUserProcesses=no
IdleAction=ignore
```

Then reload:

```bash
sudo systemctl restart systemd-logind
```

### 3. **For shell/tty auto logout**

Check if `TMOUT` is set:

```bash
echo $TMOUT
```

If it’s not `0`, disable it by editing `~/.bashrc` or `/etc/profile` and comment/remove:

```bash
# TMOUT=600
```

Then reload:

```bash
source ~/.bashrc
```
👉 After this, Debian won’t auto logout or lock screen.




So the auto logout/lock you see is most likely coming from **desktop power settings** (screen blank / suspend).

👉 Go to your desktop environment settings:

* **GNOME** → *Settings → Power → Blank Screen* → set **Never**
* **XFCE** → *Settings → Power Manager* → disable sleep/blank
* **KDE/Plasma** → *System Settings → Power Management* → turn off idle timeouts




Download source code of any package in Debian from the command line.

### Steps:

1. First enable source repos:

```bash
sudo nano /etc/apt/sources.list
```

Make sure you have lines like:

```
deb-src http://deb.debian.org/debian bookworm main contrib non-free
```

Save → exit.

2. Update package lists:

```bash
sudo apt update
```

3. Install tools (only once):

```bash
sudo apt install build-essential dpkg-dev
```

4. Download source code of a package:

```bash
apt source <packagename>
```

Example:

```bash
apt source bash
```

This will create a folder with the source code.

5. If you want all **build dependencies** too:

```bash
sudo apt build-dep <packagename>
```

---




`sudo apt build-dep <packagename>` → installs (from repos) all the **libraries & tools needed to compile** that package.

* It **does not copy source code**.
* It **does not keep local .deb files by default** (they are installed directly).
* What you get is a working environment to build that package from its source.

If you also want to **keep local copies of the .deb files** (all dependencies), you can use:

```bash
sudo apt-get --download-only build-dep <packagename>
```

They will be saved in `/var/cache/apt/archives/`.




**collect all source + build dependencies locally in Debian** so you can build offline later:

---

### 1. Enable source repos

Edit:

```bash
sudo nano /etc/apt/sources.list
```

Add lines like:

```
deb-src http://deb.debian.org/debian bookworm main contrib non-free
```

Save → exit.

---

### 2. Update repo lists

```bash
sudo apt update
```

---

### 3. Create a workspace dir

```bash
mkdir ~/offline-build && cd ~/offline-build
```

---

### 4. Download source code

```bash
apt source <packagename>
```

👉 Example:

```bash
apt source bash
```

---

### 5. Download all build dependencies (without installing)

```bash
sudo apt-get --download-only build-dep <packagename>
```

This will fetch `.deb` files into:

```
/var/cache/apt/archives/
```

---

### 6. Copy all `.deb` files locally

```bash
cp /var/cache/apt/archives/*.deb ~/offline-build/deps/
```

---

✅ Now you have:

* **Source code folder**
* **All dependency .deb files**

You can take them to another machine, install with:

```bash
sudo dpkg -i *.deb
```

then build with:

```bash
dpkg-buildpackage -us -uc
```

---




**Bash script** to grab source + all build dependencies for offline build in Debian:

```bash
#!/bin/bash
# Usage: ./offline-build.sh <package>
# Example: ./offline-build.sh bash

PKG=$1

if [ -z "$PKG" ]; then
  echo "Usage: $0 <package>"
  exit 1
fi

# Make workspace
WORKDIR=~/offline-build/$PKG
mkdir -p "$WORKDIR/deps"
cd "$WORKDIR" || exit 1

echo ">>> Updating repos..."
sudo apt update

echo ">>> Downloading source for $PKG..."
apt source "$PKG"

echo ">>> Downloading build dependencies..."
sudo apt-get --download-only build-dep -y "$PKG"

echo ">>> Copying dependency .deb files..."
cp /var/cache/apt/archives/*.deb "$WORKDIR/deps/"

echo ">>> Done!"
echo "Source code in: $WORKDIR"
echo "Dependencies in: $WORKDIR/deps/"
```

---

### 🔹 How to use:

1. Save as `offline-build.sh`
2. Make executable:

   ```bash
   chmod +x offline-build.sh
   ```
3. Run:

   ```bash
   ./offline-build.sh bash
   ```

---





`sudo apt build-dep crunch` →

* It **does not install crunch itself**.
* It **installs only the required dependency packages** needed to compile `crunch` from source.

So after that:

1. Your system will have all the libraries & tools installed.
2. You can then run:

   ```bash
   apt source crunch
   cd crunch-*
   dpkg-buildpackage -us -uc
   ```
3. This builds your own `.deb` package for crunch.


When you run:

```bash
sudo apt build-dep crunch
```

Debian looks into the **source package metadata**, not the binary package.

### 🔹 Where deps come from?

* Each Debian source package has a file called **`debian/control`**.
* Inside it there is a section:

  ```
  Build-Depends: debhelper-compat (= 13), libpam0g-dev, libssl-dev, zlib1g-dev, ...
  ```
* This line tells exactly which `.deb` packages are needed to **compile** the software.

### 🔹 What happens next?

1. `apt build-dep` reads that list.
2. It checks your system for those packages.
3. Any missing ones → it installs them from the Debian repo.
4. The program itself (`crunch`) is **not installed** — only the tools/libs needed to build it.

---

✅ So in short:

* **`apt install crunch`** → installs prebuilt crunch.
* **`apt build-dep crunch`** → installs only the compiler + libs required to build crunch from source.




Debian determines which packages to install when you run:

```bash
sudo apt build-dep crunch
```

---

### How Debian Finds Build Dependencies

* Debian looks at the **source package metadata**, not the binary package.
* In the source tree, there's a `debian/control` file with a section like:

  ```
  Build-Depends: libpam0g-dev, libssl-dev, zlib1g-dev, ...
  ```

  These are the exact .deb packages required to compile the software.
* `apt build-dep crunch` reads that metadata, checks for missing packages, and installs only those **build dependencies**—it does **not** install the `crunch` program itself.([Debian][1], [man7.org][2])

---

### Verifying the Build-Depends for `crunch`

You can see the actual list of build dependencies for the `crunch` package by running:

```bash
apt-cache showsrc crunch
```

This will print details of the source package, including the `Build-Depends:` line.([Ask Ubuntu][3])

---

### Summary

| Action                     | Purpose                                                                                        |
| -------------------------- | ---------------------------------------------------------------------------------------------- |
| `apt build-dep crunch`     | Installs all packages needed to build `crunch` from source—**does not install crunch itself**. |
| `apt-cache showsrc crunch` | Displays the source metadata including the list of build dependencies.                         |




**`Build-Depends:`**

---

### How to Inspect the Build Dependencies for `crunch`

#### **Option 1: Use `apt-cache showsrc` (if you’re on Debian)**

```bash
apt-cache showsrc crunch
```

This shows the source package metadata, including the `Build-Depends:` line directly.

#### **Option 2: Manually download the source and inspect the `debian/control` file**

Steps:

1. Enable source repositories in `/etc/apt/sources.list` (ensure `deb-src …` lines are present).
2. Update package lists:

   ```bash
   sudo apt update
   ```
3. Download the source for `crunch`:

   ```bash
   apt source crunch
   ```
4. Enter the source directory:

   ```bash
   cd crunch-*
   ```
5. Open the `debian/control` file and look for the `Build-Depends:` section.

---

### Why It Works

* The **`debian/control`** file inside the source lists dependencies needed for building (`Build-Depends`), not runtime dependencies.
* When you run:

  ```bash
  sudo apt build-dep crunch
  ```

---


