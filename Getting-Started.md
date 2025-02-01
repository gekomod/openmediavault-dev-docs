---
title: Getting Started
description: 
published: 1
date: 2025-01-26T15:48:07.354Z
tags: 
editor: markdown
dateCreated: 2025-01-24T21:09:15.673Z
---

## Installation
1. **Download the ISO**:
- Download the latest openMediaVault 7 ISO from [official website](https://www.openmediavault.org/).

2. **Create a bootable media**:
- Use a tool like [Rufus](https://rufus.ie/) (Windows) or `dd` (Linux) to create a bootable USB drive.

3. **Install openMediaVault**:
- Connect the USB drive to the server and start it.
- Follow the installer instructions to install the system.

## Configuration
1. **Login to the administration panel**:
- After installation, open a browser and go to `http://server-ip-address`.
- Login using default credentials:
- Login: `admin`
- Password: `openmediavault`

2. **Network Configuration**:
- Go to `System -> Network -> Interfaces` to configure network interfaces.

3. **System Update**:
- Go to `System -> Update Management` to install latest updates.

## User Management
1. **Adding Users**:
- Go to `Access Rights Management -> Users` to add new users.

2. **Group Management**:
- Go to `Access Rights Management -> Groups` to manage user groups.

## Disk Management
1. **Adding Disks**:
- Go to `Storage -> Disks` to add and configure new disks.

2. **Creating File Systems**:
- Go to `Storage -> File Systems` to create new file systems (e.g. ext4, BTRFS).

3. **Share Folders**:
- Go to `Storage -> Shared Folders` to share folders on the network.

## Manage Services
1. **Enable Services**:
- Go to `Services` to enable and configure services such as SMB/CIFS, NFS, FTP, etc.

2. **Configure SMB/CIFS**:
- Go to `Services -> SMB/CIFS` to configure file sharing on Windows network.

3. **Configure NFS**:
- Go to `Services -> NFS` to configure file sharing on Linux network.

## Support and Help
- **Official Documentation**: [openMediaVault Documentation](https://docs.openmediavault.org/)
- **Support Forum**: [openMediaVault Forum](https://forum.openmediavault.org/)
- **GitHub**: [openMediaVault GitHub](https://github.com/openmediavault/openmediavault)