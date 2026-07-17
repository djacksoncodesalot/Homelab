# Homelab
Active Directory Homelab
07/16/2026

## Creation of “Derrick’s Homelab”-

Purpose: Process Manual/Log

Tools and Software needed: 

1. Oracle VirtualBox or comparable hypervisor 
2. Windows Server ISO (and Windows 11 for later)

Prerequisites

1. Enough Space on whichever drive you select to run your virtual machine. 

Steps:

1. Download Oracle VirtualBox 
2. Create a Domain Controller by creating a new virtual machine 
    1. This Domain Controller can be set to these specs if you are working on a mid-range laptop or greater.
        1. 50GB memory
        2. 2 CPUs
        3. 4GB of RAM

*See Errors section for common errors I got during this process*

1. Once this is created, in the network settings of the Domain Controller virtual machine, change the Adapter1 to a Bridged Adapter, allowing a bridge from your host PC’s internet to the Virtual Machine (for ease of installing updates and downloading necessary tools).
2. Then,  you would boot up your virtual machine and complete the process of downloading Windows Server 
    1. Tricky part for me at first- if their is no allocated space within the Virtual Machine’s memory once you are asked where to mount the ISO disk, then you should delete the given Primary partition and there will be an available partition once that is completed.
    2. Most of this process is really waiting.
3. Once you have booted up in Windows Server, you will be asked to create a password for the administrator. 
4. Once logged in you will see the Service Manager screen, and this is where the action happens!
5. Navigate to the Manage tab in the top right of the screen and you will find a label that says “add roles and services”. 
6. This is where you will download Active Directory.
7. Follow prompts until you see Active Directory.
8. Once you’re finished, your computer will restart and Active Directory will be ready for use.
9. Once you are back into the Service Manager, navigate to the tools and click the Active Directory option for users and computers.
10. Here you will add your OU’s, your groups, your users, and the policies for each.

I will be modeling this setup after a medium-sized enterprise company with 100 users.
11. The Organizational Units I will be using are Users and Computers, with security groups delegated to each department.
12. Within the Computer OU, I have a group named Workstations. The group will then have these policies atteched
Settings:

Disable Guest account

Enable Windows Firewall

Enable Windows Defender

Automatic Updates

Turn on BitLocker (if supported)

Disable AutoRun

Enable SmartScreen

13. This provides a good baseline for each workstation that will be used, and further restrictions or access can be granted on a user level
depending which groups they are allocated to.

14. Now I will create a file folder within my Virtual Machine, named Global.
15. Within Global there will be multiple folders with varying levels of authorization necessary according to the GPO applied to each group.
16. For instance, only Executives and H.R are allowed to access payroll documentation as that file will not be shared with other groups.

I am still working on making more unique and interesting rules, so feel free to shoot me any inspiration.
17. For instance, only the  
