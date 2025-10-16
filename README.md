# Git and Virtual Machines Seminar

A comprehensive guide covering Git version control, GitHub collaboration, Virtual Machines with VMware Workstation, and Linux fundamentals.

## 📚 Table of Contents

1. [Git and GitHub](#git-and-github)
2. [Virtual Machines](#virtual-machines)
3. [VMware Workstation](#vmware-workstation)
4. [Creating Your First Ubuntu VM](#creating-your-first-ubuntu-vm)
5. [Linux Fundamentals](#linux-fundamentals)
6. [VM Best Practices](#vm-best-practices)

---

## Git and GitHub

### What is Git?

Git is a distributed version control system that tracks changes in code files across your project. It works locally but can connect to remote servers for collaboration.

### Getting Started with Git

#### Installation
1. Visit [https://git-scm.com](https://git-scm.com)
2. Download the appropriate version for your OS (32-bit or 64-bit)
3. Run the installer and follow the setup wizard
4. Verify installation: Open terminal/cmd and type `git`

#### Basic Commands

```bash
# Initialize a repository
git init

# Check repository status
git status

# Stage files for commit
git add .
git add <filename>

# Commit changes
git commit -m "Your commit message"

# Push to remote repository
git push

# Pull latest changes
git pull

# Clone existing repository
git clone <URL>
```

#### Working with Branches

```bash
# Create new branch
git branch <branch_name>

# Switch branches
git checkout <branch_name>

# Merge branch into current branch
git merge <branch_name>
```

### GitHub Collaboration

GitHub is a cloud-based hosting service for Git repositories, enabling team collaboration and code sharing.

#### Adding Collaborators
1. Navigate to your repository on GitHub
2. Click on **Settings**
3. Select **Collaborators** from the left menu
4. Click **Add people**
5. Search by username or email
6. Collaborators will receive an email invitation to accept

---

## Virtual Machines

### What is a Virtual Machine?

A Virtual Machine (VM) is a software-based emulation of a physical computer that runs an operating system and applications as if it were a real computer, but exists as files on your host machine.

### The Virtualization Stack

| Layer | Component | Description |
|-------|-----------|-------------|
| 5 | Applications | Software running inside the VM |
| 4 | Guest OS | Operating system installed in the VM |
| 3 | Virtual Hardware | Emulated CPU, RAM, disk, network |
| 2 | Hypervisor | VMware, VirtualBox, Hyper-V |
| 1 | Host OS | Your computer's operating system |
| 0 | Physical Hardware | CPU, RAM, Storage, Network |

### Types of Hypervisors

**Type 1: Bare-Metal**
- Runs directly on hardware
- Examples: VMware ESXi, Microsoft Hyper-V Server
- Used in data centers and enterprise environments

**Type 2: Hosted**
- Runs on top of host OS
- Examples: VMware Workstation, VirtualBox
- Used for development, testing, personal use

### Benefits of Virtualization

- **Isolation**: VMs are completely separated from host
- **Portability**: VMs can be moved between hosts
- **Snapshots**: Save VM state at any point
- **Resource Efficiency**: Multiple VMs on one machine
- **Cost Savings**: Reduce hardware requirements

---

## VMware Workstation

### System Requirements

**Minimum Requirements for VMware Workstation 17:**
- **CPU**: 64-bit x86 Intel or AMD processor (1.3GHz+)
- **RAM**: 2GB minimum (4GB recommended, 8GB+ for multiple VMs)
- **Disk**: 1.2GB for application + space for VMs
- **OS**: Windows 10/11 or Ubuntu 20.04+
- **Important**: CPU must support virtualization (Intel VT-x or AMD-V)

### Installation Steps

1. Create a Broadcom account
2. Sign in to your account
3. Go to [VMware Workstation 17 Pro download page](https://www.vmware.com/products/workstation-pro/workstation-pro-evaluation.html)
4. Select your OS version
5. Choose the latest release
6. Accept Terms and Conditions
7. Download and run the installer
8. Select "Personal Use" when prompted

---

## Creating Your First Ubuntu VM

### Download Ubuntu ISO

1. Visit [Ubuntu website](https://ubuntu.com/download/desktop)
2. Download Ubuntu 24.04.3 LTS
3. Save the ISO file for VM installation

### Creating the VM

Follow the VMware Workstation wizard to create a new VM with the Ubuntu ISO. Recommended settings:
- **RAM**: 4GB minimum
- **Disk**: 20GB minimum
- **Network**: NAT for internet access

---

## Linux Fundamentals

### Essential Commands

#### Navigation
```bash
pwd                     # Print working directory
ls                      # List files
ls -la                  # List all files with details
cd /path/to/directory   # Change directory
cd ..                   # Go to parent directory
cd ~                    # Go to home directory
```

#### File Operations
```bash
# Create files and directories
mkdir folder_name       # Create directory
touch file.txt          # Create empty file
nano file.txt          # Edit file

# Copy, move, delete
cp source.txt dest.txt  # Copy file
cp -r source/ dest/     # Copy directory
mv old.txt new.txt      # Rename/move file
rm file.txt            # Delete file
rm -rf directory/       # Delete directory (use with caution!)
```

#### File Viewing and Searching
```bash
cat file.txt           # Display file content
less large_file.txt    # View with pagination
head -n 20 file.txt    # Show first 20 lines
tail file.txt          # Show last 10 lines
grep "pattern" file    # Search for pattern
find . -name "*.txt"   # Find files by name
```

#### Process Management
```bash
ps aux                 # List all processes
top                    # Interactive process viewer
kill PID              # Terminate process
killall process_name   # Kill by name
```

#### Package Management (Ubuntu/Debian)
```bash
sudo apt update        # Update package list
sudo apt upgrade       # Upgrade installed packages
sudo apt install package_name  # Install package
sudo apt remove package_name   # Remove package
```

---

## VM Best Practices

### Performance Optimization

✅ **Recommended Practices:**
- Allocate appropriate resources (not too much, not too little)
- Use SSD for VM storage when possible
- Install VMware Tools/Open VM Tools
- Enable hardware acceleration for graphics
- Use thin provisioning for disk space
- Disable unnecessary startup services
- Clean package cache regularly: `sudo apt clean`

### Snapshot Strategy

**When to Take Snapshots:**
- Before major system updates
- Before configuration changes
- After successful setup milestones
- Before experimenting with the system

**Best Practices:**
- Use descriptive names: "Pre-Apache-Install-2024-01-15"
- Add descriptions to snapshots
- Delete old snapshots to save space

### Virtual Networking Modes

| Mode | Description | Use Case |
|------|-------------|----------|
| NAT | VM shares host's IP | Internet access, no incoming connections |
| Bridged | VM gets own IP on network | Full network participation |
| Host-only | Private network with host | Isolated testing environment |
| Custom | Virtual switches | Complex network topologies |

---

## 🚨 Important Safety Tips

- **Be careful with `rm -rf`** - deleted files are gone forever
- Always use `ls` first to verify what you're about to delete
- Use `rm -i` for interactive confirmation
- **Never run `rm -rf /`** - this will destroy the entire system
- Take regular snapshots before making system changes
- Keep your VM tools updated for security and performance

---

## 📚 Additional Resources

- [Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [VMware Documentation](https://docs.vmware.com/)
- [Ubuntu Documentation](https://help.ubuntu.com/)
- [Linux Command Line Basics](https://linuxcommand.org/)

---

*Seminar by Lior Shilon*

