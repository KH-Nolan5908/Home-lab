# RSOP, Group Policy, Task Manager, Disable Logoff

## How to disable Task Manager using Group Policy Editor :

_Objective: How would you implement a group policy that will disable Task Manager on a user's computer_

Open Server 2022 VM:
* Navigate to **Server Manager** > **Tools** > **Group Policy Management**
  
Under the mydomain.com directory:
* Right-click on **Group Policy Objects** > **New**
    * Name: **Task Manager**

<img width="1024" height="768" alt="CreationOfTaskManagerGPO" src="https://github.com/user-attachments/assets/89a71737-68ae-454c-a12d-19b399af0476" />

On the Task Manager GPO:
* Select **Delegation** > **Add...**
    * Object name to select: **Patty**
    * Permission: **Read**
    * **OK**

<img width="1024" height="768" alt="CreationOfTaskManagerGPO_2" src="https://github.com/user-attachments/assets/4b8dc68f-ecc5-40eb-8304-2d853cda22a6" />

4. Right-click on Task Manager GPO:
* Select **Edit** > **User Configuration** > **Policies** > **Administrative Templates: Policy definitions** > **System** > **Ctrl + Alt+ Del Options**
* Select **Remove Task Manager** > **Enabled** > **Apply** > **OK**

_When this policy setting is enabled, users will not be able to access Task Manager. If users try to to start Task Manager, a message appaears explaining that a policy prevents the action._

_The group policy you created is called Task Manager, and it'S assigned a policy setting that prevents the user from acessing the Task Manager._

<img width="1024" height="768" alt="RemoveTaskManager1" src="https://github.com/user-attachments/assets/3a0f2489-f48e-47fb-a5f5-f05c2c74df31" />
<img width="1024" height="768" alt="RemoveTaskManager2" src="https://github.com/user-attachments/assets/319e0ae2-fbe3-49a9-9ec3-5810dce458ce" />


Exit GPO Editior and return to Group Policy Management:
* Drag **Task Manager** GPO into the **HR** OU
* Right-click on the **Task Manager** GPO > **Enforced**

Open Desktop2 and log in as Patty:
* To update the GPO policy, open Command Prompt and enter ther following command: **gpupdate /force**
* Use the command **gpresult /r** to see the total list of policies assigned to the user's account.
* 
<img width="1024" height="768" alt="GpupdateForceTaskManager" src="https://github.com/user-attachments/assets/859268dd-d5f9-4560-b378-553a4f43927d" />

<img width="1024" height="768" alt="gpresult" src="https://github.com/user-attachments/assets/346ce579-715a-442c-acd2-0e2371f9544d" />



 On Server 2022, navigate to Group Policy Management:
* Right-click on **Group Policy Results** > **Group Policy Result Wizard...**

On Computer Selection:
* Select **Another computer** > **Browse...** 
   * Enter the object name to select: **Desktop2**

_This will generate an RSOP report of how the user Patty is set up on Desktop2._

