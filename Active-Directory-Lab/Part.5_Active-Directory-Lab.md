# Common Active Directory Issues

## 1.) Scenario 1: Unlocking a user account

1. Scenario 1: A user named Patty has called to inform you that their account is locked after too many failed login attempts.
   How would you unlock their account in Active Directory?

   (On Desktop_2 VM, try logging into the user Patty, using multilple failed passwords to lock the account.)

    <img width="1024" height="768" alt="PattyAccountLockout" src="https://github.com/user-attachments/assets/76c64293-8644-415f-ad26-dc197a759582" />

   

* Power on Server2022 VM and open Active Directory Users & Computers:
  * Navigate to Server Manager > Tools > Active Directory Users & Computer
    
* Under the HR Organizational Unit(OU):
  * Right-click on Patty > Properties > Check Unlock account > Ok

 * You may now be able to login into Patty.

   <img width="1024" height="768" alt="UnlockPattyAccount" src="https://github.com/user-attachments/assets/21f81a4d-c261-4137-8a09-163a0b60a3a4" />

## 2.) Scenario 2: Enable/Disable a user account

2. Scenario 2. Patty, has returned from her vacation only to find that her account has been disabled while away. 
She cannot lock in. How should you resolve this problem in Active Directory?

<img width="1024" height="768" alt="PattyAccountHasbeenDisabled" src="https://github.com/user-attachments/assets/45b85f8b-7ab7-4d77-9720-c2648679af2c" />

* On Active Directory Users & Computers:
  * Right-click on Patty > Disable Account
  * Restart Desktop_2

* This will disable Patty's account
* To re-enable her account simply locate the user and select Enable.

  <img width="1024" height="768" alt="PattyEnabledAccount" src="https://github.com/user-attachments/assets/2500f083-fb92-40a5-8467-a4a2d0f4dbae" />



## 3.) Scenario 3: Changing a user's password
2. Scenario 3. Patty wants to change her password to a more secured option. She contacts you for assistance.
How would you resolve her problem in Active Direcotry?

* Navigate to Active Directory Users & Computers:
  * Right-click on mydomain > Find > Patty > Find Now
  * Right-click on Patty > Reset Password...
  * Check "User must change password at next logon"
  * New Password: Welcome1

<img width="1024" height="768" alt="ResetPattyPassword" src="https://github.com/user-attachments/assets/58b38975-00fe-4048-840b-bc7ec42afc53" />

      
## 4.) Scenario 4: Extend/Renew a user's account

4. Scenario 4. Patty's user account has expired. How would you renew her account on Active Directory?

<img width="1024" height="768" alt="Desktop2PattyUserAccountExpired" src="https://github.com/user-attachments/assets/0d851452-0e9e-41fe-9950-31e390bc5422" />


* On Active Directory Users & Computers:
  * Right-click on Patty > Properties
* In Patty Properties, locate the Account tab
  * Under Account expires, select Never > Apply > OK
    
* The account is set to never expire. This allows you to log in successfully as Patty in Desktop2.

<img width="1024" height="768" alt="ExtendPattyAccount" src="https://github.com/user-attachments/assets/b63388e1-3428-4d5c-97b1-de9824bca230" />

