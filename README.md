<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>

This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

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

<h2>Instructions</h2>

**Part 1 (Create Virtual Machine in Azure)**
- Create a Resource Group in Azure
- Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
    
![Screen Shot 2023-07-23 at 3 49 33 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/23c8b658-b930-4e63-8281-a0131e9a29ce)

    
**Part 2 (Installation)**

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


**Part 3 (Install osTicket v1.15.8 or the recommended veerion)**
  
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

**Part 4 (Assign Permissions: ost-config.php)**
  
- To change permissions, first disable inheritance: 

  *right click "ost-config" (in File Explore) -> select "Properties" -> "Security" tab at the top -> select the "Advanced" -> "Disable inheritance" -> "Remove All"*

![Screen Shot 2023-07-23 at 7 53 02 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/314e7e46-6fd7-436e-9f3e-5074faf982e3)

- Now apply new permissions:

  *"Select a principal" -> Under "Enter the object name to select" type "Everyone" -> select "Check Names" -> click "OK" -> seclect "Full Control" under "Basic Permissions" -> "Apply" -> "OK"*

![Screen Shot 2023-07-23 at 7 58 21 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/885d14e3-7bf8-4690-a820-e1f1e23ee95a)

![Screen Shot 2023-07-23 at 7 58 29 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/81964826-a7a7-4787-90fb-596102f9033e)

![Screen Shot 2023-07-23 at 8 06 50 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/dcb103e4-ae2e-47d0-9808-ec46adcc145c)


- From the Installation Files, download and install HeidiSQL.
- Open Heidi SQL

![Screen Shot 2023-07-23 at 8 12 24 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/e7de4adb-c552-4f9c-9cd0-b7b978bbcbb2)

- Create a new session, username, and Password1.  For an example, user: root, password: Password1. This information will be entered in osTicket's browser setup.

![Screen Shot 2023-07-23 at 8 12 36 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/176639a9-385e-4b1d-9bd2-eebe0e784c4a)

  
- Connect to the session.
- Create a database called “osTicket”

![Screen Shot 2023-07-23 at 8 13 31 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/c02a4b07-cfc5-43b0-ac63-61e22e80b38c)

![Screen Shot 2023-07-23 at 8 13 56 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/65d226a3-dd88-45b5-9506-c04bc6d08905)

- Continue Setting up osticket in the browser with information created in Heidi SQL.

*MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1* 

- After completing the osTicket's setup on the browser, click “Install Now!”
  
![Screen Shot 2023-07-23 at 8 43 31 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/837efdac-7b90-4b58-86f8-c5fc7bbd9b15)


**Part 5 (Clean up)**

- Return to "File Explorer" and follow the this directory to delete the following:

Delete: *C:\inetpub\wwwroot\osTicket\setup*

![Screen Shot 2023-07-23 at 8 26 53 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/4a432a22-3887-48f7-9ba7-c2a9340d079d)

- Set Permissions to “Read” only by returning to ost-config.php at: 

*C:\inetpub\wwwroot\osTicket\include\ost-config.php*

- Next, apply the following settings:
  
*right click "ost-config" (in File Explore) -> select "Properties" -> "Security" tab at the top -> select the "Everyone"*

![Screen Shot 2023-07-23 at 8 32 44 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/c80d9081-0fe2-4752-8b32-3d557a51fbc4)

*"Edit" -> remove all checks except for "Read" and "Read & execute -> "OK" -> "Apply" ->"OK*

![Screen Shot 2023-07-23 at 8 32 58 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/76fe91d3-8499-409a-bfe3-9f55ec021bf4)

![Screen Shot 2023-07-23 at 8 33 27 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/d4139fa0-1f59-4dc4-99b0-adab03904e93)


Browse to your help desk login page: http://localhost/osTicket/scp/login.php

![Screen Shot 2023-07-23 at 8 33 46 PM](https://github.com/AIweave/osticket-Prerequisites-and-Installation/assets/121763338/e4a47c46-94f9-41f9-b3b2-cb2f8da3117a)
