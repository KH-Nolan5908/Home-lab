## Step 6: Security Groups, Map Drives, Personal Drives, Map Letters


### 1. Creating a Share drive in Active Directory:

On Server 2022:
* Navigate to **Server Manage**r > **File and Storage Services** > **Shares**
* In the **Share Menu**, right-click to select **New Share..**

<img width="1024" height="768" alt="NewShare1" src="https://github.com/user-attachments/assets/07aac8f3-3826-4f1f-906d-0541dd020d88" />


* Select **SMB Share - Quick** > **Next**
    * Share Name: **HR**
    * Create
* Create anotner share called _Personal_ using previous instructions.
SpecifyShareName.png

<img width="1024" height="768" alt="CreateShare" src="https://github.com/user-attachments/assets/b6203dee-81a5-45f6-adb7-cfff5a9e5b5f" />


### 2. Creating a Security Group in Active Directory:

In Active Directory Users and Computers:
* Under **mydomain.com**, right-click on **Users** > **New** > **Group**
    * Group Type: **Security**
    * Group Name: **HR**
    * **OK**

<img width="1024" height="768" alt="SecurityGroupSetup2" src="https://github.com/user-attachments/assets/a8cb372b-f32f-4235-855d-1af5b8f49f1c" />


On the HR Security Group:
* Right-click & select **Properties** > **Managed By** > **Change**
    * Object Name to select: **helpdesk**

_The HR security group is now managed by the user helpdesk located in IT._

Create an additional security group called **Personal** utilizing the steps above.


### 3. Adding members to a Security Group:

* On the HR security group:
* Right-click and select **Properties** > **Members** > **Add...**
    * Object names to select: **Patty**
    * **Apply**

_Patty is now a member of the HR security Group. Repeat the process on your Personal security group._

<img width="397" height="452" alt="MemberHRSecurityGroup" src="https://github.com/user-attachments/assets/71b0e941-ed71-4ced-bfa5-3f76a3fea7a7" />



### 4.Modifying permissions on a Personal Share drive:

* Open **File Explore** > **Local Disk (C:)** > **Shares**
    * Right-click on **Personal** > **Security** > **Advance**

<img width="1024" height="768" alt="PersonalSharePropertiesAdvance" src="https://github.com/user-attachments/assets/e24bb939-31aa-4d3c-b2cb-67226b4b5313" />


In **Advanced Security Settings**:
* Select **Disable Inheritance** > **Convert inherited permissions into explicit permissions on this object**
 
In **Permission entries**:
* Remove all **Users (MYDOMAIN\Users)*** from the list
* Select **Add**, to add a Permission entry for the Personal share
   * Principle: **Personal**
   * Basic Permissions: **Modify**, **Read & execute**,**List folder contents**, **Read**, **Write**
   * **OK** > **Apply** > **OK**


<img width="1024" height="768" alt="ConvertInheritedObjectsToExplicitPermissions" src="https://github.com/user-attachments/assets/90d5b2cc-a3df-4924-bb24-030a92a93a27" />
<img width="1024" height="768" alt="PersonalShareBasicPermissions" src="https://github.com/user-attachments/assets/6c023321-d6b0-4ae6-b3df-f423440604dd" />


In Personal **Properties**:
* Navigate to **Sharing** > **Share...**

Under **Network access**:
* Select **Personal** > **Permission Level: Read/Write** > **Share**

<img width="1024" height="768" alt="PersonalRead Write" src="https://github.com/user-attachments/assets/9801c55e-1a33-48eb-9716-fad43dff0d79" />



### 5. Modifying Share Permissions on an HR Share Folder

* Navigate to **File Explorer** >**Local Disk (C:)** > **Shares** > **HR** >
* Right-click on **HR** > **Properties** > **Security** > **Advanced**

In **Advanced Security Settings**for HR Shares:
* Select **Disable Inheritance** > **Convert inherited permissions into explicit permissions on this object**
* Remove all **User(MYDOMAIN\Users)**
* Select **Add** > **Principal: Select a principal**
  * Object name to select: **helpdesk** & "**HR**"
  * Basic Permissions: **Modify**, **Read & execute**, **List folder contents**, **Read**, **Write**
  * Select **OK** > **Apply** > **OK**


<img width="1024" height="768" alt="HRShareBasicPermissions" src="https://github.com/user-attachments/assets/fc6ab72c-39ad-4090-ba9f-426b4dd5469e" />

In HR Properties:
* Navigate to **Sharing** > **Share...**
    HR Permission Level: **Read/Write**


### 6. Mapping HR Share drive to an authorized user:

Map the HR share folder to the to user Patty on a Windows 10 client. Open Desktop2 VM and log in as Patty.

* Open **File Explore** > **This PC** > **Map network drive...**
    Drive Letter: **Z**(_any letter_)
    Folder: **\\Myserver2022\hr**
    Reconnect at sign-on: **Yes**
    **Finish**

<img width="1024" height="768" alt="MappingHRshareDriveToPatty" src="https://github.com/user-attachments/assets/eb742181-5c79-42ff-b758-1e41a0fd6366" />

## Mapping a Personal Share drive to a user on Active Directory:

Open Server2022. Under the HR Organizational Unit(OU)
* Right-click on **Patty** > **Properties** > **Profile**

* In **Home** Folder:
   * Connect: **P**: To: **\\MYSERVER2022\Personal%username%**
   * **Apply** > **Ok**

<img width="1024" height="768" alt="MappingPattyToPersonalUsingAD" src="https://github.com/user-attachments/assets/b94a0547-fb7d-4db8-b149-6c8e776f6394" />


_This created a folder called Patty inside the **Personal** share drive in AD. On Desktop2, Log into the user as Patty to view the final results.
_

<img width="1024" height="768" alt="FinishedResults" src="https://github.com/user-attachments/assets/9b65970b-43e3-47ca-9ad8-1c6b7f28a985" />
