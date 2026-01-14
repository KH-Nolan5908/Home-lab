## Step 6: Security Groups, Map Drives, Personal Drives, Map Letters


1. Creating Share drive in Active Directory:

* On Server 2022:
* Navigate to **Server Manage**r > **File and Storage Services** > **Shares**
* In the **Share Menu**, right-click to select **New Share..**
NewShare1.png

* Select **SMB Share - Quick** > **Next**
    * Share Name: **HR**
    * Create
* Create anotner share called _Personal_ using previous instructions.
SpecifyShareName.png
CreateShare.png


2. Creating Security Group:

* In Active Directory Users and Computers:
* Under **mydomain.com**, right-click on **Users** > **New** > **Group**
    * Group Type: **Security**
    * Group Name: **HR**
    * **OK**
SecurityGroupSetup2.png

* On the HR Security Group:
* Right-click & select **Properties** > **Managed By** > **Change**
    * Object Name to select: **helpdesk**

_The HR security group is now managed by the user helpdesk located in IT._

Create an additional security group called Personal using the steps above.


3. Adding Members to Security Group:

* On the HR security group:
* Right-click and select **Properties** > **Members** > **Add...**
    * Object names to select: **Patty**
    * **Apply**

_Patty is now a member of the HR security Group. Repeat the process on your Personal security group._
MemberHRSecurityGroup.png


4.Modifying Permissions on Personal Share drive:

* Open **File Explore** > **Local Disk (C:)** > **Shares**
    * Right-click on **Personal** > **Security** > **Advance**
PersonalSharePropertiesAdvance.png


* In **Advanced Security Settings**
* Select **Disable Inheritance** > **Convert inherited permissions into explicit permissions on this object**
In Permission entries:

Remove all Users (MYDOMAIN\Users)* form the list
Select Add, to add a Permission Entry for the Personal Share"
Principle: Personal
Basic Permissions: Modify, Read & execute, List folder contents, Read, Write
OK > Apply > OK

ConvertInheritedObjectsToExplicitPermissions.png
PersonalShareBasicPermissions.png

In Personal Properties
Navigate to Sharing > Share...

Under Network access:
Select Personal > Permission Level: Read/Write > Share

PersonalRead&Write.png

/
Modifying Share Permissions on the HR Share Folder


Navigate to the HR Share Folder in File Explore:

File Explorer > Local Disk (C:) > Shares > HR >
Right-Click on HR > Properties > Security > Advanced

In Advanced Security Settings For HR Shares:

Select Disable Inheritance > Convert inherited permissions into explicit permissions on this object
Remove User(MYDOMAIN\Users)*
Select Add > Principal: Select a principal
    Object name to select: helpdesk
    Basic Permissions: Modify, Read & execute, List folder contents, Read, Write

Select OK > Apply > OK
Repeat and add HR to the principal.

HRShareBasicPermissions.png

In HR Properties:
Navigate to Sharing > Share...
    HR Permission Level: Read/Write


Mapping HR Share Drive to an authorized user

We will now attempt to map the HR network drive to user Patty. Open Desktop2 VM and log in as Patty.

Open File Explore > This PC > Map network drive...
    Drive Letter: Z(any letter)
    Folder: \\Myserver2022\hr
    Reconnect at sign-on: Yes
    Finish

MappingHRshareDriveToPatty.png

Mapping Personal Share drive to an authorized user on Active Directory:

Open Server2022 and navigate to Active Directory Users and Computers:

Under the HR Organizational Unit(OU)
Right-click on Patty > Properties > Profile

In Home Folder
    Connect: P: To: \\MYSERVER2022\Personal%username%
    Apply > Ok

MappingPattyToPersonalUsingAD.png

This created a folder called Patty in our Personal share drive in Server 2022. Log in as the user Patty on Desktop2 to view the final results.

FinishedResults.png
