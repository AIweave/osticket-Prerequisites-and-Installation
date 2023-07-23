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


- Once the window pop-up, click on "Internet Information Services" drop tab -> World Wide Web Services -> Application Development Features ->
    
	[X] CGI

	[X] Common HTTP Features

![Screen Shot 2023-07-23 at 4 01 31 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/d2a8b447-0bbb-490e-851e-a8d004acab22)

- Now, enable IIS Management Console by going to Internet Information Services -> Web Management Tools ->

	[X] IIS Management Console

![Screen Shot 2023-07-23 at 6 39 46 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/8a0faaa5-7126-4887-864c-396acd98d611)



  - From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

  - From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)

  - Create the directory C:\PHP by creating an empty folder inside of Window's Directory (C:) within the "File Explorer" located at the bottom of the screen.

![Screen Shot 2023-07-23 at 6 50 21 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/56416b13-1371-4b94-9766-a812876e73f4)


From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip or the recommended version) and unzip the contents into C:\PHP

From the Installation Files, download and install VC_redist.x86.exe.

From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Password1

Open IIS as an Admin

Register PHP from within IIS

Reload IIS (Open IIS, Stop and Start the server)

Install osTicket v1.15.8
Download osTicket from the Installation Files Folder
Extract and copy “upload” folder to c:\inetpub\wwwroot
Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browse, observe the changes

Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

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

Notes:
Browse to your help desk login page: http://localhost/osTicket/scp/login.php  
End Users osTicket URL: http://localhost/osTicket/ 

Part 3 (Post Installation Setup)
Configure Roles
Admin Panel -> Agents -> Roles
Supreme Admin
Configure Departments
Admin Panel -> Agents -> Departments
System Administrators
Configure Teams
Admin Panel -> Agents -> Teams
Level I Support
Level II Support
Allow anyone to create tickets
Admin Panel -> Settings -> User Settings
Registration Required: Require registration and login to create tickets 
Configure Agents (workers)
Admin Panel -> Agents -> Add New
Jane
John
Configure Users (customers)
Agent Panel -> Users -> Add New
Karen
Ken
Configure SLA
Admin Panel -> Manage -> SLA
Sev-A (1 hour, 24/7)
Sev-B (4 hours, 24/7)
Sev-C (8 hours, business hours)
Configure Help Topics
Admin Panel -> Manage -> Help Topics
Business Critical Outage
Personal Computer Issues
Equipment Request
Password Reset

Part 4 (Tickets and Ticket Lifecycle)
Just practice creating, triaging, and solving tickets. I recommend watching the video to learn about triaging multiple tickets.
Ticket examples:
Sev-A (1 hour, 24/7) [entire mobile/online banking system is down] -> SysAdmins
Sev-B (4 hours, 24/7) [accounting department needs adobe upgrade, broken]
Sev-B/C (2 hours, business hours) [CFO’s laptop seems a bit slow]

