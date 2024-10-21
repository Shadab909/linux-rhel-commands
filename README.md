# Linux RHEL Commands

## 01. File Operations
- 'ls'
    - ls                # Lists files in the current directory
    - ls -l /home/user  # Lists files in /home/user with detailed info (permissions, size, etc.)
 
- 'cp'
    - cp file.txt /home/user/       # Copies file.txt to /home/user directory
    - cp -r /var/log /backup/logs   # Recursively copies /var/log directory to /backup/logs
    - Root Required  if copying to system directories like /etc or /var

 
- 'mv'
    - mv file.txt /home/user/       # Moves file.txt to /home/user directory
    - mv oldfile.txt newfile.txt    # Renames oldfile.txt to newfile.txt
    - Root Required if moving/renaming files in system directories or root-owned files.

- 'rm'
    - rm file.txt                     # Deletes file.txt
    - rm -r /home/user/old_directory  # Recursively deletes /home/user/old_directory
    - Root Required if deleting files in system directories or owned by root.

## 02. Directory Management

- 'mkdir'
    - mkdir /home/user/new_directory  # Creates a directory called new_directory in /home/user
    - mkdir -p /home/user/project/src # Creates nested directories (project/src)
    - Root Required if creating directories in system paths like /etc or /usr

 
- 'rmdir'
    - rmdir /home/user/empty_directory  # Removes an empty directory
    - Root Required if removing directories in system locations.

 
- 'cd'
    - cd /home/user/projects  # Changes to /home/user/projects directory
    - cd ..                   # Moves one level up in the directory tree

- 'pwd'
    - pwd  # Displays the current working directory

## 03. File Permissions and Ownership

- 'chmod'
    - chmod 755 script.sh               # Grants read, write, execute permissions to the owner, and read, execute to others
    - chmod -R 644 /home/user/docs      # Recursively sets all files in /home/user/docs to be readable by everyone, but writable only by the owner
    - Root Required if modifying system files or files owned by root.

 
- 'chown'
    - chown user:group file.txt         # Changes ownership of file.txt to user and group
    - chown -R user:group /home/user    # Recursively changes ownership of /home/user directory
    - Root Required

## 04. System Monitoring and Resource Management

- Root Not Required for monitoring general user processes and directories
- Root Required to view all processes, detailed I/O stats, or to monitor system directories/files owned by root.

- 'top'
    - top                   # Start top interface
    - top -u username       # Show only processes for a specific user
 
- 'htop'
    - htop  # Starts the htop interface
    - More intuitive than top and allows scrolling through processes.

 
- 'ps'
    - ps                      # Show processes for the current shell
    - ps aux                  # Show all processes with detailed information
    - ps -u username          # Show processes for a specific user

 
- 'df'
    - df -h           # Display disk space usage in human-readable format
    - df -T           # Show filesystem type along with usage

 
- 'du'
    - du -h /home/user      # Show space usage of /home/user directory in human-readable format
    - du -sh /var/log       # Show total space used by /var/log directory

 
- 'free'
    - free                # Display memory usage
    - free -h             # Display memory in human-readable format

 
- 'uptime'
    - uptime  # Show uptime and load averages

 
- 'iostat'
    - iostat              # Display CPU and I/O statistics
    - iostat -d 2 5       # Show I/O stats for devices every 2 seconds, 5 times

 
- 'vmstat'
    - vmstat              # Show virtual memory stats since last boot
    - vmstat 5            # Display stats every 5 seconds

 
- 'sar'
    - sar -u 1 5          # Report CPU usage every second for 5 iterations
    - sar -r              # Report memory usage



## 05. Package Management
- 'yum / dnf'
    - Root Required
    - yum install httpd           # Install Apache HTTP Server
    - yum update                  # Update all packages to the latest version
    - yum remove nginx            # Uninstall nginx package
    - dnf search nginx            # Search for a package named nginx
    - dnf check-update            # Check for available package updates
    
 
- 'rpm'
    - Root Required
    - rpm -ivh package.rpm        # Install a package from a local RPM file
    - rpm -e package_name         # Remove a package
    - rpm -qa                     # List all installed RPM packages
    - rpm -qf /usr/bin/wget       # Find which package installed a particular file

- 'yum list / dnf list'
    - yum list installed          # Show all installed packages
    - yum list available          # Show all available packages
    - dnf list updates            # List all packages with available updates
 
- 'yum info / dnf info'
     - yum info httpd              # Display information about the httpd package
     - dnf info nginx              # Display information about the nginx package
 
- 'yum clean all / dnf clean all'
    - Root Required
    - yum clean all               # Remove all cached data
    - dnf clean all               # Clear cache and metadata
 
- 'yum history / dnf history'
    - yum history                 # Display the package management history
    - dnf history info 3          # Show detailed info for transaction ID 3
 
- 'rpm -V'
    - rpm -Va                    # Verify all installed packages
    - rpm -V package_name         # Verify a specific package

- 'rpm -qi'
    - rpm -qi package_name        # Show detailed information for an installed package
    - rpm -ql package_name        # List all files installed by a package

- 'dnf groupinstall / yum groupinstall'
    - Root Required  
    - dnf groupinstall "Development Tools"  # Install all development tools
    - yum groupinstall "Web Server"         # Install web server packages

- 'dnf autoremove / yum autoremove'
    - Root Required 
    - dnf autoremove             # Remove unnecessary packages
    - yum autoremove             # Clean up unused dependencies


## 06. Networking
- 'ping'
    - ping google.com               # Ping Google to test connectivity
    - ping -c 4 192.168.1.1         # Send 4 ping requests to a specific IP

- 'curl'
    - curl http://example.com      # Fetch the webpage from example.com
    - curl -O http://example.com/file.txt  # Download a file from a URL

- 'wget'
    - wget http://example.com/file.txt  # Download a file
    - wget -r http://example.com/        # Download an entire website recursively

- 'nslookup'
    - nslookup google.com            # Look up the IP address for google.com
    - nslookup 8.8.8.8              # Find domain name for a specific IP

- 'ip'
    - ip addr show                  # Show all IP addresses assigned to interfaces
    - ip link show                  # Show all network interfaces
    - ip route show                 # Show the routing table

- 'netstat'
    - netstat -tuln                # Show listening TCP and UDP ports
    - netstat -r                   # Display the routing table
    - netstat -i                   # Show network interface statistics

- 'ss'
    - ss -tuln                     # Show all listening TCP and UDP sockets
    - ss -s                        # Show summary statistics

- 'hostname'
    - hostname                       # Display the current hostname

## 07. User Management
- 'who'
    - who                        # Show all logged-in users
- 'finger'
    - finger newuser              # Show information about newuser
    - finger                      # Show information about all logged-in users

- 'id'
    - id newuser                  # Show user ID and group ID for newuser
    - id                         # Show user and group information for the current user

- 'groups'
    - groups newuser              # Show groups for newuser
    - groups                      # Show groups for the current user




## 08. Archiving and Compression

## 09. Disk Management
- 'lsblk'
    - lsblk                        # Show all block devices
    - lsblk -f                     # Show filesystems on each block device

- 'parted'
    - parted /dev/sda              # Open parted for the specified disk

- 'fdisk'
    - fdisk -l                     # List all disk partitions
 

## 10. System Shutdown and Reboot

## 11. Searching and Text Processing
- 'find'
    - find /var/log -name "*.log"   # Find all log files in /var/log
    - find /var/log -type f -mtime -7    # Find files in /var/log modified in the last 7 days

- 'grep'
    - grep "error" /var/log/messages # Search for "error" in the messages log
    - grep -i "failed" /var/log/secure # Search for "failed" in the secure log, case-insensitive
 
- 'awk'
    - awk '{print $1}' file.txt          # Print the first column of each line in file.txt
    - awk -F: '{print $1}' /etc/passwd    # Print the first field (username) from /etc/passwd

- 'sed'
    - sed 's/foo/bar/g' file.txt        # Replace "foo" with "bar" in file.txt
    - sed -n '1,5p' file.txt             # Print lines 1 to 5 from file.txt

- 'cut'
    - cut -d: -f1 /etc/passwd           # Print the first field (username) from /etc/passwd
    - cut -c1-5 file.txt                # Print the first 5 characters of each line in file.txt

- 'uniq'
    - uniq file.txt                     # Omit repeated lines in file.txt
    - sort file.txt | uniq              # Sort and remove duplicates

- 'wc'
    - wc file.txt                       # Show line, word, and byte counts for file.txt
    - wc -l file.txt                    # Show only the line count

- 'diff'
    - diff file1.txt file2.txt          # Show differences between file1.txt and file2.txt


- 'cat'
    - cat /var/log/boot.log         # Display the boot log

- 'less'
    - less /var/log/auth.log        # View the authentication log

- 'tail'
    - tail /var/log/messages        # Show the last 10 lines of the messages log
    - tail -f /var/log/syslog       # Follow the syslog file in real-time

## 12. Logs and System Events
- 'systemctl'
    - systemctl status httpd        # Show status and logs for the httpd service
 
- 'logger'
    - logger "This is a test log message" # Log a custom message
 
- 'dmesg'
    - dmesg                         # Show all kernel messages
    - dmesg | tail                  # Show the last few kernel messages

- 'journalctl'
    - journalctl                    # Show all logs
    - journalctl -u sshd            # Show logs for the sshd service
    - journalctl --since "2024-10-01" # Show logs since a specific date
    - journalctl -u httpd --since "1 hour ago" # Show recent logs for httpd

## 13. System Information

- 'cat /proc/meminfo'
    - cat /proc/meminfo              # Show detailed memory information
- 'cat /proc/cpuinfo'
    - cat /proc/cpuinfo             # Show detailed CPU information
- 'lscpu'
    - lscpu                          # Display CPU architecture information
- 'uname'
    - uname -a                       # Show all system information
    - uname -r                       # Show kernel version


## 14. Scheduling Tasks
- 'batch'
    - echo "bash /path/to/script.sh" | batch  # Run script.sh when system load allows
 
- 'at'
    - echo "bash /path/to/script.sh" | at 14:00  # Run script.sh at 2 PM

- 'crontab'
    - crontab -l                     # List current user's cron jobs
    - crontab -r                     # Remove all cron jobs for the current user

- 'cron'
    - crontab -e                     # Edit the crontab for the current user
    - 0 2 * * * /path/to/script.sh  # Run script.sh at 2 AM daily



## 15. Service Management
- 'systemctl is-enabled'
    - systemctl is-enabled httpd      # Check if httpd is enabled to start at boot
 
- 'systemctl is-active'
    - systemctl is-active httpd       # Check if the httpd service is active

- 'systemctl list-units'
    - systemctl list-units --type=service   # List all services
    - systemctl list-units --state=running   # List all running services


## 16. Security and Firewall

