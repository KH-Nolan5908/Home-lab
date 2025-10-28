
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

In Active Direcotry Domain Services Configuration Wiard:
* Select **Add a new forest**
**Root Domain Name**: mydomain.com  > **Next**
* Set **(DSRM) password:** Password123  > **Next**
* Skip to _Prequistes Check_: **Install** and **Restart PC**

 5. Login Using:
    **User**: mydomain/Administrator
    **Password**: Random123

<img width="1024" height="768" alt="Step2_4LastPicture" src="https://github.com/user-attachments/assets/d89abad2-f87b-479c-b793-2414f2543d5a" />
