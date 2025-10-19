# Active Directory Lab - Step-By-Step 



## Step 1: Aquire Software

### Download Software Here:

* Oracle Virtual Box [(Download here)](https://www.virtualbox.org/)
* Windows 10 Server 2022 64-bit [(Download here)](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022)
* Windows 10 ISO [(Download here)](https://www.microsoft.com/en-us/software-download/windows10)

## Step 2: Installing Server 2022 on VirtualBox

1. Open VirtualBox > Click **New**.
2. Create a new Virtual Machine:
    * **Name**: Server2022Lab
    * **ISO Image**: <Server 2022 ISO File>
    * **Type**: Microsoft Windows
    * **Version**: Windows Server 2022 (64-bit)
    * **Skip Unattended Installation**: Yes

3. Hardware:
   * **Base Memory**: 2080 MB(2GB) minimum
   * **Processors**: 1 CPU minimum

4. Hard Disk File Location & Size:
   * (This is dependent on the amount of disk space you're willing to allocate)
   * **25.00 GB** (Minimum Required)

**Finish**
<img width="941" height="637" alt="Step1_1_VirtualBoxSetupParameters" src="https://github.com/user-attachments/assets/3c94c95a-e437-434f-96e1-ac617bee901f" />

5. Start the VM and mount the downloaded Server 2022 **ISO** file to begin the boot process.
 <img width="1155" height="979" alt="Step1_5WindowsBootMenu" src="https://github.com/user-attachments/assets/aee4d975-7a6f-4d5f-b163-939608df96c4" />

On the Windows Setup menu:
* Click **Next** > **Install Now**
* Select **Windows Server 2022 (Desktop Experience)** > **Next**
* Select **Custom: Install Microsoft Server** > **Next**
     * (This is going to install Server 2022 OS onto the allocated storage space (25.0 GB Storage) we cofigured earlier on our VM)


<img width="1156" height="980" alt="Step1_5_1InstallServer2022Desktop" src="https://github.com/user-attachments/assets/ca239664-48d1-435d-84cb-6652f84c11c8" />


## Step 2 : Installing Active Directory on Server 2022

_Objective: Change the default server name and install Active Directory with our own custom Domain._

1. Press the Windows Home Button, and go to **Settings** > **System** > **About** > **Rename this PC. > Next > Restart Now**

_(Change the PC name to something readble like myServer2022 or anything you find appropriate.)_

<img width="1024" height="768" alt="Step2_1ServerNameChange" src="https://github.com/user-attachments/assets/441cafb7-4b0c-4064-8ad3-791ae95acbd8" />


2. Next, Open Server Manager:
   * Select **Manage** > **Add Roles and Features** > **Next** > **Role-Based Feature-Based Installation**
     
 3. Click **Next** to _Server Roles_ and select **Active Direcotry Domain Services** > **Add Features**
    
    <img width="1156" height="980" alt="Step2_2InstallingAD" src="https://github.com/user-attachments/assets/207eaf94-0443-4e32-b519-6e217e0fd994" />

4. Complete the installation process under "_Confirmation_" by clicking **Install**. Then click **Promote this server to a domain controller**

In the Active Direcotry Domain Services Configuration Wiard:
* Select **Add a new forest**
**Root Domain Name**: 1st_Domain.com  > **Next**
* Set **(DSRM) password:** Password123  > **Next**
* Skip to _Prequistes Check_: **Install** and **Restart PC**

 5. Login Using:
    **User**: 1st_Domain/Administrator
    **Password**: Random123

<img width="1024" height="768" alt="Step2_4LastPicture" src="https://github.com/user-attachments/assets/d89abad2-f87b-479c-b793-2414f2543d5a" />


## Step 3 : Active Directory Account Creation, CMD Commands

Objective: Manually create a user account containing all the administrative group policies.

1. Open Server Manager:
   * Select **Tools** > **Active Directory Users & Computers**
   * Note: Pin tab to the taskbar

2. Create a User Account:
   * Right click the container called **Users** > **New** > **User**
<img width="1155" height="1110" alt="Step3_2ADCreateNewUserNavigation" src="https://github.com/user-attachments/assets/b7d618da-8e7d-4d6c-957f-05c5d45bf63b" />

3. User Configuration:
   
   * First Name: **TestUser1**
   * User logon name: **TestUser1**
   * Password: **Password1!**(Or anything you choose)
   * Password Never Expires: **Yes**
   * Finish

4. To copy a User and its group policies to create another:

Right-Click on a user account and select Copy:
   (In this case I selected the Administrator account to copy)
      * First Name: **helpdesk**
      * User logon name: **helpdesk**
      * Password: **Password123!**(Or anything you choose)
      * Password Never Expires: **yes**
      * **Finish**

<img width="1156" height="980" alt="Step3_3ADCopyAdminUser" src="https://github.com/user-attachments/assets/5c2347d6-bcfd-48b9-8c1a-d145a2106666" />

<img width="1024" height="768" alt="VirtualBox_Server2022Lab_07_09_2025_00_50_20" src="https://github.com/user-attachments/assets/86f649dc-5bfa-41a6-b789-bc4e65285ee1" />


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


  
4. Using command-prompt To view a user account information



      







