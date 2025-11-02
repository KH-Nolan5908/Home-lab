## Step 4 : Join Windows 10 to domain, Group Policies, CMD, RSOP Report

_Objective: Install a seperate VM workstation and join it to the domain._

1. Create a new VM workstation using the Windows 10 ISO file:

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

2. Power on _Desktop_2_ VM, to complete the installation process:
* Windows 10 Setup
     * Select **Windows 10 Pro**
     * Select **Custom: Install Windows Only**

3. Creating a user for an Organizational Unit(OU) on Server 2022
* An _Organiaztional Unit(OU)_ is used to keep things organized. To start, open the Server 2022 VM lab on your computer.
     * Select **Active Directory Users & Computers**
     * Right-click on **mydomain.com** > **New** > **Organization Unit**
     * Name: **HR** (or any name you choose)
     * Repeat the process and create one called **IT**

       
<img width="1024" height="768" alt="part4_pic1OU" src="https://github.com/user-attachments/assets/23f39e98-3c2b-4954-9578-f43240c6af7e" />


* Creating a hypothetical user for an HR Organizational Unit(OU):
    * Right-click on **Users** > **New** > **User**
    * First Name: **Patty**
    * User logon name: **Patty**
    * Password: **Password1234**
    * User Must Change Password at next logon: **No**
    * Drag the user **Patty** to the **HR** OU.
    * Drag the user **helpdesk** to the **IT** OU.
      
<img width="1024" height="768" alt="Part_4 2_HR" src="https://github.com/user-attachments/assets/e91e9ad5-5c17-47cf-9b3b-700a883b6176" />

* To view the user's Patty's account infomation, use the following command on the windows command prompt:
        * **net user patty /domain**

  <img width="1024" height="768" alt="Part_4 4_cmd" src="https://github.com/user-attachments/assets/aa59d9c3-7656-46cf-b9eb-591b5b08053f" />


5. Exploring _Group Policy Management_:

* This is where we will assign and manage Group Policies for our user accounts on our domain.
* Open Server Manager:
    * Select **Tools** > **Group Policy Management**
    * Navigate to **Domains** > **mydomain** > **Default Domain Policy** > **Settings**

* Here we can view the network and security policies associated with our domain. For example, under _Account Policies/Kerberos Policy_, we can view the set policies pertaining to our user accounts, which includes the policies set for our maximum/minimum password length, age, or account-lockout threshold.

<img width="1024" height="768" alt="part4 5_DefaultDomainPolicy" src="https://github.com/user-attachments/assets/a6e5d28e-a1b3-4076-9822-1f75877a493f" />


6. Exploring _Group Policy Editor_:

* To edit/modify any policies associated within our domain, we can use the _Group Policy Editor_. Let's modify one of the policies that relates to a Windows account.
  
* To edit the _Windows Account Lockout Threshold_:
  * Navigate to **mydomain** > **Default Domain** > **Edit...**
  * Under _Computer Configuration_, select **Policies** > **Windows Settings** > **Security Settings** > **Account Policies** > **Account Lockout Policy**
  

<img width="1024" height="768" alt="part4 6_GPOEditorAccountLockout" src="https://github.com/user-attachments/assets/28e4b11e-1a85-4c18-9720-e71b483a2cd8" />

* On _Acount Lockout Threshold_ Properties
    Enable **Define this policy setting**
    Account will lock out after: **10 invalid logon attempts**
    Select **Apply** > **OK**
    Right-click on **Default Domain** > **Enforce**

* When restarting _Group Policy Management_, the effects will show inside the default domain settings.

<img width="1024" height="768" alt="part4 7_AccountLockoutThreshold" src="https://github.com/user-attachments/assets/9b432428-3963-4407-a318-0b73318006df" />


7. Join a Windows 10 VM to a Domain:

* Open _Desktop_2_ VM containing the Windows 10 Workstation.

* Activate an Administrative account:
    * Open **File Explorer**
    * Right-click on **This PC** > **Manage**
    * On Computer Management, select **Local Users & Groups** > **Users**
    * Right-click on **Administrator** > **Properties** > uncheck **Account is disabled**
    * Right-click on **Administrator** > **Set Password** > **Proceed** > **OK**
    * Right-click on **Home** > **Shut down or sign out** > **Sign out**


<img width="1024" height="768" alt="part4 7_EnableAdminAccount" src="https://github.com/user-attachments/assets/2036cbc4-3d48-428a-841e-e50c8da83ad0" />


* Once you log in as an Administrator:
    * Open **Control Panel** > **View Network Status & Tasks** > **Change Adapter Settings** >
    * Right-click on **Ethernet** > **Properties**
    * Double-click on **Internet Protocol Version 4(TCP/IPv4)**

* We will manually assign the following static IP address to VM so that may join it to our Domain at Server 2022. Enter the following IP Configurations:
    * IP address:               **10.1.10.4**
    * Subnet mask:              **255.0.0.0**
    * Default Gateway:          **10.1.10.1**
    * Preferred DNS Server:     **10.1.10.2**
    * Alternate DNS Server:     **10.1.10.1**

<img width="1024" height="768" alt="part4 8_Windows10IPV4Config" src="https://github.com/user-attachments/assets/0539265e-906a-4349-ab3a-53104f5103d7" />


* To be able to communicate with other virtual machines stored locally on our device, we need to enable the proper network adapter configuration settings in VirtualBox. On the toolbar above:
    * Select **Devices** > **Network** > **Network Settings...**
    * Attached to: **Host-only Adapter**

* If you don't have an Host-Only network adapter, you can create one in Virtual Box Manager:
    * **File** > **Tools** > **Network** > **Create**


<img width="1039" height="684" alt="part4 9_HostAdapterSettings" src="https://github.com/user-attachments/assets/c745cee9-0598-4435-ad99-fee48f7d33bf" />

 * On the Windows Settings About Page:
    * Select**Rename this PC(advanced)**
    * Click Change to insert your Domain & Rename your Computer
    * Computer Name: Desktop2
    * Domain:<YourDomainname.com>

    ConnectWindows10ToDomain.png

