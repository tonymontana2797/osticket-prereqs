# OS-Ticket-Pre-Reqs 
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure Virtual Machine
- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)


<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2> List of Prerequisites </h2> 

-   PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) (https://www.iis.net/downloads/community/2018/05/php-manager-150-for-iis-10)
-   Rewrite Module (rewrite_amd64_en-US.msi)(https://www.iis.net/downloads/microsoft/url-rewrite)
-   PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip)
-   VC_redist.x86.exe (https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170)
-    MySQL 5.5.62 (mysql-5.5.62-win32.msi) (https://downloads.mysql.com/archives/community/)
-    HeidiSQL (https://www.heidisql.com/download.php) 

<h2> Installation Steps </h2>  

<h2> Create Virtual Machines on Azure </h2>  

<br />
<p>
	Create a Resource Group
</p>
<p>
	  

https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/567e07cf-0f82-4dbb-9b00-0b2681888fdb



</p>
<p>
	Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
	When creating the VM, allow it to create a new Virtual Network (Vnet):

</p>
<p>
         <img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/5f750521-21f7-40af-a2fe-f747d40272a3"/>

</p>

<br /> 
<br />
<h3> Connect to your Virtual Machine with Remote Desktop</h3>
<br />
<p>
	-If using PC, use Remote Desktop Connection
        
</p>
<p> 
      -If using Mac, use Microsoft Remote Deskop
</p> 

<p>  
      -Use the VM public IP address to connect, along with username and password that you used when VM was created.
</p>
	
<p>
	<img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/318d1ba2-8130-47f6-b56a-19d18dee3d06"/>
</p>
<br />
<br />
<h3>  Install and Enable IIS in Windows </h3>
<br />
<p>
      -Within the VM Windows Machine, go to Control Panel and Programs 
      
</p>	

<p>
	-When in the Programs, go to Turn Windows features on or off 

</p> 
    
<p>
    - World Wide Web Services -> Application Development Features ->  [X] CGI
    [X] Common HTTP Features


</p> 

<p>    -   -> Internet Information Services -> Web Management Tools -> IIS Management Console
	[X] IIS Management Console

</p> 
<p>
	
	
https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/03ae682d-9c67-4c7c-9f4c-6f629807ef7f

</p>
<br />
<br />
<h3>Install Dependencies</h3>
<br />

<p>
     -Download PHP manager for IIS 
</p>
<p>
     -Download Rewrite Module
</p> 

<p> 
   -Create the directory C:\PHP
</p> 	
<p>
   - Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP

</p>

<p> 
    -Download and install VC_redist.x86.exe.

</p> 
<p> 
    -Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)


</p> 

<p>
	-Add MySQL 5.5 

Name: root

Password: Password1:
</p>

<p>
      - Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

</p>
<p>
	<img src="https://github.com/user-attachments/assets/610e341c-3cd0-4490-b46a-eae4033607ac"/>
</p>
<p>
    - Open IIS as an Admin, Reload IIS (Open IIS, Stop and Start the server)


</p> 
<p>
	<img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/06ec3624-c223-42d1-8155-03fe8ed46fdc"/>

	
</p>
<br />
<br />
<h3>Install osTicket v1.15.8</h3>
<br />

<p>
	-Download osTicket 
</p>
<p>
       -Extract and copy the “upload” folder to c:\inetpub\wwwroot

</p> 
<p>
	<img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/28222cd0-273f-4ed9-a0f2-6514e9d0b44e"/>

</p>
<p>
     - Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
</p>
<p>
	<img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/f21e9869-8cc7-41d2-8ae9-f89e10900c34"/>
</p>

<br />
<br />
<h3>Reload IIS (Open IIS, Stop and Start the server)</h3>
<br />
<p>
 Go to sites -> Default -> osTicket:
</p>
<p>
	<img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/1f0fad17-d033-4455-b669-9f30c4dc9bb3"/>

	
</p>
<p>
	On the right, click “Browse *:80”:
</p> 

<p>
	

https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/48374172-ef6d-4409-bc35-bffa97e430a8

</p>
<br />
<br /> 
<h3>Enable Extensions in IIS: Note that some extensions are not enabled</h3>
<br />
<p>
	Go back to IIS, sites -> Default -> osTicket.
</p>

<p>
	Double-click PHP Manager:
</p>

<p>
	Click “Enable or disable an extension”.
</p>
<p>
	Enable: php_imap.dll.
</p>
<p>
	Enable: php_intl.dll.
</p>
<p>
	Enable: php_opcache.dll:
</p>
<p>
	<img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/3ad0691a-87f8-4ab0-9211-1e657811c603"/>

</p> 

<br />
<br />
<h3>Refresh the osTicket site in your browser, observe the changes</h3>
<br />
<p>
	<img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/394c0284-2288-4121-aa2a-d08af996d035"/>
</p>
<br />
<br />
<h3>Rename</h3>
<br />
<p>
	From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php to C:\inetpub\wwwroot\osTicket\include\ost-config.php

</p> 
<p>

https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/fd7c722d-bb8a-489c-9da6-4ee1c2ac4798


</p> 
<br />
<br />
<h3>Assign Permissions: ost-config.php</h3>
<br />
<p>
	Disable inheritance -> Remove All:
</p> 

<p>
	<img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/7dd5bd6a-13c2-4ecd-bf9c-8a8587a92bae"/>

</p> 
<p>
	New Permissions -> Everyone -> All:
</p>
<p>
	

https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/4d4eb92d-e9e9-42dc-9b26-c9f0643b14c0

</p> 
<br />
<br />
<h3>Continue Setting up osTicket in the browser</h3>
<br />
<p>
	Name Helpdesk
</p>
<p>
	Default email 
</p>
<p>
	<img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/b60c93c5-4a9f-4a79-af7e-3446333cc4b4"/>
</p> 
<br />
<br />
</h3>Download and Install HeidiSQL</h3>
<br />
<p> 
     <img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/ca5e20e6-0c04-4522-af2e-375e118174ae"/>
</p> 
<p>
	Create a new session, root/Password1.
<p> 
        Connect to the session:
</p> 
    <img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/9fe8b85e-53c7-4c1f-af85-02ff4b93d7fe"/>
</p>
<p>
	Create a database called “osTicket”:
</p>
<p>
	<img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/9e9143cf-e4c5-4fc2-82e8-20017fa30c2e"/> 

</p>
<br />
<br />
<h3>Continue Setting up osTicket in the browser</h3>
<br />
<p>MySQL Database: osTicket</p>
<p>
	MySQL Username:
</p>
<p>
	MySQL Password:
</p> 
<p> 
	Click “Install Now!”

</p>
<p> 
	Congratulations, hopefully, it is installed with no errors! 

</p>  

<p>
	<img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/47a0789c-b71e-4427-b3ad-46403b901d5c"/> 
</p>
<br />
<br />
<h3>Clean up</h3>
<br /> 
<p>
	Delete: C:\inetpub\wwwroot\osTicket\setup:
</p>

<p>
	<img src="https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/24ead4c5-bcaf-4b45-b3f2-0aa35d2c0ae1"/>  

</p> 

<p>
	Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php:
</p> 
<p>
	

https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/19d4ae86-a445-4e38-bb88-e8d853e23368


</p> 

<br />
<br />
<h3>Login to the osTicket Admin Panel (http://localhost/osTicket/scp/login.php)</h3>
<br />
<p> 
      

https://github.com/ethansevilla/OS-Ticket-Pre-Reqs/assets/170621372/d8fb8409-48f8-4f7a-a02a-51a3e89592da 
</p> 

<br />
<br />
<p>
	Setting up and installing osTicket is done! I hope this tutorial helped you with installing osTicket.
</p>


