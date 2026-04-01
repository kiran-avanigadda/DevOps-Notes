## Linux Notes

Linux is an open-source OS kernel based on UNIX principles.
- UNIX is licensed and developed by AT&T Bell labs.
- Linux is open-source and community driven.
- Distributions like Ubuntu, CentOS, RHEL, Bebian are built on same kernel but differ in package management and User Interface (UI).

---

#### What is Linux Distro?
Ans: A linux distro is packaged version of linux kernel with software, libraries and tools.
- Ubuntu/Debain ---> APT package manager.
- CentOS/RHEL ---> YUM/DNF.
- SUSE ---> Zypper.

---

Commands to check the linux disro:
- cat /etc/os-release
- lsb_release -a
- uname -a
- uname -r ---> Gives kernel version.

File systems in Linux:
- /       - root.
- /bin    - essential binaries.
- /var    - variable data like logs.
- /etc    - config files.
- /usr    - user programs and utilities.

---

**Kernel** – Kernel is the core component of the Linux OS that acts as a bridge between software and hardware. It is the first program loaded into memory after system boot.

**Shell** – A program that interprets commands. Examples: bash, zsh, sh.

**System Libraries** – Interface between the kernel and applications.

**Terminal** – Interface used to access the shell (e.g., GNOME Terminal).

**Systemd** – It is the init system used to bootstrap the user space and manage services.

---

#### What are the challanges if we have different servers running on different OS Distros?
Ans: Using different Linux distributions increases complexity in package management, configuration management, patching, security, troubleshooting, and automation. It makes CI/CD pipelines and Ansible playbooks OS-specific, increases operational risk, and slows down incident response due to inconsistent system behavior.

#### Explain Linux architecture and its components
Ans: It is a layered structure with 4 major components.

---

**1. Hardware Layer:** 

- It Includes CPU, Memory, Disks etc..

**2. Kernel:** 
- It is the core component of the Linux OS that acts as a bridge between software and hardware.
- Manages CPU scheduling, memory management, process control, I/O operations, and device mangement.

**3. Shell:** 
- It is the command interpreter between user and kernel.
- It converts user commands into system calls understood by the kernel.

**4. Application Layer:** 
- It contains user utilities, applications, and tools like cat, vim etc..
- Uses system calls to communicate with kernel.

#### Describe the flow when user executes a command. (ex: ls, cd, pwd)
- Type 'ls' word in shell.
- Shell parses the command to find its binary --> /bin/ls.
- Shell sends a sys-call to kernel to execute it.
- From there on, Kernel loads the 'ls' binary to memory and executes it and interacts with the filesystem to the list.
- Finally, the operation is sent back to the kernel --> Shell --> Displays on the terminal.

---

#### Types of Kernels:

**- Monolithic Kernel:** All OS Servers (Process, Memory, I/O) run in one kernel space (Linux).

**- Micro Kernel:** Only essential services run in kernel space, rest of the services run in userspace (MINIX).

**- Hybrid Kernel:** It is a combination of both micro, monolithic kernels (Windows, Mac).

#### Kernel Space and User Space:
Ans: In Linux, memory is divided into two parts called Kernel Space and User Space to ensure system security and stability.

**- Kernel Space:** It is the core part of the OS where the kernel runs. It has full access to hardware and system resources. It handles critical tasks like process management, memory management, and device control.

**- User Space:** It is where normal user applications run (like browsers, editors). It has limited access and cannot directly interact with hardware. It communicates with the kernel using system calls.

---

#### Linux File System:
Ans: The Linux file system is the way Linux organizes and stores files on a disk. It follows a hierarchical structure that starts from the root directory /. Everything in Linux (files, directories, devices) is organized under this structure. It also manages how data is stored, retrieved and accessed efficiently and also handles permissions, security and disk space.

**- EXT4:** Most common, reliable.
**- XFS:** High Performance, Used in CentOS/RHEL.

#### Difference between EXT4 and XFS:
Ans: Ext4 and XFS are both journaling file systems used in Linux, but they differ in performance, scalability, and use cases.

**- EXT4:** Most common and widely used, stable and reliable, supports journaling, good for general-purpose use, easier to manage and repair.

**- XFS:** High performance file system, designed for large files and large storage, better for heavy workloads (databases, big data), faster with parallel operations, cannot shrink filesystem.

**Conclusion:** Ext4 is best for general use due to its stability and ease of management, while XFS is preferred for high-performance environments with large files and heavy workloads.

**- Ext4 (Fourth Extended File System):**

- It is the most commonly used and default file system in many Linux distributions.
- It is stable, reliable, and well-tested.
- Supports journaling (helps recover data after crashes).
- Good for general-purpose use like desktops and servers.
- Easier to manage and repair.

**- XFS:**

- Designed for high performance, especially with large files.
- Handles very large file systems and files efficiently.
- Better for heavy workloads like databases, big data, and media storage.
- Faster with parallel operations.
- Cannot shrink a filesystem once created (Ext4 can).

---

#### What is `strace ls`?:
Ans: `strace` is a Linux command used to trace system calls and signals made by a process. When we run `strace ls`, it shows all the system calls that the `ls` command makes while executing. It helps in debugging and understanding how a command interacts with the system.

#### Process Management in Linux:
Ans: Process management is handled by the Linux kernel, which controls how processes are created, scheduled, and terminated.

**- PID (Process ID):** Unique identifier assigned to each process.  
**- Scheduler:** Decides which process gets CPU time and manages execution order.  
**- System Calls (fork()):** Used to create a new process from an existing one.  
**- Process States:** Tracks different states of a process such as Running, Waiting, Stopped, and Zombie.

#### CLI vs GUI:
**- CLI:** Faster, Scriptable, Resource efficient.
**- GUI:** Used for local development, visualization.


| Parameter        | CLI (Command Line Interface)                  | GUI (Graphical User Interface)              |
|------------------|----------------------------------------------|---------------------------------------------|
| Interface        | Text-based commands                          | Visual interface with icons and windows     |
| Speed            | Faster for experienced users                 | Slower compared to CLI                      |
| Accessibility    | Requires command knowledge                   | Easy to use for beginners                   |
| Automation       | Supports scripting and automation            | Limited automation                          |
| Resource Usage   | Low resource consumption                     | High resource consumption                   |
| Common in        | Servers, DevOps, System Administration       | Desktops, End-user systems                  |

---

**- `ls -d */` command:** The `ls -d */` command is used to list only directories in the current location. Basically it is used to quickly view only directories without showing files.

**- `ls -R` command:** The `ls -R` command is used to list directories along with their contents recursively. It helps to view directories and all their contents in a recursive manner.

---

#### Useful Commands in Linux:
Ans: In Linux, the `tar` command is commonly used to compress and extract files and directories.

**→ tar -cvzf file.tar.gz:** Creates a compressed archive
**Ex:**  `tar -cvzf backup.tar.gz myfolder/`
- c → create archive  
- v → verbose (shows progress)  
- z → compress using gzip  
- f → specifies file name  

**→ tar -xvzf file.tar.gz:** Extracts a compressed archive
**Ex:**  `tar -xvzf backup.tar.gz`
- x → extract archive  
- v → verbose  
- z → decompress using gzip  
- f → specifies file name

**→ `rsync -avz /opt/logs user@remote:/backup/logs`:** This command is used to copy/sync the `/opt/logs` directory to a remote server.

---

**→ `du -h --max-depth=1 / | sort -hr | head` :** This command is used to find the largest directories in the root (`/`) directory.

**→ `find /etc -type f -name "*.conf" -mtime -2` :** This command is used to find configuration files in the `/etc` directory that were modified in the last 2 days.

**→ `grep "connection refused" /var/log/app.log | tail` :** This command is used to find recent occurrences of the message "connection refused" in a log file.

**→ `find /var/log -type f -name "*.log" -exec du -sh {} + | sort -hr | head -n 10` :** This command is used to find the 10 largest log files in the `/var/log` directory.

**→ `lsblk or fdisk -l` :** Commands to Check Attached Disks in Linux.

---

#### Difference Between grep and egrep:

| Feature        | grep                                  | egrep (grep -E)                         |
|----------------|----------------------------------------|----------------------------------------|
| Pattern Type   | Basic Regular Expressions (BRE)        | Extended Regular Expressions (ERE)     |
| Special Chars  | Limited support (need escape \| \+ ?)   | Supports \| + ? () without escape      |
| Ease of Use    | Slightly complex for patterns          | Easier for complex patterns            |
| Usage          | Simple searches                        | Advanced pattern matching              |

**Example:**

**→ grep:**  
`grep "cat\|dog" file.txt`  
(Searches for "cat" OR "dog" using escape)

**→ egrep:**  
`egrep "cat|dog" file.txt`  
(Searches for "cat" OR "dog" without escape)

---

#### Important Linux System Files:
Ans: These files store user, group, and authentication-related information in Linux.

**- /etc/passwd:** Stores user account information like username, UID, GID, home directory, and shell.  
**- /etc/shadow:** Stores encrypted passwords and password policies (secure, only root can access).  
**- /etc/group:** Contains group information like group name and group ID (GID).  
**- /etc/gshadow:** Stores secure group information including group passwords.

**Additional Important Files:**

**- /etc/sudoers:** Defines user permissions for sudo (administrative access).  
**- /etc/hosts:** Maps hostnames to IP addresses (local DNS).  
**- /etc/fstab:** Contains information about file systems and how they are mounted.  
**- /etc/os-release:** Provides OS details like version and distribution.

---

#### User Management Commands in Linux:

** sudo usermod -aG devops,admin,qa <username>:**  
Adds an existing user to multiple groups (devops, admin, qa).  
- -a → append (do not remove from existing groups)  
- -G → specify groups  


**→ sudo useradd -r -s /sbin/nologin <username>:**  
Creates a system user without login access.  
- -r → system account  
- -s /sbin/nologin → disables login shell  

**→ sudo usermod -aG sudo engineer:**  
Adds the user `engineer` to the sudo group (grants admin privileges).

---

#### Passwordless Authentication in Linux:
Ans: Passwordless authentication allows users to log in to a system without entering a password, usually using SSH keys.

**- How it works:**  
- A public and private key pair is generated  
- The public key is stored on the server  
- The private key remains with the user  
- During login, the system verifies the key instead of asking for a password  

**- Common Use:**  
Used in SSH login between servers for secure and automated access.

**- Benefits:**  
- More secure than passwords  
- Enables automation (scripts, deployments)  
- No need to remember passwords

---

#### Security Hardening in Linux:
Ans: Security hardening is the process of securing a Linux system by reducing vulnerabilities and minimizing attack surfaces.

**→ Best Practices:**
- Disable unnecessary services and ports  
- Apply regular security patches and updates  
- Use strong passwords and enable SSH key authentication  
- Configure firewall (iptables/firewalld)  
- Set proper file permissions and ownership  
- Disable root login via SSH  
- Enable logging and monitoring  

---

#### Service Not Restarting in Linux – Additional Checks:
Ans: Along with basic troubleshooting, we should also check system-level logs, hardware status, and mount points.

**- dmesg Logs:**  
`dmesg | tail`  
- Checks kernel messages for hardware or driver-related issues  

**- System Logs:**  
`/var/log/messages` or `/var/log/syslog`  
- General system errors and service-related issues  

**- Auth Logs:**  
`/var/log/auth.log` or `/var/log/secure`  
- Checks authentication or permission-related failures  

**- Mount Paths:**  
`df -h` and `mount`  
- Ensure required file systems are mounted and accessible  
- Service may fail if dependent mount is missing  

**- Hardware Issues:**  
- Check disk errors, CPU, memory issues  
- Use: `dmesg`, `smartctl`, `lscpu`, `free -m`

**- Application/Error Logs:**  
- Check service-specific logs (e.g., `/var/log/<service>/`)  
- Helps identify exact failure reason

---

#### Which Protocol Does `ping` command Use:
Ans: The `ping` command uses the ICMP (Internet Control Message Protocol).

**- ICMP:**  
- Used for sending echo request and echo reply messages  
- Helps check network connectivity between systems

---

#### Disk Full Error but `df -h` Shows Free Space:
Ans: This issue usually happens due to hidden disk usage, inode exhaustion, or deleted files still being used by processes.

**- Check Inodes Usage:**  
`df -i`  
- Disk may have free space but no inodes left  


**- Check Deleted Files Still in Use:**  
`lsof | grep deleted`  
- Files deleted but still held by running processes  
- Restart the process/service to release space  


**- Check Disk Usage Properly:**  
`du -sh /*`  
- Identify which directory is consuming space  


**- Check Mounted Filesystems:**  
`mount`  
- Verify correct mount points (sometimes data is written to wrong/unmounted path)  


**- Check Hidden Files:**  
`du -ah / | sort -hr | head`  
- Find large hidden files  


**- Check Logs:**  
- Large log files in `/var/log/`  
- Rotate or clean logs if needed  

**Resolution:**
- Clear unused files/logs  
- Restart services holding deleted files  
- Free up inodes if exhausted  
- Fix incorrect mount issues  

---

#### What are Inodes in Linux:
Ans: Inodes are data structures in Linux that store metadata about a file, but not the actual file content.

**→ What Inodes Store:**  
- File size  
- File permissions  
- Owner and group  
- Timestamps (created, modified, accessed)  
- Location of data blocks on disk

---

#### What is a file descriptor?
Ans: A file descriptor is a unique number assigned by the Linux kernel to identify an open file or resource.

**- What it represents:** It can represent files, sockets, pipes, or input/output streams  

**- Common File Descriptors:**  
- 0 → Standard Input (stdin)  
- 1 → Standard Output (stdout)  
- 2 → Standard Error (stderr) 

---

#### Other imp commands in Linux:

**→ `lsattr` :** List the attributes of the file/directory in linux.

**→ `netstat` :** Displayes n/w connections. It is replaced by `ss` command recently.

**→ `telnet` :** Tests connectivity on a remote host on a specific port.

**→ `apt-get` :** It is the legacy tool for package operations.

**→ `uname` :** Displayes system info like kernel version.

**→ `lscpu` :** Displayes the CPU architecture info.

**→ `iostat` :** Displayes CPU & IO stats.

**→ `renice` :** Changes the priority of a running process. Usage: renice -n <priority> -p <PID>

---
