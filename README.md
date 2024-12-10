## **Linux Server Automation**

### **Overview**
This project automates routine system administration tasks on a Linux server to improve efficiency, ensure consistent performance, and minimize manual intervention. Tasks include automating system updates, cleaning up logs, and scheduling backups, all managed through Bash scripts and cron jobs.

### **Features**
- **System Updates**:
  - Automatically checks for and installs updates for system packages to maintain security and stability.
- **Log Management**:
  - Scheduled cleanup of outdated logs to optimize disk usage and prevent clutter.
- **Automated Backups**:
  - Configured backup scripts to secure important data with versioning and scheduled transfers to remote storage.

### **Tools & Technologies**
- **Bash**: Used to write scripts for automating tasks.
- **Cron**: Linux-based job scheduler to run scripts at predefined intervals.

### **Installation & Setup**
#### **1. Clone the Repository**
```bash
git clone https://github.com/yourusername/linux-server-automation.git
cd linux-server-automation
```

#### **2. Configure the Scripts**
- Update `backup.sh`, `update.sh`, and `log_cleanup.sh` scripts with specific directories, commands, and remote storage configurations.
- Example of `backup.sh`:
  ```bash
  tar -czvf /backup/mydata-$(date +%F).tar.gz /home/user/data
  rsync -avz /backup remoteuser@remotehost:/remote-backup
  ```

#### **3. Schedule Cron Jobs**
- Open the cron table:
  ```bash
  crontab -e
  ```
- Add entries to schedule tasks. Example:
  - Daily updates at 2 AM:
    ```bash
    0 2 * * * /path/to/update.sh
    ```
  - Weekly log cleanup:
    ```bash
    0 3 * * 1 /path/to/log_cleanup.sh
    ```

### **Usage**
- Run scripts manually to verify functionality:
  ```bash
  bash update.sh
  bash log_cleanup.sh
  bash backup.sh
  ```
- Use `systemctl status cron` to ensure the cron service is running.
