# Active Directory Lab - Step-By-Step 



## Step 1: Aquire Software

### Download Software Here:

* Oracle Virtual Box [(Download here)](https://www.virtualbox.org/)
* Windows 10 Server 2022 64-bit [(Download here)](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022)
* Windows 10 ISO [(Download here)](https://www.microsoft.com/en-us/software-download/windows10)

## Step 2: Installing Server 2022 on VirtualBox

1. Open VirtualBox > Click **New**.
2. Create Virtual Machine
    * **Name**: Server2022Lab
    * **ISO Image**: <Server 2022 ISO File>
    * **Type**: Microsoft Windows
    * **Version**: Windows Server 2022 (64-bit)
    * **Skip Unattended Installation**: Yes

3. Hardware:
   * **Base Memory**: 2080 MB(2GB) minimum
   * **Processors**: 1 CPU minimum

4. Hard Disk File Location & Size
   * (This is dependent on the amount of disk space you're willing to allocate)
   * **25.00 GB** (Minimum Required)

**Finish**
<img width="941" height="637" alt="Step1_1_VirtualBoxSetupParameters" src="https://github.com/user-attachments/assets/3c94c95a-e437-434f-96e1-ac617bee901f" />

5. Start the VM and mount the Server 2022 ISO file to begin the boot process. On Windows Setup menu:
 <img width="1155" height="979" alt="Step1_5WindowsBootMenu" src="https://github.com/user-attachments/assets/aee4d975-7a6f-4d5f-b163-939608df96c4" />



   
 * Click **Next** > **Install Now**
* Select **Windows Server 2022 (Desktop Experience)** > **Next**
* Select **Custom: Install Microsoft Server** > **Next**
* (This is going to install Server 2022 OS onto the allocated storage space (25.0 GB Storage) we cofigured earlier on our VM)


   








