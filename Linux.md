## Linux Notes

Linux is an open-source OS kernel based on UNIX principles.
- UNIX is licensed and developed by AT&T Bell labs.
- Linux is open-source and community driven.
- Distributions like Ubuntu, CentOS, RHEL, Bebian are built on same kernel but differ in package management and User Interface (UI).

#### What is Linux Distro?
Ans: A linux distro is packaged version of linux kernel with software, libraries and tools.
- Ubuntu/Debain ---> APT package manager.
- CentOS/RHEL ---> YUM/DNF.
- SUSE ---> Zypper.

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

**Kernel** – Kernel is the core component of the Linux OS that acts as a bridge between software and hardware. It is the first program loaded into memory after system boot.

**Shell** – A program that interprets commands. Examples: bash, zsh, sh.

**System Libraries** – Interface between the kernel and applications.

**Terminal** – Interface used to access the shell (e.g., GNOME Terminal).

**Systemd** – It is the init system used to bootstrap the user space and manage services.

#### What are the challanges if we have different servers running on different OS Distros?
Ans: Using different Linux distributions increases complexity in package management, configuration management, patching, security, troubleshooting, and automation. It makes CI/CD pipelines and Ansible playbooks OS-specific, increases operational risk, and slows down incident response due to inconsistent system behavior.

#### Explain Linux architecture and its components
Ans: It is a layered structure with 4 major components.

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

#### Types of Kernels:

**- Monolithic Kernel:** All OS Servers (Process, Memory, I/O) run in one kernel space (Linux).

**- Micro Kernel:** Only essential services run in kernel space, rest of the services run in userspace (MINIX).

**- Hybrid Kernel:** It is a combination of both micro, monolithic kernels (Windows, Mac).

#### Kernel Space and User Space:
Ans: In Linux, memory is divided into two parts called Kernel Space and User Space to ensure system security and stability.

**- Kernel Space:** It is the core part of the OS where the kernel runs. It has full access to hardware and system resources. It handles critical tasks like process management, memory management, and device control.

**- User Space:** It is where normal user applications run (like browsers, editors). It has limited access and cannot directly interact with hardware. It communicates with the kernel using system calls.

**Conclusion:** Kernel space handles critical system operations with full access, while user space runs applications with restricted access for safety.

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


**- `ls -d */` command:** The `ls -d */` command is used to list only directories in the current location. Basically it is used to quickly view only directories without showing files.

**- `ls -R` command:** The `ls -R` command is used to list directories along with their contents recursively. It helps to view directories and all their contents in a recursive manner.

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

**→ `du -h --max-depth=1 / | sort -hr | head` Command**: This command is used to find the largest directories in the root (`/`) directory.

**→ `find /etc -type f -name "*.conf" -mtime -2` Command:** This command is used to find configuration files in the `/etc` directory that were modified in the last 2 days.

**→ `grep "connection refused" /var/log/app.log | tail` Command:** This command is used to find recent occurrences of the message "connection refused" in a log file.

**→ `find /var/log -type f -name "*.log" -exec du -sh {} + | sort -hr | head -n 10` Command:
Ans: This command is used to find the largest log files in the `/var/log` directory.
