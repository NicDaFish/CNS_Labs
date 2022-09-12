# Investor Inc. Evaluation of Windows 10 and CentOS 7 according to the Security Technical Implementation Guide
---

Upon request from Investor Inc., I went through the systems of Windows 10 and CentOS 7 to evaulate the controls that were in place or missing from the systems. During this evaluatio, it was noticed that multiple security implementations were not in place which could lead to extreme vulnerabilites on the machines. Throughout this evaluation, I noted missing Security Technical Implemenatation as well as implemnted vital ones to ensure the safety of the systems. Below is the outome from the evaluation with the process that was taken and my recommendations.

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
* STIGViewer
- STIGViewer was used to track and manage the Windows 10 and the CentOS 7 Checklists as the evaluation was taking place. As different controls were being examined, they would be tracked as either "Open" when there was a finding and finding details were added, or as "Not a Finding" if the system already had the controls integrated. 
* Windows 10 VM (Matches the version on all Windows 10 machines in the organization)
- The Windows 10 VM was the same version that all the other Windows 10 machines were running allowing me to examine the controls that were in place on the actual machines without risking and compromising an actual machine.
* CentOS 7 VM (Matches the version on all Windows 10 machines in the organization)
- The CentOS 7 VM was the same version that all the other CentOS 7 machines were running allowing me to examine the controls that were in place on the actual machines without risking and compromising an actual machine.
* Vagrant
- Vagrant was used to manage and deploy the virtual machines through VirtualBox. This allowed for the creating and enabling of multiple virtual machines ensuring they had the same configuration. Everytime the machine was created, the version would be of the same configuration as the ones before. This allowed for a repeatable process, ensuring that the systems were properly configured. The evaluation can be repeated easily and with confidence. The machines that were examined matched a version that was on Vagrant Cloud.
* VirtualBox
- VirtualBox was the Hypervisor of choice to be used with Vagrant. VirtualBox allowed me to created desktop virtualization to utilize the GUI as a regular user would see it. I was able to easily access and confirm the controls on the systems as well as implement changes to ensure that the corrections could be implemented to fix findings. 

