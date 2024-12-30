<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- https://youtu.be/1Ctyv29vxTs

<h2>Enviroments and Technologies Used</h2>

Microsoft Azure (Virtual Machines/Compute)
Remote Desktop
Internet Information Services (IIS)

<h2>Operating Systems Used</h2>

- Windows 10</b> (21H2)

- <h2>List of Prerequisites</h2>

- Azure Virtual Machine
- osTicket Installation files
- Heidi SQL

- <h2>Installation Steps</h2>

<p>
</p>
<p>
Ok, welcome to my first tutorial! First things first we will have to create a Virtual machine using the Microsoft Azure portal. We will be using a VM which is a remote computer. We are using a VM in order to protect our physical machine just in case something breaks. Create a resource group and title it "osTicket". Afterwards create a VM with 2-4 CPUs. In this example I will be using 2 CPUs.
  
<img src="https://i.imgur.com/epHDY1R.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<p>
</p>
<p>Next simply connect to your newly created VM using RDP using the public IPv4 address. If you are a Mac user you will have to download Microsoft RDP. 
</p>
<img src="https://i.imgur.com/clhm8RF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
</p>
<p>
Alright, now that you are connected to your VM you will have to enable IIS. Simply access the control panel then select uninstall a program. Off to the left select "Turn windows features on or off". A list will appear then you will enable Internet Information Services.
</p>  
<img src="https://i.imgur.com/2k1j6WT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
</p>
<p>
  <p>
</p>
Excellent. Now that you have enabled IIS we need to install osTicket-installation-files. I provided the link here: https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD  That link will provide you with all of the material you need to download to get osTicket up and running. Simply click the link and install osTicket-installation-files.

</p>
</p>
<p>
Once you have installed osTicket-installation-files open it. You'll need to unzip onto your desktop. From the osTicket-installation-files folder, install PHP Manager 
</p>  
<img src="https://i.imgur.com/yk0jvoQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
After that you need to install Rewrite Module from the osTicket-installation-files.
</p>
<p>
</p>
<img src="https://i.imgur.com/79GdVbt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
</p>
Next, download VC_redist.x86.exe from the osTicket-installation-files
<img src="https://i.imgur.com/QwQLfig.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
<p>
Next, create the directory C:\PHP
<img src="https://i.imgur.com/zkpMYi6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
<img src="https://i.imgur.com/IoATmsy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
</p>
From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Username: root
Password: root
<img src="https://i.imgur.com/gyBOW1K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
</p>
Open IIS as an Admin

Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

Reload IIS (Open IIS, Stop and Start the server)
<img src="https://i.imgur.com/JUQDqX0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
</p>
Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”
<img src="https://i.imgur.com/NSvNSjr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
</p>
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
Refresh the osTicket site in your browser, observe the changes
<img src="https://i.imgur.com/XzzV7WA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/kFSfUNd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/h48cyOq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
</p>
Next, we have to rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
<img src="https://i.imgur.com/UfqSLeS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
</p>
After that we need to assign permissions: Right click ost-config.php -> Properties -> Security ->  Click advanced ->
Disable inheritance -> Remove All
New Permissions -> Everyone -> All
<img src="https://i.imgur.com/AGeMZ8T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
</p>
From the “osTicket-Installation-Files” folder, install HeidiSQL.
Open Heidi SQL
Create a new session, root/root
Connect to the session
Create a database called “osTicket”
<img src="https://i.imgur.com/5XFyu8r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
</p>
Continue Setting up osTicket in the browser: MySQL Database: osTicket, MySQL Username: root, MySQL Password: root
Click “Install Now!”
<img src="https://i.imgur.com/sEprJTl.png" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
</p>
Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

End Users osTicket URL:
http://localhost/osTicket/ 

