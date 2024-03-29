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

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Steps</h2>

1.) Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs by going to https://portal.azure.com/
<p>
<img src="https://i.imgur.com/dyeqebs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

2.) Once created use the public ip address of the Virtual Machine to connect through the remote desktop connection app.
<p>
<img src="https://i.imgur.com/YGmjsM8.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>

3.) On your Virtual Machine go to the Control Panel, open Programs and select Turn Windows features on and off.
<p>
<img src="https://i.imgur.com/XcHY4Kh.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
4.) Install / enable IIS in Windows with CGI, Common HTTP Features and IIS Management Console.</p>
    - World Wide Web Services > Application Development Features > [x] CGI [X] Common HTTP Features. 
<p>
<img src="https://i.imgur.com/4RvUDIe.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>
<p>
    - Internet Information Services > Web Management Tools > [x] IIS Management Console 
<p>
<img src="https://i.imgur.com/5tJDdHZ.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>
<p>
NOTE: Make sure all Common HTTP Features are checked.
</p>
To make sure the IIS is installed / enabled go to a browser of your choice and search for 127.0.0.1 It should look something like this.
<p>
<img src="https://i.imgur.com/TAHSEaa.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
5.) From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi).</p>

6.) From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)</p>

7.) Create a folder in the C drive called PHP.</p>

8.) From the Installation Files, download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) and unzip the contents into C:\PHP
<p>
9.) From the Installation files, download and install the VC_redist.x86.exe.</p>

10.) From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi):</p>
- Typical Setup ->
- Launch Configuration Wizard (after install) ->
- Standard Configuration ->
</p>
Make the new root password: Password1
<p>    
<img src="https://i.imgur.com/PqcKcXV.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
Execute the process on the following page.
<p>
<img src="https://i.imgur.com/gcnbdoM.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
11.) Now that we have all the files downloaded and installed, we will search for IIS in the windows search bar and Open IIS as an administrator.
<p>
<img src="https://i.imgur.com/PQYsN4F.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
12.) We want to register PHP from within IIS. Click on PHP Manager.
<p>
<img src="https://i.imgur.com/2qLhS5m.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
- Register new PHP version.
<p>
<img src="https://i.imgur.com/78PN35f.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
- Provide a path to the php executable file (php-cgi.exe)). Go to C Drive -> PHP -> click on php-cgi file.
<p>
<img src="https://i.imgur.com/qbIaYDy.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>
- Restart the IIS server.
<p>
<img src="https://i.imgur.com/njBDLU4.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
13.) From the Installation Files, download and Install osTicket v1.15.8</p> 
    - Move "upload folder" to c:\inetpub\wwwroot.<p> 
    - Rename "upload folder" to "osTicket".</p>
      Restart IIS again.
</p>
14.) Open osticket installer
</p>
On IIS go to vm-osticket -> sites -> Default Web Sites -> osTicket - then on the right, click on “Browse *:80”.
</p>
<img src="https://i.imgur.com/9H9umEl.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Some extensions are not enabled on the osTicket browser.
</p>
<img src="https://i.imgur.com/7Qiv4sd.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
Enable the extensions by going back to IIS: vm-osticket -> sites -> Default Web Sites -> osTicket.
</p>
- Open PHP manager then click "Enable or disable an extension".
<p>
<img src="https://i.imgur.com/5kTdTqQ.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
We will enable the following extensions: php_imap.dll, php_intl.dll, php_opcache.dll.
<p>
<img src="https://i.imgur.com/AGKbpSU.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Refresh osticket installer
<p>
<img src="https://i.imgur.com/ZJqVJCN.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>    
15.) Rename: ost-config.php
</p>
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
Once renamed, right click on the file and go to properties. From the ost-config.php Propeties, click on security, then advanced, and disable the inheritance. We will select Remove all inherited permissions from this object. 
<p>
<img src="https://i.imgur.com/4wp0nvP.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/gkVSBX9.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we will add new permissions, click on Add.
<p>
<img src="https://i.imgur.com/TEuhMwQ.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Select a principal and enter "everyone" in the box.
<p>
<img src="https://i.imgur.com/J9pjPkL.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Make sure full control and all the other boxes are checked.
</p>
<img src="https://i.imgur.com/DkBpfZp.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click Apply and Ok.
</p>
<img src="https://i.imgur.com/OSfeN5n.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once done we will continue to setup osTicket in the browser by clicking to ¨Continue¨. Fill out the page as required except the Database Settings at the bottom of the page, we will fill that later.
</p>
<img src="https://i.imgur.com/g2Lmr7k.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
</p>
<img src="https://i.imgur.com/AS3EgcZ.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
16.) From the Installation Files, download and install HeidiSQL.
</p>
- Open Heidi SQL
<p>
<img src="https://i.imgur.com/eqJoqj8.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
- Create a new session, root/Password1
<p>
<img src="https://i.imgur.com/aPz1uAL.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/ORwQpl9.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
- Once we are connected to the session, we will now create a new database called “osTicket”
<p>
<img src="https://i.imgur.com/2ZY10hE.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/bKPXTfg.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/WxBzMiw.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
We can now fill the Database Settings at the botton on the osTicket installer in the browser, and install now.
</p>
<img src="https://i.imgur.com/P2JjGTa.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/drC5EJA.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Before login to osTicket on the browser, we first ne to do some clean up:
</p>
- Delete the file setup: C:\inetpub\wwwroot\osTicket\setup
<p>
- Set Permissions to “Read” only on ost-config.php: C:\inetpub\wwwroot\osTicket\include\ost-config.php
<p>
<img src="https://i.imgur.com/BS8MhKv.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/DgKnOe5.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/nJjNuln.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
Last action, browse to your help desk login page: http://localhost/osTicket/scp/login.php
<p>
<img src="https://i.imgur.com/8ADGSu4.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
Congratulations, you have successfully installed and setup osTicket!
