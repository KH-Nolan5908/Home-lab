## Step 3 : Active Directory Account Creation, CMD Commands

Objective: Manually create a user account containing all administrative group policies.

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

