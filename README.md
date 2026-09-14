# Blue Valley IT Help Desk Lab

## Project Overview

This project demonstrates the creation and administration of a simulated business IT environment for a fictional organization called **Blue Valley**.

I built a Windows domain environment using Microsoft Azure virtual machines, Windows Server, Active Directory Domain Services, DNS, and a Windows client workstation. I configured the domain environment, created and managed users and security groups, and joined a Windows client computer to the domain.

After building the Active Directory environment, I used **osTicket** to simulate a Help Desk ticketing system and worked through three realistic IT support scenarios involving account lockouts, resource permissions, Active Directory security groups, and new employee onboarding.

The goal of this project is to demonstrate hands-on experience with technologies and troubleshooting processes commonly used by entry-level IT Support and Help Desk professionals.
---

## Technologies Used

The following technologies and tools were used to build and manage the Blue Valley lab environment:

- **Microsoft Azure** - Hosted the virtual machines and virtual network used for the lab.
- **Windows Server** - Used for the Blue Valley domain controller.
- **Windows 11** - Used for the domain-joined client workstation.
- **Active Directory Domain Services (AD DS)** - Provided centralized user, computer, and domain management.
- **DNS** - Allowed domain clients to locate the domain controller and other domain services.
- **Group Policy** - Used to configure domain account policies, including account lockout settings.
- **Active Directory Users and Computers (ADUC)** - Used to manage users, groups, Organizational Units, and account settings.
- **PowerShell / Command Prompt** - Used to verify configurations, authentication, group memberships, and domain connectivity.
- **Remote Desktop Protocol (RDP)** - Used to remotely access and administer the Azure virtual machines.
- **Windows File Sharing and NTFS Permissions** - Used to create and control access to departmental shared resources.
- **osTicket** - Used to create, manage, document, and resolve simulated Help Desk tickets.
- **GitHub** - Used to document and present the completed project.
---

## Lab Environment

The Blue Valley lab was designed to simulate a small business Windows domain environment. The primary infrastructure consists of two virtual machines hosted in Microsoft Azure.

### BV-DC01 - Domain Controller

**BV-DC01** is the Windows Server virtual machine configured as the domain controller for the Blue Valley domain.

Its primary responsibilities include:

- Active Directory Domain Services
- DNS
- Domain user and group management
- Organizational Unit (OU) management
- Group Policy
- Authentication for domain users
- Management of departmental shared resources

### BV-Client01 - Domain Client

**BV-Client01** is a Windows 11 virtual machine joined to the Blue Valley domain.

This workstation was used to simulate an employee computer within the organization. It was used to:

- Test domain user authentication
- Reproduce Help Desk issues
- Verify Active Directory account changes
- Test security group memberships and permissions
- Access departmental shared folders
- Perform Remote Desktop testing
- Access and manage Help Desk tickets through osTicket

Together, BV-DC01 and BV-Client01 provided a controlled environment where I could practice both Active Directory administration and end-user Help Desk troubleshooting.
