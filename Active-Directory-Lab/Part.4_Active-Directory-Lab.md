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

In this example, we will use the command prompt and use the command net user to view the Patty's user account infomation of our domain.

Open the command prompt on Windows, type and Enter:
        net user patty /domain

5. Exploring Group Policy Management

* This is where we will assign and manage any group policies for our domains and accounts on our system.
* Open Server Manager:
    * Select **Tools** > **Group Policy Management**
    * Select **Domains** > **mydomain**(your Domain) > **Default Domain Policy** > **Settings**

* Here we can view the network and security policies associated with our domain. For example, under _Account Policies/Kerberos Policy_, we can view the set policies pertaining to our user accounts, which includes the policies set for our maximum/minimum password length, age, or account-lockout threshold.

GroupPolicyManagement1.png

6. Exploring Group Policy Editor

* To edit/modify any policies associated within our domain, we can use the _Group Policy Editor_. Let's modify one of the policies that relates to a Windows account.

* To edit our Windows Account Lockout Threshold:
    Navigate to **mydomain**(<your_Domain>):
    Right-click on **Default Domain** > **Edit...**
    Select **Policies** > **Windows Settings**>**Security Settings** > **Account Policies**
    Double-click on **Account Lockout Policy**

    GroupPolicyEditor1.png

* On Acount Lockout threshold Properties
    Enable **Define this policy setting**
    Account will lock out after: **10 invalid logon attempts**
    Select **OK** > **Apply**
    Right-click on **Default Domain** > **Enforce**

* When restarting Group Policy Management, the effects will show inside your default domain settings

EnforceGPO.png


7. Join a Windows 10 VM  to our Domain

* Open _Desktop_2_ VM containing the Windows 10 Workstation.

* Activate an Administrative account:
    * Open **File Explorer**
    * Right-click on **This PC** > **Manage**
    * On Computer Management, select **Local Users & Groups** > **Users**
    * Right-click on **Administrator** > **Properties** > uncheck **Account is disabled**
    * Right-click on **Administrator** > **Set Password** > **Proceed** > **OK**
    * Right-click on **Home** > **Shut down or sign out** > **Sign out**


    EnableAdministratorAccountWindows10.png


* Once you log in as an Administrator:
    * Open** Control Panel** > **View Network Status & Tasks**
    * Select **Change Adapter Settings** > **Ethernet** > **Properties**
    * Double-click on **Internet Protocol Version 4(TCP/IPv4)**

* We will manually assign the following static IP address to this workstation so we can  join it to our Domain. Enter the following IP Configurations:
    * IP address:               **10.1.10.4**
    * Subnet mask:              **255.0.0.0**
    * Default Gateway:          **10.1.10.1**
    * Preferred DNS Server:     **10.1.10.2**
    * Alternate DNS Server:     **10.1.10.1**

Windows10_VM_IPConfigurations.png


* To be able to communicate with other virtual machines stored locally on our device, we need to enable the proper network adapter configuration settings in VirtualBox. On the toolbar above:
    * Select **Devices** > **Network** > **Network Settings...**
    * Attached to: **Host-only Adapter**

* If you don't have an Host-Only network adapter, you can create one in Virtual Box Manager:
    * **File** > **Tools** > **Network** > **Create**


 HostAdapter.png

 * On the Windows Settings About Page:
    * Select**Rename this PC(advanced)**
    * Click Change to insert your Domain & Rename your Computer
    * Computer Name: Desktop2
    * Domain:<YourDomainname.com>

    ConnectWindows10ToDomain.png

