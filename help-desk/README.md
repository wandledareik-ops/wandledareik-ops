[← Back to Main Project](../README.md)

# Blue Valley Help Desk Ticketing Lab

## Overview

This section documents the Help Desk portion of the **Blue Valley IT Help Desk Lab**.

After building the Active Directory domain environment, I used **osTicket** to simulate a ticket-based IT support workflow. I created and resolved realistic support requests involving Windows domain accounts, Active Directory, security groups, shared-folder permissions, and employee onboarding.

The purpose of these scenarios was to practice both the technical and procedural sides of IT support. Each ticket required investigating the user's issue, identifying the root cause, implementing an appropriate solution, verifying the result, documenting the work performed, and closing the ticket.

The Help Desk environment used the Active Directory infrastructure created during the first part of this project:

- **BV-DC01** - Windows Server domain controller providing Active Directory and DNS services.
- **BV-Client01** - Windows 11 domain-joined workstation used to reproduce and verify user issues.
- **osTicket** - Ticketing system used to document, track, and resolve support requests.

[View the Active Directory Infrastructure Walkthrough](../active-directory/README.md)

---

## Help Desk Troubleshooting Workflow

Throughout the project, I followed a structured troubleshooting process:

1. **Receive and review the ticket**
2. **Reproduce or verify the reported issue**
3. **Gather information and investigate the cause**
4. **Identify the root cause**
5. **Implement an appropriate resolution**
6. **Verify that the solution worked**
7. **Document the troubleshooting process and resolution**
8. **Close the ticket**

This process helped ensure that issues were not considered resolved simply because a configuration change was made. The final result was tested from the user's perspective before the ticket was closed.

---

## Ticket Scenarios

Three Help Desk scenarios were completed using the Blue Valley lab environment.

### Ticket #1 - Sarah Johnson: Account Lockout

**Department:** Accounting  
**Ticket Type:** Incident  
**Issue:** Unable to sign into the Windows domain account after multiple unsuccessful login attempts.

This scenario demonstrates Active Directory account troubleshooting, account lockout policy, Group Policy, account recovery, and verification of domain authentication.

### Ticket #2 - Mike Davis: Accounting Shared Folder Access

**Department:** Accounting  
**Ticket Type:** Incident  
**Issue:** Able to sign into the domain but receives an access denied message when attempting to access the Accounting shared folder.

This scenario demonstrates Active Directory security groups, authorization, Windows share and NTFS permissions, security token refresh, and permission troubleshooting.

### Ticket #3 - Emily Carter: New Employee Onboarding

**Department:** Accounting  
**Ticket Type:** Service Request  
**Request:** Create and configure a new domain account for an Accounting employee.

This scenario demonstrates Active Directory user provisioning, Organizational Unit placement, password configuration, security group assignment, domain authentication, and verification of resource access.
