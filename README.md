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



- Used `sudo -l` to list allowed sudo commands

Screenshot:  
![Sudo Privileges](screenshots/day2-afternoon/step3-sudo-check.png)
## Day 2 – Morning: TCO Analysis

### Total Cost of Ownership (TCO)

| Cost Item         | On-Premises (SGD) | Cloud (SGD/month) |
|-------------------|-------------------|-------------------|
| Server Hardware   | 4000              | -                 |
| Power & UPS       | 500               | -                 |
| Software License  | 1200              | Included          |
| Networking        | 100               | 100               |
| Cloud Services    | -                 | 30                |
| IT Maintenance    | 300               | 200               |

3-Year Total Cost:
- On-Premises: SGD 21,100
- Cloud: SGD 11,880

Break-even Point: approximately 81 months

Conclusion:  
Cloud deployment is more cost-effective in the short to medium term due to lower upfront investment and better scalability. On-premises solutions may only become economical after a significantly longer time period.

---

### Supporting Files and Visuals

- [TCO_Comparison.xlsx](./TCO_Comparison.xlsx)
- ![Cost Table](./tco-01-cost-table.png)
- ![3-Year Cost](./tco-02-total-3year-cost.png)
- ![Break-even Calculation](./tco-03-break-even.png)
- ![Analysis Summary](./tco-04-analysis-summary.png)
## Day 2 – Afternoon: Cloud Server & Automation Script

### EC2 Instance Configuration (AWS)
- Launched a t2.micro EC2 instance using Ubuntu 22.04 LTS
- Created and downloaded SSH key pair: `isea-key.pem`
- Opened ports for SSH (22), HTTP (80), HTTPS (443)
- Region: ap-southeast-2 (Singapore)

### SSH Access

```bash
chmod 400 isea-key.pem
ssh -i "isea-key.pem" ubuntu@<your-public-ip>
```

### Bash Script: `daily-log.sh`

```bash
#!/bin/bash
echo "==== Log at $(date) ====" >> /var/log/daily.log
df -h >> /var/log/daily.log
uptime >> /var/log/daily.log
```

### Cron Job

```bash
crontab -e
```

Add the following line to run the log script daily at 12:00 PM:

```cron
0 12 * * * /home/ubuntu/daily-log.sh
```

---

## Day 3 – DNS & HTTPS Setup + Server Automation

### DNS Setup

* Registered domain: `zytestdns.tk`
* Configured A record pointing to public IP
* Verified DNS using `dig zytestdns.tk` or `nslookup`

### SSL Certificate (Let's Encrypt)

* Installed Certbot:

  ```bash
  sudo apt update
  sudo apt install certbot python3-certbot-nginx -y
  ```

* Generated SSL certificate:

  ```bash
  sudo certbot --nginx -d zytestdns.tk
  ```

* Verified HTTPS access via browser: `https://zytestdns.tk`

---

## Server Automation (Update Script)

### Script: `update-server.sh`

```bash
#!/bin/bash
echo "==== Update Log at $(date) ====" >> /var/log/update.log
sudo apt update >> /var/log/update.log
sudo apt upgrade -y >> /var/log/update.log
```

### Cron Schedule

```bash
crontab -e
```

Add the following to schedule the update script at 2:00 AM daily:

```cron
0 2 * * * /home/ubuntu/update-server.sh
```

---

## Supporting Files and Screenshots

| Description                 | Suggested Filename       |
| --------------------------- | ------------------------ |
| SSH connection success      | `ssh-01-connect.png`     |
| daily-log.sh cron execution | `cron-01-daily-log.png`  |
| DNS dig result screenshot   | `dns-01-dig-result.png`  |
| Certbot installation steps  | `certbot-01-install.png` |
| HTTPS browser verification  | `https-01-verified.png`  |
| update-server.sh output log | `update-01-logs.png`     |

# ISEA Lab – Day 4: Final Project, Extra Service & Reflection

## Final Project Demonstration & Peer Feedback

This video demonstration includes:
- A walkthrough of all lab tasks from Day 1 to Day 3
- Explanation of key server configurations, automation scripts, and DNS/SSL setups
- Real-time preview of running services
- My personal insights and learning reflections
- Verbal response to peer feedback

 **Video Link**: [Insert OneDrive/YouTube/Stream URL]

##  Additional Server Service: MySQL Installation & Testing

As an extended learning task, I chose to install and configure **MySQL Server** on my Ubuntu instance.

###  Installation Steps
```bash
sudo apt update
sudo apt install mysql-server
sudo systemctl start mysql
sudo systemctl enable mysql
