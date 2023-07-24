<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>

This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

**Must Know** - Software and applications in "Instructions" may vary in versions based on updates and user's computer.

<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Microsoft Remote Desktop 
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b>

<h2>List of Prerequisites</h2>

- Web Server: Apache or IIS.
- PHP Versions:
- osTicket Version 1.15+ 
- MySQL Database: 5.5+

- <h2>Instructions</h2>

- **Part 1 (Create Virtual Machine in Azure)**
  - Create a Resource Group in Azure
  - Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
    
![Screen Shot 2023-07-23 at 3 49 33 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/23c8b658-b930-4e63-8281-a0131e9a29ce)

    
- **Part 2 (Installation)**

- Install / Enable IIS in Windows with CGI and Common HTTP Features by accessing the "Control Panel" in Windows. Then click on "Programs" and "Turn on Windows features on or off" under "Programs and Features" afterwards.
 
![Screen Shot 2023-07-23 at 3 56 37 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/36ee57ef-59fd-4d5f-b727-27d06da6b2c9)


- Once the window pop-up, click on:

   *Internet Information Services (drop tab) -> World Wide Web Services -> Application Development Features ->*
    
	[X] CGI

	[X] Common HTTP Features

![Screen Shot 2023-07-23 at 4 01 31 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/d2a8b447-0bbb-490e-851e-a8d004acab22)

- Now, enable IIS Management Console by going to:

   *Internet Information Services -> Web Management Tools ->*

	[X] IIS Management Console

![Screen Shot 2023-07-23 at 6 39 46 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/8a0faaa5-7126-4887-864c-396acd98d611)



  - From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

  - From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)

  - Create the directory C:\PHP by creating an empty folder inside of Window's Directory (C:) within the "File Explorer" located at the bottom of the screen.

![Screen Shot 2023-07-23 at 6 50 21 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/56416b13-1371-4b94-9766-a812876e73f4)


- From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip or the recommended version) and unzip the contents into C:\PHP

- From the Installation Files, download and install VC_redist.x86.exe.

- From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi or recommended version). Within the installation, choose the following options when they appear:
  
	*Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration -> (create a password) (as shown below)*

![Screen Shot 2023-07-23 at 7 03 51 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/f2b70b08-58d3-46a7-88a7-3b638cd6e5dc)


- Open IIS as an Admin by entering "ISS" in the search box of the home screen.  Select "Run as administrator".


![Screen Shot 2023-07-23 at 7 11 28 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/242ba71a-f2f6-4cb6-8f32-a9c09100a099)


- Select "PHP Manager" once ISS Manager appears and click on "Register new PHP version" to register PHP.

![Screen Shot 2023-07-23 at 7 14 55 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/a887fe54-c5eb-4cef-96a8-5a23e2b88928)

- Upload the PHP (C:\PHP) folder that was created previously into entry box.

![Screen Shot 2023-07-23 at 6 50 21 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/56416b13-1371-4b94-9766-a812876e73f4)
 
- Open IIS, Stop, and Start the server

  ![Screen Shot 2023-07-23 at 7 21 30 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/58b7af7a-71ad-42e4-b9ce-db7582da3592)


- **Part 3 (Install osTicket v1.15.8 or the recommended veerion)**
  
  - Download osTicket from the Installation Files Folder
  - Extract and copy “upload” folder to c:\inetpub\wwwroot
  - Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

![Screen Shot 2023-07-23 at 7 25 22 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/12150281-f165-4ffb-b68b-0541c0386a34)


- Open IIS, Stop, and Start the server
- Under "Connections" on left side of the screen,
  
  *Go to sites -> Default -> osTicket -> On the right*, click “Browse *:80(http)”

  ![Screen Shot 2023-07-23 at 7 32 31 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/4297b081-15aa-4d51-b3d5-ae935cab6c08)


- Some extensions will not be enabled, so:

  *Go back to IIS, sites -> Default -> osTicket*, Double-click "PHP Manager"

- Click “Enable or disable an extension”

  ![Screen Shot 2023-07-23 at 7 35 38 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/a561b81c-337a-4181-9d97-97837ee7537e)

- Select the following extensions and click "Add" under "Actions" on the right side of the screen.
  
  Enable: php_imap.dll
  
  Enable: php_intl.dll
  
  Enable: php_opcache.dll

![Screen Shot 2023-07-23 at 7 35 23 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/0037e6ff-c177-4ec7-9bc6-77a2c52f25f0)


- Go to [osTicket](http://localhost/osTicket/scp/login.php) site in your browse.

![68747470733a2f2f692e696d6775722e636f6d2f50504e7a6956352e706e67](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/1df3bf7a-5fb9-43d0-8ae1-e3b1724d501b)

- Return to "File Explorer" to rename: ost-config.php
  
  From: *C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php*
  
  To: *C:\inetpub\wwwroot\osTicket\include\ost-config.php*

- **Part 4 (Assign Permissions: ost-config.php)**
  
- To change permissions, first disable inheritance: 

  *right click "ost-config" (in File Explore) -> select "Properties" -> "Security" tab at the top -> select the "Advanced" -> "Disable inheritance" -> "Remove All"*

  ![Screen Shot 2023-07-23 at 7 53 02 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/314e7e46-6fd7-436e-9f3e-5074faf982e3)

- Now apply new permissions:

  *"Select a principal" -> Under "Enter the object name to select" type "Everyone" -> select "Check Names" -> click "OK" -> seclect "Full Control" under "Basic Permissions" -> "Apply" -> "OK"*

  ![Screen Shot 2023-07-23 at 7 58 21 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/885d14e3-7bf8-4690-a820-e1f1e23ee95a)

  ![Screen Shot 2023-07-23 at 7 58 29 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/81964826-a7a7-4787-90fb-596102f9033e)


Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

From the Installation Files, download and install HeidiSQL.
Open Heidi SQL
Create a new session, root/Password1
Connect to the session
Create a database called “osTicket”

Continue Setting up osticket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1
Click “Install Now!”

Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

End Users osTicket URL:
http://localhost/osTicket/ 

Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Part 4 (Tickets and Ticket Lifecycle)
Just practice creating, triaging, and solving tickets. I recommend watching the video to learn about triaging multiple tickets.
Ticket examples:
Sev-A (1 hour, 24/7) [entire mobile/online banking system is down] -> SysAdmins
Sev-B (4 hours, 24/7) [accounting department needs adobe upgrade, broken]
Sev-B/C (2 hours, business hours) [CFO’s laptop seems a bit slow]

