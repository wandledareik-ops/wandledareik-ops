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
---

# Ticket #1 - Sarah Johnson: Account Lockout

## Ticket Summary

**User:** Sarah Johnson  
**Department:** Accounting  
**Ticket Type:** Incident  
**Reported Issue:** Unable to sign into the Windows domain account after multiple unsuccessful login attempts.

The objective of this ticket was to investigate Sarah's login failure, determine the root cause, restore access to her account, verify successful authentication, and document the resolution in osTicket.

---

## 1. Reviewing the Account Lockout Policy

Before reproducing the issue, I reviewed the existing domain account lockout policy.

Using the `net accounts` command, I found that the domain was originally configured with the following setting:

**Lockout threshold: Never**

![Original Account Lockout Policy](images/01-original-lockout-policy.png)

This meant that repeated incorrect password attempts would not automatically lock a user's domain account.

**Why this was important:**  
Because this was a lab environment, I needed to configure a realistic account lockout policy before I could reproduce and troubleshoot an account lockout scenario.

---

## 2. Configuring the Account Lockout Policy

Using Group Policy, I configured the domain account lockout policy so that an account would lock after **5 invalid login attempts**.

![Configuring Account Lockout Policy](images/02-configuring-lockout-policy.png)

After changing the policy, I refreshed Group Policy using:

`gpupdate /force`

This ensured that the updated policy settings were applied.

**Why this was important:**  
Account lockout policies help protect user accounts against repeated unauthorized password attempts. In a Help Desk environment, these policies can also result in support tickets when legitimate users repeatedly enter an incorrect password.

---

## 3. Reviewing the Help Desk Ticket

A Help Desk ticket was created in osTicket for Sarah Johnson after she reported that she was unable to sign into her domain account.

![Sarah Ticket Created](images/03-sarah-ticket-created.png)

Rather than immediately changing Sarah's password or account settings, I first attempted to reproduce and verify the reported problem.

**Troubleshooting approach:**  
The reported symptom was treated as the starting point of the investigation rather than assuming the cause of the problem.

---

## 4. Reproducing the Login Failure

I attempted to sign into the domain-joined BV-Client01 workstation using Sarah's domain account.

![Sarah Login Failure](images/04-sarah-login-failure.png)

The login attempt failed, confirming that the issue described in the ticket could be reproduced.

At this point, I knew that Sarah was experiencing an authentication problem, but additional investigation was required to determine why the authentication attempt was failing.

---

## 5. Identifying the Root Cause

I checked Sarah's account in **Active Directory Users and Computers (ADUC)** and confirmed that the account had been locked.

![Sarah Account Locked](images/05-sarah-account-locked.png)

The investigation identified the root cause:

> **Root Cause:** Sarah's domain account was locked after the number of unsuccessful login attempts exceeded the configured domain account lockout threshold.

This explained why Sarah could no longer authenticate even when attempting to use the correct credentials.

---

## 6. Resolving the Issue

Because Sarah's existing password was still valid, I unlocked the account in Active Directory rather than performing an unnecessary password reset.

This was the least disruptive solution because the problem was the account's locked status rather than an unknown or expired password.

After unlocking the account, I returned to BV-Client01 and tested Sarah's account again.

The login was successful, and I verified that the authenticated account was:

`bluevalley\sjohnson`

**Resolution:**  
Sarah's Active Directory account was unlocked and access was restored without changing her existing password.

---

## 7. Verification and Ticket Closure

After confirming that Sarah could successfully authenticate to the Blue Valley domain, I documented the troubleshooting process and resolution in osTicket and closed the ticket.

![Sarah Ticket Closed](images/06-sarah-ticket-closed.png)

The ticket was only considered resolved after successful login was verified from the user's workstation.

### Final Resolution

- Confirmed the account was locked in Active Directory.
- Unlocked Sarah's domain account.
- Kept the existing password because a reset was not required.
- Successfully authenticated from BV-Client01.
- Verified the domain identity as `bluevalley\sjohnson`.
- Documented the resolution in osTicket.
- Closed the ticket after successful verification.

---

## Ticket #1 - Skills Demonstrated

This ticket demonstrated hands-on experience with:

- Active Directory user account administration
- Account lockout troubleshooting
- Domain account lockout policies
- Group Policy
- `net accounts`
- `gpupdate /force`
- Active Directory Users and Computers
- Windows domain authentication
- Root cause analysis
- Least-disruptive remediation
- Post-resolution verification
- Help Desk ticket documentation
- Incident resolution

### Key Takeaway

This scenario reinforced the importance of diagnosing the actual cause of a user's problem before making changes.

Although a password reset might initially appear to be an appropriate response to a login problem, the investigation showed that Sarah's password was not the root cause. The account itself was locked.

By identifying the root cause first, I was able to restore access with the least disruptive solution and verify that the issue was resolved before closing the ticket.
