# Evaluation of Windows 10 and CentOS 7 according to the Security Technical Implementation Guide
---

Upon request from Investor Inc., I went through the systems of Windows 10 and CentOS 7 to evaluate the controls that were in place or missing from the systems. During this evaluation, it was noticed that multiple security implementations were not in place which could lead to extreme vulnerabilites on the machines. Throughout this evaluation, I noted missing Security Technical Implemenatation as well as implemnted vital ones to ensure the safety of the systems. Below is the outome from the evaluation with the process that was taken and my recommendations.

---

## Executive Summary
The purpose of this evaluation was to analyze the Windows 10 and CentOS 7 systems that Investor Inc. utilizes to ensure NIST standards were met through comparison with the Security Technical Implementation Guide (STIG). This was accomplished by comparing the systems to the STIG checklists by using the STIG viewer tool to compare and fix missing best practices or help reduce vulnerabilities. The STIG checklists, as I will display later, allowed me to record changes, finds, and recommendations I came across as I was evaluating the systems. Any recommendations that are still open are marked by the status of `Open` and ones that were fixed or properly implemented were marked as `Not a Finding`. Overall, I recommend that the systems continue to be updated due to the multitude of finds that still exist on the systems.

---

## Introduction
I am evaluating Windows 10 and CentOS 7 for Investor Inc. to provide recommendations of steps to take to ensure known vulnerabilities and security concerns are addressed. The system I am using to evaluate this is STIG (Security Technical Implementation Guide) and the checklists for each system respectively. These checklists allow me to ensure that the systems meet the recommended security compliances and allow me to fix known security concernse and vulnerabilities. These security flaws and vulnerabilities are all based off of known NIST recommendations. Through utilizing Virtual Machines on VirtualBox, along with STIG Viewer, I evaluated both Windows 10 and CentOS 7 for compliance with different NIST recommendations. The Virtual Machines allowed me to ensure testing was in a controlled environment and no harm was done to any real machines.

---

## Background of Practitioner
My background as a Cyber Security Practitioner comes from my education of programming and networking throughout my time in high school. From there I worked on cloud development as a Software Engineer Intern for IBM for 2 years. I worked with a multitude of languages and tools from virtual machines to Docker to languages such as Python, Java, C++, and Swift. I continued to develop my Cyber Security education at the United States Coast Guard Academy where I continued to practice and expand my knowledge of programming and networking. I expanded into Cyber Security over my studies which have given me the ability to learn how to analyze and evaluate systems for vulnerabilities and good cyber practices.

---

## Method
To accomplish this evaluation the following tools were used:
* STIGViewer - STIGViewer was used to track and manage the Windows 10 and the CentOS 7 Checklists as the evaluation was taking place. As different controls were being examined, they would be tracked as either "Open" when there was a finding and finding details were added, or as "Not a Finding" if the system already had the controls integrated. 
* Windows 10 VM (Matches the version on all Windows 10 machines in the organization) - The Windows 10 VM was the same version that all the other Windows 10 machines were running allowing me to examine the controls that were in place on the actual machines without risking and compromising an actual machine.
* CentOS 7 VM (Matches the version on all Windows 10 machines in the organization) - The CentOS 7 VM was the same version that all the other CentOS 7 machines were running allowing me to examine the controls that were in place on the actual machines without risking and compromising an actual machine.
* Vagrant - Vagrant was used to manage and deploy the virtual machines through VirtualBox. This allowed for the creating and enabling of multiple virtual machines ensuring they had the same configuration. Everytime the machine was created, the version would be of the same configuration as the ones before. This allowed for a repeatable process, ensuring that the systems were properly configured. The evaluation can be repeated easily and with confidence. The machines that were examined matched a version that was on Vagrant Cloud.
* VirtualBox - VirtualBox was the Hypervisor of choice to be used with Vagrant. VirtualBox allowed me to created desktop virtualization to utilize the GUI as a regular user would see it. I was able to easily access and confirm the controls on the systems as well as implement changes to ensure that the corrections could be implemented to fix findings. 

---

## Assumptions
During the evaluation of the Windows 10 and CentOS 7 systems, the assumpthin that all the machines had the exact same environment was made. It is assumed that the organization has the same image file for the operating systems and that a new image could be created with the controls and findings corrected. This would allow for the organization to push the changes out to every machine. The assumption was made that the versions of Windows 10 and CentOS 7 were up-to-date and had the latest patches installed. Furthermore, it was assumed that the STIG checklists that were utilized were the most recent and up-to-date with the latest known controls and vulnerabilites that should be addressed. These assumptions assured that the tests were accurate and fixes could be applied to all machines. It also allowed for the proper testing of one virtual machine to check all the machines that the company may have employees using.

---

## Summary of Actions Taken (Identification of Controls Assessed

To create the test environment for the evaluation, I utilized Vagrant to create environments of Windows 10 and CentOS 7. Utilizing Vagrant allowed me to create the exact same version of a Virtual Machine each time for consistant and repeatable evaluations and testing. I used Vagrant with the Hypervisor VirtualBox to actually run the Virtual Machines. I then set up the STIG Viewer with a checklist for Windows 10 and a checklist for CentOS 7. I then began working on testing and evaluating the machines.

For Windows 10, I identified controls to evaluate and when through the process of confirming if they were findings or not. If there was a finding, I would note what was found and then would continue through the steps to fix the finding. I would then state what setting I implemented in the comments to ensure that it was documented and the result was understood. The final result would be a commented control labeled as "Not a Finding". When a finding was located and was not fixed, it would marked as "Open" and I would put finding details to note what was wrong with it and what had to be fixed. The processes to verify and fix the controls through the settings, Windows\System32 directory, gpedit.msc, and the local computer policy for the main ones. The settings in these areas were changed and sometimes Powershell was used to fix the findings. The steps on each control were followed to make an evaluation.

For CentOS 7, I also identified controls in the same manner as Windows 10 for marking and documenting controls. I also marked open findings as "Open" to ensure further review, and for the controls that were not a finding or were fixed were marked as "Not a Finding" when they were completed. To evaluate, I worked inside the terminal for inspecting the controls as well as editing the files to fix the settings. `Grep` was used to find and get the value of the settings that were being evaluated. I then used `Vim` and `Nano` to edit the files and edit the values of the settings to fix the findings.

### Windows 10 System
#### Controls Evaluated - Resulted in "Not a Finding":
* V-220697 - Ensure that the Edition of Windows is "Windows 10 Enterprise" Found in "Settings" under "System", then "About".  
* V-220708 - Ensure that the File System is using "NTFS" for each volume. Run `Computer Management` and navigate to storage and Disk Management to check
* V-220709 - Alternate operating systems must not be permitted.
* V-220743 - The maximum password age must be configured to 60 dyas or less. This was set to 42 days by default in the Local Computer Policy navigation to Password Policy.

#### Controls Evaluated - Resulted in "Finding" and corrected:
* V-220699 - Windows 10 systems must have Unified Extensible Firmware Interface (UEFI) firmware and be configured to run in UEFI mode, not Legacy BIOS. Changed the BIOS boot mode to UEFI in the BIOS upon boot. To demonstrate it worked on the VM, the settings for the motherboard was changed inside the VirtualBox settings.)
* V-220740 - The number of allowed bad logon attempts must be configured to 3 or less. Utilizing gpedit.msc and navigating Local Computer Policy >> Computer Configuration >> Windows Settings >> Security Settings >> Account Policies >> Account Lockout Policy, I changed the lockout threshold from 0 to 1.
*  V-220741 - The period of time before the bad logon counter is reset must be configured to 15 minutes. Utilizing gpedit.msc and navigating Local Computer Policy >> Computer Configuration >> Windows Settings >> Security Settings >> Account Policies >> Account Lockout Policy, I changed the lockout counter from 0 to 30 minutes.
*  V-220742 - The password history must be configured to 24 passwords remembered. Utilizing gpedit.msc and navigating Local Computer Policy >> Computer Configuration >> Windows Settings >> Security Settings >> Account Policies >> Password Policy I changed the enforce password history from 0 to 24 passwords remembered.
*  V-220744 - The minimum password age must be configured to at least 1 day. Utilizing gpedit.msc and navigating Local Computer Policy >> Computer Configuration >> Windows Settings >> Security Settings >> Account Policies >> Password Policy I changed the minimum password age from 0 to 1 day.
*  V-220744 - Passwords must, at a minimum, be 14 characters. Utilizing gpedit.msc and navigating Local Computer Policy >> Computer Configuration >> Windows Settings >> Security Settings >> Account Policies >> Password Policy I changed the minimum password length from 0 characters to 14 characters.
*  V-220856 - Users must be prevented from changing installation options. Utilizing the registry, I navigated to HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Installer\ to check if the vaule name was enabled. To correct this, I changed the policy value by navigating to Computer Configuration >> Administrative Templates >> Windows Components >> Windows Installer >> "Allow user control over installs" and set it to disabled.

#### Controls Evaluated - Resulted in "Finding" and left "Open" or N/A:
* V-220716 - Accounts must be configured to require password expiration. Both accounts on the system had passwords that would never expire.
* V-220734 - Bluetooth must be turned off unless approved by the organization. This was N/A because the devices in the organization do not have bluetooth as an option.

**Image Demonstration**

Unfixed Control

![alt text](/Lab2/Screenshots/WindowsScreenshotFixed_V220741.png "Unfixed Finding")

Fixed Control

![alt text](/Lab2/Screenshots/WindowsScreenshot_V-220856.png "Fixed Finding")

---

### CentOS 7 System

#### Controls Evaluated - Resulted in "Not a Finding":
* V-204425 - The Red Hat Enterprise Linux operating system must be configured so that the SSH daemon does not allow authentication using an empty password. The value is set to "no" as required so an empty password can not be used for SSH authentication

#### Controls Evaluated - Resulted in "Finding" and corrected:
* V-204410 - The Red Hat Enterprise Linux operating system must be configured so that when passwords are changed or new passwords are established, the new password must contain at least one special character. To correct this, I changed the file "/etc/security/pwquality.conf" by altering the line 'ocredit = 1' changed from 1 to -1. 
* V-204411 - The Red Hat Enterprise Linux operating system must be configured so that when passwords are changed a minimum of eight of the total number of characters must be changed. To correct this, I changed the value of difok to 8 in the file "/etc/security/pwquality.conf".
* V-204412 - The Red Hat Enterprise Linux operating system must be configured so that when passwords are changed a minimum of four character classes must be changed. To correct this, I corrected the file "/etc/security/pwquality.conf" by changing the minclass to 4.
* V-204413 - The Red Hat Enterprise Linux operating system must be configured so that when passwords are changed the number of repeating consecutive characters must not be more than three characters. To correct this finding, I altered the file "/etc/security/pwquality.conf and changed the value of maxrepeat to 3.
* V-204420 - The Red Hat Enterprise Linux operating system must be configured so that passwords for new users are restricted to a 60-day maximum lifetime. To correct this finding, I edited the file "/etc/ligin.defs and changed the value of PASS_MAX_DAYS to 60.
* V-204423 - The Red Hat Enterprise Linux operating system must be configured so that passwords are a minimum of 15 characters in length. To correct this finding, I altered the file "/etc/security/pwquality.conf and changed the value of minlen to 15.
* V-204426 - The Red Hat Enterprise Linux operating system must disable account identifiers (individuals, groups, roles, and devices) if the password expires. To correct this finding, I altered the file /etc/default/useradd and changed the value of INACTIVE to 35.
* V-204442 - The Red Hat Enterprise Linux operating system must not have the rsh-server package installed. To correct this finding, I ran the command `sudo apt-get remove rsh-server`.

#### Controls Evaluated - Resulted in "Finding" and left "Open" or N/A:
* V-204422 - The Red Hat Enterprise Linux operating system must be configured so that passwords are prohibited from reuse for a minimum of five generations. This was a finding that is left in the Open status and is recommended to be fixed.
* V-204424 - The Red Hat Enterprise Linux operating system must not allow accounts configured with blank or null passwords. This is a finding that was left in the open state and is highly recommend that it be corrected as soon as possible.

**Image Demonstration**

Unfixed Control

![alt text](/Lab2/Screenshots/Centos_V-204426_Finding.png "Unfixed Finding")

Fixed Control

![alt text](/Lab2/Screenshots/Centos_V-204426_FindingFixed.png "Fixed Finding")

![alt text](/Lab2/Screenshots/Centos_V-204426_FindingFixed2.png "Fixed Finding")

---

## Highest Impact Controls Discussion

With STIG and the checklists for Windows 10 and CentOS 7 I was able to evaluate how important certain controls are through the different levels of compliance. There are three levels and they are CAT 1, CAT 2, and CAT 3. CAT 1 controls that are findings offer the highest risk for exploiting machines and doing damage to the network. CAT 2 is a moderate level of security risks and still offers the ability for the organization to be damaged. Finally, CAT 3 is the lowest risk of damage which should still be fixed but are not the first priority.

### Windows 10 Highest Security Risks

* V-220707 (CAT 1) - The Windows 10 system must use an anti-virus program. While extremely simple, this use of an anti-virus program can assist in ensuring if anything got on the machine, if it is recognized it would be quaratined.
* V-220708 (CAT 1) - Local volumes must be formatted using NTFS. This is such a high security concern due to the essential nature of needing to set proper permissions and auditing for the Local Volumes.
* V-220740 (CAT 2) - The number of allowed bad logon attempts must be configured to 3 or less. This is a moderate security concern because it is still vital to ensure that someone can not keep trying passwords forever. Account lockout is vital to ensure security from unauthorized access attempts.
* V-220742 (CAT 2) - The password history must be configured to 24 passwords remembered. This is vital to implement to ensure that there is not a chance of unauthorized access if one password is compromised. Having revolving and changing passwords is vital to ensure the security of user accounts.

**Windows 10 Discussion**

The above examples of different controls and their category level shows the multitude of vital pieces of Windows 10 that need to be secured. Some of the above controls were implemented already while others I had to implement. Any of these controls could lead to a large amount of damage to data and the network. With the password findings, these controls offer a massive opportunity for privilage escalation and unauthorized access. Overall, implementing these controls and ensuring that Windows 10 is updated to the latest version with installed drivers, will greatly increase the security for the organization.

### CentOS 7 Highest Security Risks

* V-204424 (CAT 1) - The Red Hat Enterprise Linux operating system must not allow accounts configured with blank or null passwords. This was a control that had a finding and is of great concern. If there is an ability to log in without a password, this could lead to exploitation with privilage escalation. 
* V-204425 (CAT 1) - The Red Hat Enterprise Linux operating system must be configured so that the SSH daemon does not allow authentication using an empty password. This is concerning due to the ability for a person to get into the system with ssh without a password. This was correctly implemented by default so it was not a concern, but should be checked on all systems.
* V-204442 (CAT 1) - The Red Hat Enterprise Linux operating system must not have the rsh-server package installed. This control was a finding due to the rsh-server package being installed. This presented the risk of having the ability to have a remote access service that was unencrypted. For most organizations, this is not needed for operations and should be removed to protect against unauthorized control.

**CentOS 7 Discussion**

The above examples display the major need to ensure that there is proper implementation of tools and limitation of tools such as rsh-server. There are a lot of different tools that are not needed for use under your organization, and should be removed. These could present unknown security risk if they were just left in place. Furthermore, being bale to access the machine either with ssh or physically with a `null` password value leads to a multitude of vulnerabilites. These corrections are necassary to harden the basic access and defense on all the systems across the organizations network.

---

## Conclusion

While evaluating Windows 10 and CentOS 7 with their respective STIG checklists, I came across multiple findings that had to be corrected. These systems needed to be hardened to boost their security against many known possible vulnerabilities. All these findings were documented and have been passed forward with this document. There are some that remain open with more suggestions and fixes that need to be addressed. I recommend the continued evaluation of the Operating Systems and any future Operating Systems to limit vulnerabilites and maintain strong cybersecurity throughout the organization and the network.

---

## Artifacts and Appendix

* All artifacts are stored in the [Screenshots folder](/Lab2/Screenshots).
* All STIG Checklists with notes and finding information are located in the [STIGs folder](/Lab2/STIGs).
