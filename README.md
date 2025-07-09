# ISEA Lab Activities - BRG-27

## Day 1 – Morning

### GitHub Repository Setup
- Created GitHub account and repository: `BRG-27-labs`
- Cloned repository to local machine
- Created README.md for documentation

### VirtualBox and Ubuntu Installation
- Installed VirtualBox on host machine
- Downloaded Ubuntu ISO from official website
- Created VM with 4GB RAM and 20GB disk
- Installed Ubuntu successfully

Installation Screenshot:  
![Step 1 - VM Created](screenshots/day1-install/step1-virtualbox-created.png)

### Basic Linux Navigation and Commands
- Practiced using:
  - `pwd`, `ls`, `cd`, `mkdir`, `touch`
- Explored important directories:
  - `/etc`, `/var`, `/home`
- Used `man` to read manual pages (e.g., `man ls`, `man grep`)

## Day 1 – Afternoon

### Linux Service Management
- Listed services with: `systemctl list-units --type=service`
- Started and stopped service: `cron`
- Verified service status using: `systemctl status cron`

Screenshot:  
![Service Management 1](screenshots/day1-install/step1-service-list1.png)  
![Service Management 2](screenshots/day1-install/step1-service-list2.png)  
![Service Management 3](screenshots/day1-install/step1-service-list3.png)

### Linux File Permissions
- Viewed file permissions using: `ls -l`
- Modified permissions with: `chmod +x`
- Changed ownership with: `chown`

Screenshot:  
![File Permissions](screenshots/day1-install/step2-permission-change.png)

### Searching Filesystem
- Used `find` to locate files
- Used `grep -r` to search file contents

Screenshot:  
![Find and Grep](screenshots/day1-install/step3-find-and-grep.png)

## Day 2 – Morning

### User and Group Management

- Created group `group1`
- Added users `student1`, `student2`
- Added both users to group1 using `usermod`
- Verified group memberships with `groups` and `/etc/group`
- Verified users exist via `/etc/passwd`

Screenshot:  
![Add Group and Users](screenshots/day2-morning/step1-ip-a.png)  
![Usermod Group1](screenshots/day2-morning/step2-ping.png)  
![Group Check](screenshots/day2-morning/step3-adduser.png)  
![Passwd File](screenshots/day2-morning/step4-passwd1.png)
![Passwd File](screenshots/day2-morning/step4-passwd2.png)
