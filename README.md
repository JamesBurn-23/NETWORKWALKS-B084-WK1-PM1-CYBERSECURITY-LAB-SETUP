# Virtual Cybersecurity Lab Setup – Kali Linux & Oracle VirtualBox

## Table of Contents

- [Project Overview](#project-overview)
- [Project Objectives](#project-objectives)
- [Tools and Technologies](#tools-and-technologies)
- [Lab Configuration](#lab-configuration)
- [Lab Setup Procedure](#lab-setup-procedure)
- [Network Connectivity Verification](#network-connectivity-verification)
- [Shared Folder Verification](#shared-folder-verification)
- [Problems Encountered and Solutions](#problems-encountered-and-solutions)
- [What I Learned](#what-i-learned)
- [References](#references)

---

## Project Overview

This project focuses on establishing a virtual cybersecurity lab environment using Oracle VirtualBox and Kali Linux.

The objective is to configure Kali Linux as the attacking machine within a virtual network, providing an isolated environment for cybersecurity testing and practical penetration testing exercises.

This documentation covers the installation and configuration process, including virtual machine resource allocation, network configuration, shared folder integration, and connectivity testing.

Screenshots are included throughout the documentation to demonstrate the different stages of the setup and verify the completed configurations.

## Project Objectives

The following objectives define the scope of this project:

- Install and configure Oracle VirtualBox.
- Deploy Kali Linux as the attacking machine.
- Create a NAT Network using the `10.0.0.0/24` subnet.
- Assign Kali Linux the static IP address `10.0.0.2/24`.
- Enable bidirectional shared clipboard and drag-and-drop functionality.
- Configure a shared folder between the Windows host and Kali Linux using the host's Downloads folder.
- Ensure Kali Linux has internet connectivity.
- Verify network connectivity and shared folder functionality.
- Document the complete setup and configuration process.

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Oracle VirtualBox | Virtualisation platform for managing virtual machines |
| Kali Linux | Linux distribution used for cybersecurity testing |
| NAT Network | Provides network connectivity between virtual machines and external networks |
| Linux networking tools | Used for network configuration, connectivity testing, and troubleshooting |

## Lab Configuration

The following table outlines the hardware and network configurations used in this lab.

| Component | Configuration |
|---|---|
| Host Operating System | Windows 11 |
| Hypervisor | Oracle VirtualBox |
| Security Operating System | Kali Linux |
| Allocated RAM | 4000 MB |
| Virtual CPUs | 4 |
| Video Memory | 128 MB |
| Virtual Network | NAT Network |
| Network Name | NatNetwork |
| Network Address | `10.0.0.0/24` |
| Kali Linux IP Address | `10.0.0.2/24` |
| Default Gateway | `10.0.0.1` |
| DNS Server | `8.8.8.8` |
| Shared Folder | Downloads |
| Shared Clipboard | Bidirectional |
| Drag and Drop | Bidirectional |

## Lab Setup Procedure

This section documents the installation and initial configuration of the virtual cybersecurity lab.

### 1. Downloading Kali Linux
Downloaded the pre-built Kali Linux virtual machine from the official Kali Linux website.

**Screenshot 1 – Kali Linux Pre-built Virtual Machine Download Page**
![Kali Linux Download Page](Lab_Setup/Screenshot_1.png)


### 2. Opened VirtualBox
VirtualBox was already installed in my computer, kindly ignore the Kali Linux virtual machine, it was from a previous project.

**Screenshot 2 – Oracle VirtualBox**
![Imported Kali Linux VM](Lab_Setup/Screenshot_2.png)


### 3. Import of the pre-built kali linux
I added the new kali linux for the purpose of pentesting, cybersecurity, and testing.

**Screenshot 3 – Oracle VirtualBox**
![Imported Kali Linux VM](Lab_Setup/Screenshot_3.png)


### 4. Created the NAT Network
Created a NAT Network in Oracle VirtualBox using the `10.0.0.0/24` subnet and named it as "NatNetwork.

**Screenshot 4 – Oracle VirtualBox**
![Imported Kali Linux VM](Lab_Setup/Screenshot_4.png)



### 5. Configuring Virtual Machine Resources
Configured the virtual machine's hardware resources to ensure sufficient performance.

**Screenshot 4 – Base Memory Configuration**
![RAM Configuration](Lab_Setup/Screenshot_5.png)

**Screenshot 5 – Processor Configuration**
![CPU Configuration](Lab_Setup/Screenshot_6.png)

**Screenshot 6 – Video Memory Configuration**
![Video Memory Configuration](Lab_Setup/Screenshot_7.png)


### 6. Configuring Network Settings
I configured the Kali Linux virtual machine to use the NAT network (NatNetwork).

**Screenshot 7 – Virtual Machine Network Adapter Configuration**
![Network Adapter Configuration](Lab_Setup/Screenshot_8.png)


### 7. Configuring Shared Folders
Configured a shared folder between the Windows host and Kali Linux, using the Windows Downloads directory.

**Screenshot 9 – Shared Folder Configuration**
![Shared Folder Configuration](Lab_Setup/Screenshot_9.png)



### 10. Booting Kali Linux
Successfully started the Kali Linux virtual machine after completing the initial configuration.

**Screenshot 10 – Successful Kali Linux Boot**
![Kali Linux Boot](Lab_Setup/Screenshot_10.png)

### 11. Configuring Static IPv4 Settings

Manually configured the IPv4 network settings in Kali Linux with the following values:

- IP Address: `10.0.0.2`
- Netmask: `255.255.255.0`
- Gateway: `10.0.0.1`
- DNS Server: `8.8.8.8`

**Screenshot 11 – Manual IPv4 Configuration**
![IPv4 Configuration](Lab_Setup/Screenshot_11.png)

---

## Network Connectivity Verification

After completing the network configuration, several commands and tests were performed to verify that the virtual machine was communicating correctly with the network.

The following requirements were tested:

1. Kali Linux has the correct IP address (`10.0.0.2/24`).
2. The default gateway (`10.0.0.1`) is reachable.
3. External internet connectivity is working.
4. DNS resolution is working correctly.

### 1. Verify the Assigned IP Address

Used the following command to inspect the network interfaces and verify the assigned IP address.

```bash
ip a
```

**Evidence:** Screenshot showing the command output and the assigned IP address.
![IP Address Verification](Network_Verification/Screenshot_12.png)


### 2. Verify the Default Gateway
Used the following command to inspect the routing table and identify the configured default gateway.

```bash
ip route
```

**Evidence:** Screenshot showing the routing table and default gateway.
![Default Gateway Verification](Network_Verification/Screenshot_13.png)


### 3. Test Gateway Connectivity
Used `ping` to verify communication between Kali Linux and its default gateway.

```bash
ping 10.0.0.1
```

**Evidence:** Screenshot showing the ping results.
![Gateway Connectivity Test](Network_Verification/Screenshot_14.png)

### 4. Test External Internet Connectivity
Tested connectivity to Google's public DNS server using its IP address.

```bash
ping 8.8.8.8
```

**Evidence:** Screenshot showing successful external connectivity.
![Internet Connectivity Test](Network_Verification/Screenshot_15.png)


### 5. Test DNS Resolution
Used `nslookup` to verify that domain names could be resolved into IP addresses.

```bash
nslookup google.com
```

**Evidence:** Screenshot showing the DNS lookup results.
![DNS Resolution Test](Network_Verification/Screenshot_16.png)


### 6. Verify Internet Access Through the Browser
Finally, I opened YouTube through the Kali Linux browser to visually confirm that internet access was functioning.

![Kali Linux Internet Access](Network_Verification/Screenshot_17.png)

---

## Shared Folder Verification
To verify that the shared folder was working correctly, I created a test folder inside the Windows Downloads directory.

The folder was named:

`If you see this folder, that means that it worked!`

This folder was used as a simple way to confirm that files created on the Windows host could be accessed from Kali Linux.

### 1. Windows Downloads Folder

The following screenshot shows the test folder created inside the Windows Downloads directory.

![Windows Downloads Folder](Shared_Folder_Verification/Screenshot_18.png)

### 2. Accessing the Shared Folder in Kali Linux

Verified that the shared folder was accessible from within Kali Linux using the terminal.

![Kali Linux Shared Folder](Shared_Folder_Verification/Screenshot_19.png)

### 3. Comparing Windows and Kali Linux

The following screenshot provides a side-by-side comparison of the Windows Downloads folder and the corresponding shared folder accessed through Kali Linux.

![Shared Folder Comparison](Shared_Folder_Verification/Screenshot_20.png)

---

## Problems Encountered and Solutions

The majority of the setup process went smoothly. However, I encountered an issue while configuring the network connection in Kali Linux.

After manually configuring the IPv4 settings, the virtual machine was unable to access the internet. Websites would not load through the browser.

### Solution

To troubleshoot the issue, I used NetworkManager's command-line utility (`nmcli`) to modify the IPv4 Duplicate Address Detection (DAD) timeout and restart the network connection.

The following commands were executed:

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0

sudo nmcli connection down "Wired connection 1"

sudo nmcli connection up "Wired connection 1"
```

### Command Explanation

| Command / Parameter | Explanation |
|---|---|
| `sudo` | Executes the command with administrator privileges. |
| `nmcli` | NetworkManager's command-line utility. |
| `connection modify` | Modifies an existing network connection profile. |
| `ipv4.dad-timeout 0` | Sets the IPv4 Duplicate Address Detection timeout to zero. |
| `connection down` | Deactivates the specified network connection. |
| `connection up` | Reactivates the network connection using its configured settings. |

### Result

After executing the commands, network connectivity was restored, and I was able to access websites through the Kali Linux browser.

This resolved the connectivity issue and allowed me to continue with the remaining configuration and verification steps.

---

## What I Learned

Completing this project gave me practical experience in building and configuring a virtual cybersecurity lab environment.

Some of the key things I learned include:

**Virtualisation**

Gained practical experience using Oracle VirtualBox to deploy, configure, and manage a Kali Linux virtual machine.

**Network Configuration**

Learned how to create and configure a NAT Network, assign a static IPv4 address, and configure the default gateway and DNS settings.

**Linux Networking**

Became more familiar with Linux networking commands such as `ip a`, `ip route`, `ping`, and `nslookup` to inspect and troubleshoot network connectivity.

**Network Troubleshooting**

Gained experience identifying and resolving a network connectivity issue using NetworkManager commands.

**Host and Virtual Machine Integration**

Learned how to configure shared folders, shared clipboard functionality, and drag-and-drop between a Windows host and a Kali Linux virtual machine.

**Technical Documentation**

Improved my ability to document technical configurations, troubleshooting steps, and verification results using screenshots.

Most importantly, this project helped me understand how different components of a virtual lab environment work together. It also provided a foundation for future practical exercises involving penetration testing and cybersecurity assessments.

---

## References

The following official resources were used during the setup process:

1. [Kali Linux – Official Download Page](https://www.kali.org/get-kali/#kali-platforms)
2. [Oracle VirtualBox – Official Downloads](https://www.virtualbox.org/wiki/Downloads)

---

**Project Status:** Completed

**Environment:** Windows 11 | Oracle VirtualBox | Kali Linux
