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
