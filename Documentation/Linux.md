# Linux Knowledge Bytes

<details>
<summary>Package Management</summary>

## Package Management
DNF stands for Dandified YUM.
It’s the next-generation package manager for Fedora, Red Hat Enterprise Linux (RHEL), and CentOS (from version 8 onward).
Think of it as the "app store backend" for Linux — the tool that installs, updates, removes, and manages software packages.
It replaced the old YUM (Yellowdog Updater, Modified) because it’s faster, smarter, and more reliable.

| Command                      | Description                       |
| ---------------------------- | --------------------------------- |
| `sudo dnf update`            | Update all packages               |
| `sudo dnf upgrade`           | Upgrade packages and dependencies |
| `sudo dnf install <package>` | Install a package                 |
| `sudo dnf remove <package>`  | Uninstall a package               |
| `dnf search <keyword>`       | Search for packages               |
| `dnf info <package>`         | Show package details              |
| `dnf list installed`         | List installed packages           |
| `dnf history`                | Show package transaction history  |

</details>

<details>
<summary>Navigation & File Management</summary>

## Navigation & File Management 
| Command         | Description                                                                   |
| --------------- | ----------------------------------------------------------------------------- |
| `ls`            | List directory contents (`ls -l` for detailed view, `ls -a` for hidden files) |
| `cd`            | Change directory (`cd ..` to go up one level)                                 |
| `pwd`           | Print working directory (shows where you are)                                 |
| `mkdir`         | Create a directory                                                            |
| `rmdir`         | Remove empty directory                                                        |
| `cp`            | Copy files or directories (`cp -r` for recursive)                             |
| `mv`            | Move or rename files                                                          |
| `rm`            | Remove files (`rm -r` for directories)                                        |
| `touch`         | Create an empty file or update a file’s timestamp                             |
| `cat`           | Display file contents                                                         |
| `less` / `more` | View file contents page by page                                               |
| `find`          | Search for files (`find / -name "filename"`)                                  |
| `locate`        | Quickly find files using an indexed database (run `updatedb` first)           |

</details>

<details>
<summary>System Information & Management</summary>

## System Information & Management
| Command       | Description                                                      |
| ------------- | ---------------------------------------------------------------- |
| `uname -a`    | Display kernel and system info                                   |
| `hostnamectl` | Show or change the system’s hostname                             |
| `uptime`      | Show how long the system has been running                        |
| `top`         | View running processes live                                      |
| `htop`        | Improved version of `top` (install with `sudo dnf install htop`) |
| `ps aux`      | List all running processes                                       |
| `free -h`     | Show memory usage                                                |
| `df -h`       | Show disk space usage                                            |
| `du -sh *`    | Show directory sizes                                             |
| `lscpu`       | Display CPU info                                                 |
| `lsblk`       | Show storage devices and partitions                              |
| `dmidecode`   | Display detailed hardware information (requires sudo)            |

</details>

<details>
<summary>User & Permission Management</summary>

## User & Permission Management 
| Command               | Description                        |
| --------------------- | ---------------------------------- |
| `whoami`              | Display current user               |
| `id`                  | Show user ID and group memberships |
| `adduser` / `useradd` | Add new users                      |
| `passwd`              | Change user password               |
| `sudo`                | Run command as root                |
| `chmod`               | Change file permissions            |
| `chown`               | Change file ownership              |
| `groups`              | Show groups a user belongs to      |

</details>

<details>
<summary>Networking</summary>

## Networking

| Command             | Description                                   |
| ------------------- | --------------------------------------------- |
| `ip a`              | Show network interfaces and IPs               |
| `ping`              | Test network connectivity                     |
| `curl`              | Transfer data from URLs                       |
| `wget`              | Download files from the web                   |
| `ss -tuln`          | Show listening ports and connections          |
| `nmcli`             | Manage NetworkManager connections             |
| `dig` or `nslookup` | Query DNS records                             |
| `traceroute`        | Trace the route packets take to a destination |

</details>

<details>
<summary>System Services</summary>

## System Services

| Command                       | Description               |
| ----------------------------- | ------------------------- |
| `systemctl status`            | Check system status       |
| `systemctl start <service>`   | Start a service           |
| `systemctl stop <service>`    | Stop a service            |
| `systemctl restart <service>` | Restart a service         |
| `systemctl enable <service>`  | Enable service on boot    |
| `systemctl disable <service>` | Disable service from boot |
| `journalctl -xe`              | View system logs          |

</details>

<details>
<summary>File Editing & Viewing</summary>

## File Editing & Viewing

| Command              | Description                                                   |
| -------------------- | ------------------------------------------------------------- |
| `nano <file>`        | Edit a file (simple editor)                                   |
| `vi` or `vim <file>` | Advanced text editor                                          |
| `gedit <file>`       | GUI text editor                                               |
| `head` / `tail`      | View first/last lines of a file (`tail -f` follows logs live) |

</details>

<details>
<summary>Compression & Archiving</summary>

## Compression & Archiving

| Command                       | Description                |
| ----------------------------- | -------------------------- |
| `tar -czvf file.tar.gz <dir>` | Create compressed archive  |
| `tar -xzvf file.tar.gz`       | Extract compressed archive |
| `zip -r file.zip <dir>`       | Create ZIP file            |
| `unzip file.zip`              | Extract ZIP file           |

</details>

<details>
<summary>System Power & Boot</summary>

## System Power & Boot

| Command              | Description             |
| -------------------- | ----------------------- |
| `reboot`             | Reboot system           |
| `shutdown -h now`    | Power off               |
| `systemctl poweroff` | Power off (alternative) |
| `systemctl reboot`   | Reboot (alternative)    |

</details>

<details>
<summary>Creating Perminant Aliases on Fedora</summary>

## Creating Perminant Aliases on Fedora

```bash
nano ~/.bashrc
```
Now add you aliases, scroll to the bottom and add your aliases. Below is an example to get started.
```bash
# ---- Custom Aliases ----
alias ll='ls -la --color=auto'
alias cls='clear'
alias update='sudo dnf upgrade -y'
alias ports='ss -tuln'
alias myip="ip a | grep 'inet '"
alias fixfedora='sudo dnf upgrade -y && sudo dnf autoremove -y && sudo dnf clean all'
```
Save and close the file, Ctrl+0 -> Enter -> Ctrl+X
Now let's apply the changes immediately, or close and restart the terminal. 
```bash
source ~/.bashrc
```

</details>