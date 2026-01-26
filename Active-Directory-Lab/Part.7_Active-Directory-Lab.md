# RSOP, Group Policy, Task Manager, Disable Logoff

## How to disable Task Manager using Group Policy Editor :

How would you implement a group policy that will disable Task Manager on a user's computer?

Open Server 2022 VM:

Navigate to Server Manager > Tools > Group Policy Management

Under mydomain.com directory
Right-click on Group Policy Objects > New >
    Name: Task Manager

CreationOfTaskManagerGPO.png

On the Task Manager GPO:
Select Delegation > Add...
    Object name to select: Patty
    Permission: Read
    OK

CreationOfTaskManagerGPO_2.png

Right-click on Task Manager GPO:
Select Edit > User Configuration > Policies > Administrative Templates: Policy definitions > System > Ctrl + Alt+ Del Options
Select Remove Task Manager > Enabled > Apply > OK

When this policy setting is enabled, users will not be able to access Task Manager. If users try to to start Task Manager, a message appaears explaining that a policy prevents the action.

The group policy you created is called Task Manager, and its assigned a policy setting that prevents user from acessing the Task Manager

RemoveTaskManager1.png
RemoveTaskManager2.png

Exit GPO Editior and return to Group Policy Management

Drag Task Manager GPO into the HR OU
Right-click on Task Manager GPO > Enforced

Open Desktop2 and log in as Patty.

To update the GPO policy, open Command Prompt and enter ther following command: gpupdate /force

GpupdateForceTaskManager.png

Use the command gpresult /r to see the total list of policies assigned to the user's account.
gpresult.png


In Group Policy Management on Server 2022:

Right-click on Group Policy Results > Group Policy Result Wizard...

On Computer Selection:
Select Another computer > Browse... > 
    Enter the object name to select: Desktop2

This will generate an RSOP report of how the user Patty is set up on Desktop2.

