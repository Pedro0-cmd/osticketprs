<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

-Azure Virtual Machine

-Internet Information Services (IIS)

-PHP Manager

-Rewrite Module

-VC Redist

-MySQL

-Heidi SQL

-osTicket v1.15.8

-Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Steps</h2>


### Steps to Set Up and Access a Virtual Machine

1. **Create a Virtual Machine**
   - First, create a virtual machine.
   - Ensure it has at least **2 vCPUs** and **8 GB of RAM**.
   - Choose **Windows 10** or a later version as the operating system. (I prefer Windows 10, so that’s what I’ll be using for this guide.)

2. **Access the Virtual Machine via Remote Desktop**
   - Next, open the **Remote Desktop** application to connect to your virtual machine.
   - In the **Computer** field, enter the **IP address** of your virtual machine to log in.
     ![image](https://github.com/user-attachments/assets/d6e9213a-1c24-4a24-a682-85d41d6cb7cd)
     ![image](https://github.com/user-attachments/assets/68d3d48d-2f08-4eb8-9c81-7ecf79870835)

3.**Install / Enable IIS in Windows with CGI and Common HTTP Features**

 **Go to the Control Panel**:
   - Open the Control Panel. You can do this by pressing the `Windows` key, typing **Control Panel**, and selecting it from the search results.

 **Select "Programs"**:
   - In the Control Panel, find and click on **Programs**.

 **Click "Turn Windows features on or off"**:
   - Under the "Programs and Features" section, click on **Turn Windows features on or off**. This will open a list of features that you can enable or disable in Windows.

![image](https://github.com/user-attachments/assets/3290a685-fec4-4774-bd56-1484e264682f)
![image](https://github.com/user-attachments/assets/55e0aa81-de01-404a-ae6a-d54e81660074)

These are the Windows features you need to enable: CGI and Common HTTP Features. Ensure that all the options under Common HTTP Features are checked.

![image](https://github.com/user-attachments/assets/fa0e697e-1247-420a-b259-c290de18c8bc)

To verify that IIS is installed and enabled, open your preferred browser and navigate to 127.0.0.1. You should see a page similar to this.

![image](https://github.com/user-attachments/assets/147626f3-39c4-485a-9aec-6b8f7b5236d2)

Next, go to the installation files, download ***PHP Manager***, and proceed with the installation.

Also, download and install the ***Rewrite Module (rewrite_amd64_en-US.msi)***.

Create a folder named ***'PHP'*** in the C drive.

I know I mentioned installing PHP, but there's also a ZIP file named ***PHP (php-7.3.8-nts-Win32-VC15-x86.zip)*** that you need to download. Unzip this file into the 'PHP' folder you created.

We're almost done. You will need to download and install ***VC_redist.x86.exe***.

Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi). Run the setup wizard and follow these steps:

Choose ***'Typical Setup.'***

![image](https://github.com/user-attachments/assets/d9e4701f-d7e4-40b0-aa70-e77897c5e45e)

After installation, select ***'Launch Configuration Wizard.'***


Choose ***'Standard Configuration.'***

![image](https://github.com/user-attachments/assets/33baf9ce-c7cc-4f9b-b180-c26016243787)

![image](https://github.com/user-attachments/assets/1ebb4525-8cf1-4398-952b-78472a8fa700)


Set the new root password to: Password1.

![image](https://github.com/user-attachments/assets/29a2e50c-85d3-4e5e-98b8-c919a4c6b218)

Execute the process on the following page.

![image](https://github.com/user-attachments/assets/e1aa59db-04c3-4228-89d9-624e87dbd75f)

Now that we have downloaded and installed the files, search for IIS in the Windows search bar. Open IIS as an administrator. The program should look like this.

![image](https://github.com/user-attachments/assets/feb489e3-aded-47a2-8753-6e91ca0c2f71)

Next, we need to register PHP within IIS. Click on 'PHP Manager'.

![image](https://github.com/user-attachments/assets/7508c5e4-a79a-4a7b-9413-87e9eadd1817)

Register a new PHP version.

![image](https://github.com/user-attachments/assets/0918de90-0fc8-4dd7-af1a-046fc1c7eef1)

You will need to provide the path to the PHP executable file (php-cgi.exe). Navigate to C: Drive -> PHP -> and select the php-cgi.exe file.

![image](https://github.com/user-attachments/assets/2968812c-0672-4b55-a87b-d610623e94b6)

Restart the IIS server.

![image](https://github.com/user-attachments/assets/6f2be16d-7791-4390-9c14-42ebbd2de345)

Install osTicket v1.15.8:

1. Download osTicket from the Installation Files folder.

![image](https://github.com/user-attachments/assets/be48a0f9-8aa1-472e-99c9-e86257de91fa)

2. Extract the files and copy the 'upload' folder to `C:\inetpub\wwwroot`.
   
3. Within `C:\inetpub\wwwroot`, rename the 'upload' folder to 'osTicket'.

Reload IIS again.

![image](https://github.com/user-attachments/assets/e4f90e1f-f142-414c-ab5c-6639e85d2836)

On IIS, navigate to Sites -> Default -> osTicket. On the right side, click 'Browse *:80.'

![image](https://github.com/user-attachments/assets/caa09bfe-37c0-4420-b2d1-4f028b6ee0ef)

Some extensions are not enabled for osTicket in the browser.

![image](https://github.com/user-attachments/assets/cf4c4c35-fe1b-493a-8ef6-285f52068012)

To enable the extensions:

1. Go back to IIS, navigate to Sites -> Default -> osTicket.
2. Double-click 'PHP Manager.'
3. Click 'Enable or disable an extension.'

![image](https://github.com/user-attachments/assets/f7ff4044-2401-401f-8650-c88263c8fcb7)

From here, enable the following three extensions:

1. `php_imap.dll`
2. `php_intl.dll`
3. `php_opcache.dll`"

![image](https://github.com/user-attachments/assets/407a5c23-4071-4c30-9d06-d9b996b582fa)

Once the extensions are enabled in IIS, you need to rename a file in the osTicket folder. Open File Explorer and navigate to `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`.

Rename `ost-sampleconfig.php` to `ost-config.php`.

Now that the files are renamed, right-click on `ost-config.php` and select 'Properties.' 

1. Go to the 'Security' tab.
2. Click 'Advanced.'
3. Disable inheritance by selecting 'Remove all inherited permissions from this object.'

Next, we will add new permissions:

1. Click 'Add.'

![image](https://github.com/user-attachments/assets/8547bf28-9415-420b-8ea8-270b27cfb6c6)

2.Select a principal.

![image](https://github.com/user-attachments/assets/574ee0ac-14f3-4f81-9a4d-bc518b81fab4)

Type 'Everyone' in the box.

![image](https://github.com/user-attachments/assets/81c22bb4-f282-4879-bc34-c011ff98bf2e)

Make sure 'Full Control' and all other checkboxes are selected.

![image](https://github.com/user-attachments/assets/a8e282f9-9431-4a00-a5c3-2e3829e50168)

Click 'Apply' and then 'OK.

![image](https://github.com/user-attachments/assets/aff6a3c7-e3d7-487a-8704-e2f0f035d1c6)

Once that is done, continue setting up osTicket in the browser. Click 'Continue' on the osTicket page. Fill out the form as required, except for the Database Settings at the bottom of the page; we will address that later.

Next, download and install HeidiSQL from the Installation Files.

![image](https://github.com/user-attachments/assets/681f21db-9db7-4bac-8479-274aaa801066)

When the program is open, create a new session.

![image](https://github.com/user-attachments/assets/51c14906-c59d-4ea0-9fc4-a1369fab5f0a)

Ensure that the username is `root` and the password is `Password1`.

![image](https://github.com/user-attachments/assets/3617cfc8-1c5c-4d97-a950-508365432072)



Once connected to the session, return to the browser to complete the setup. In the Database Settings section, use `root` as the username and `Password1` as the password.

Next, create a new database in HeidiSQL. Right-click on the left panel where it says 'Unnamed,' select 'Create New,' and then choose 'Database.' Name the new database `osTicket`. 

After setting up the new database, return to the osTicket browser and enter `osTicket` under MySQL Database.

![image](https://github.com/user-attachments/assets/f899c683-0c39-4453-a42b-4a0b78dd5f26)

![image](https://github.com/user-attachments/assets/698b9d88-7c0f-4cd2-997c-48f1f9b62d89)

The final step is to perform some cleanup. 

1. Delete the setup folder from the system: `C:\inetpub\wwwroot\osTicket\setup`. Make sure to delete only the setup folder and nothing else.

2. Restore the permissions on the `ost-config.php` file to 'Read' only.

![image](https://github.com/user-attachments/assets/f5ee4087-5136-45b9-bb79-7b9cad7a9847)

![image](https://github.com/user-attachments/assets/e90f2a91-e3d6-444c-ad51-86fbf2564f97)

![image](https://github.com/user-attachments/assets/ad3d15c6-7e15-4adb-8f83-3fe0049fdb35)

Congratulations! You have now successfully installed and set up osTicket!























<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
