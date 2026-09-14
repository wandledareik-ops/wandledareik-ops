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
---

# Part 1 - Active Directory Infrastructure

## Building the Blue Valley Domain

The first phase of this project focused on building the Windows domain infrastructure that would later support the Help Desk scenarios.

Using Microsoft Azure, I created a virtualized environment containing a Windows Server domain controller and a Windows 11 client workstation.

During this phase of the project, I:

- Created and configured Azure virtual machines for the domain controller and client workstation.
- Configured the virtual network and DNS settings so the client could locate the domain controller.
- Installed Active Directory Domain Services (AD DS) on BV-DC01.
- Promoted BV-DC01 to a domain controller.
- Created the Blue Valley Windows domain.
- Created Organizational Units (OUs) to organize users and resources.
- Created domain user accounts for employees.
- Created security groups for managing access to company resources.
- Created an IT administrative account for domain administration.
- Joined BV-Client01 to the Blue Valley domain.
- Verified that domain users could successfully authenticate from the client workstation.

This infrastructure provided the foundation for the Help Desk troubleshooting scenarios performed during the second phase of the project.

### Key Skills Demonstrated

- Microsoft Azure virtual machines
- Windows Server administration
- Active Directory Domain Services
- DNS configuration
- Domain creation and administration
- Organizational Units
- User and group management
- Domain joining
- Windows authentication
- Basic PowerShell and command-line verification

### Active Directory Walkthrough

➡️ [View the complete Active Directory Infrastructure walkthrough](active-directory/README.md)
---

# Part 2 - Help Desk Ticketing Scenarios

## Simulating Real-World IT Support

After completing the Blue Valley domain environment, I used osTicket to simulate a Help Desk ticketing system and worked through three common IT support scenarios.

Each scenario followed a structured Help Desk workflow:

**Ticket Received → Investigate → Identify Root Cause → Implement Resolution → Verify Solution → Document Work → Close Ticket**

The purpose of these scenarios was to demonstrate not only how to perform technical tasks in Active Directory, but also how those skills are used within a ticket-based IT support environment.

### Ticket #1 - Sarah Johnson: Account Lockout

**Department:** Accounting  
**Issue:** Unable to log into Windows domain account

Sarah Johnson reported that she was unable to sign into her Windows account after multiple unsuccessful login attempts.

I investigated the domain account lockout policy, reproduced the issue, confirmed the account lockout in Active Directory, restored access to the account, and verified that Sarah could successfully authenticate to the Blue Valley domain.

**Skills demonstrated:**

- Account lockout troubleshooting
- Active Directory user administration
- Group Policy
- Domain authentication
- Account recovery
- Troubleshooting verification
- Help Desk ticket documentation

### Ticket #2 - Mike Davis: Shared Folder Access

**Department:** Accounting  
**Issue:** Unable to access the Accounting shared folder

Mike Davis could authenticate to the domain but received an access denied message when attempting to access the Accounting department's shared folder.

I verified that the shared resource was operational, investigated Mike's Active Directory security group memberships, identified the missing authorization, added Mike to the appropriate security group, refreshed his Windows authentication session, and verified successful access to the Accounting resource.

**Skills demonstrated:**

- Active Directory security groups
- Group-based access control
- NTFS permissions
- Windows share permissions
- UNC paths
- Windows security tokens
- `whoami /groups`
- Permission troubleshooting
- Help Desk documentation

### Ticket #3 - Emily Carter: New Employee Onboarding

**Department:** Accounting  
**Request:** Provision a new employee account and department access

A new employee onboarding request was submitted for Emily Carter.

I created Emily's domain account in the appropriate Organizational Unit, configured an initial temporary password and first-login password change requirement, assigned the appropriate Accounting security group, tested domain authentication, and verified access to the department's shared resources.

**Skills demonstrated:**

- Active Directory user creation
- Organizational Units
- User provisioning
- Password management
- Security group assignment
- Role-based access
- Domain authentication testing
- Employee onboarding
- Help Desk service request documentation

> **Detailed walkthrough coming next:** The Help Desk section of this repository will contain the screenshots, troubleshooting process, technical explanations, and ticket documentation for all three scenarios.
---

## Project Takeaways

This project provided hands-on experience with the relationship between infrastructure, identity management, access control, troubleshooting, and Help Desk ticket management.

Building the Blue Valley domain helped me understand how Active Directory and DNS provide centralized authentication and management within a Windows business environment.

The Help Desk scenarios demonstrated how technical knowledge is applied when supporting end users. Rather than immediately making changes when a user reported a problem, I practiced identifying symptoms, investigating possible causes, determining the root cause, implementing an appropriate solution, and verifying that the issue was resolved before closing the ticket.

The project also reinforced the importance of documenting troubleshooting steps and resolutions so that support activity can be understood by other IT professionals and referenced in the future.

---

## Repository Structure

This repository is organized into two primary technical walkthroughs:

1. **Active Directory Infrastructure** - Building and configuring the Blue Valley Windows domain environment.
2. **Help Desk Ticketing Scenarios** - Resolving three simulated IT support requests using osTicket and Active Directory.

Each walkthrough includes screenshots and explanations documenting both **how** the tasks were completed and **why** the configurations or troubleshooting steps were performed.
