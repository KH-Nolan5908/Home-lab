## Step 4 : Join Windows 10 to domain, Group Policies, CMD, RSOP Report

_Objective: Install a seperate VM workstation and join it to the domain._

1. Create a new VM workstation using the Windows 10 ISO file.

* Open VirtualBox > **New**
     * Name: **Desktop_2**
     * Type: **Microsoft Windows**
     * Version: **Windows 10 (64-Bit)**
* Hardware:
   * Base Memory: **4GB**
   * Processors: **1**
     
* Virtual Hard Disk:
  * Disk Size: **25.00 GB**
 
* Click **Finish**

2. Power on Desktop_2 VM, to complete the installation process.
* Windows 10 Setup
     * Select **Windows 10 Pro**
     * Select **Custom: Install Windows Only**

3. Creating a user for an Organizational Unit(OU) on Server 2022
* An _Organiaztional Unit(OU)_ is used to keep things organized. To start, open the Server 2022 VM lab on your computer.
     * Select **Active Directory Users & Computers**
     * Right-click on **1st_Domain** > **New** > **Organization Unit**
     * Name: **HR** (or any name you choose)
     * Repeat the process and create one called **IT**

       
<img width="1024" height="768" alt="OU" src="https://github.com/user-attachments/assets/2556eb9d-767d-4f11-83f2-f071a903d91a" />

* Creating a User for an Organizational Unit(OU)
    * Right-click on **Users** > **New** > **User**
    * First Name: **Patty**
    * User logon name: **Patty**
    * Password: **Welcome1**
    * User Must Change Password at next logon: **No**
    * Drag the user **Patty** to the **HR** OU.
    * Drag the user **helpdesk** to the **IT** OU.
      
<img width="1024" height="768" alt="OUHR IT" src="https://github.com/user-attachments/assets/49d9be74-8455-4b0b-b585-0bf60772f155" />


