<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This repository provides a comprehensive guide covering the prerequisites and installation process of the open-source help desk ticketing system, osTicket, on a virtual machine.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create a Windows 10 Virtual Machine with Azure Portal
- Install and Enable IIS
- Download and install dependencies
- Register PHP from within IIS
- Install osTicket


<h2>Installation Steps</h2>

<p>
Utilizing the Azure Portal, you can initiate the process bt creating a Windows 10 Virtual Machine equipped with 4 vCPUs. During the Virtual Machine creation, it's important to establish a new resource group named as "osTicket-RG" for organizational purposes. Furthermore, designate the virtual machine with the name "VM-osTicket" to maintain clarity and organization within your Azure resources. Upon the successful creation of both the reasource group and the virtual machine, you can proceedby logging in to the newly established machine using Remote Desktop. This series of steps ensures the systematic setup and accessibility of the virtual machine for further configuration and use.
</p>
<br />

![rdp](https://github.com/NicholasLudwig/osticket-prereqs/assets/104456331/68f70468-491a-492f-be03-98c7fe46b057)

<br />

<p>
To install and configure IIS, navigate to the Control Panel > Programs > Turn Windows features on or off. In the Windows features pane, navigate to Internet Information Services > Web Management Tools and check the box for IIS Management Console. Expand Web Management Tools and ensure IIS Management Console is checked. Expand World Wide Web Services > Application Development Features, and check the box for CGI. Check the box for Common HTTP Features and make sure all boxes are checked. 
</p>
<br />

![enable-iis-all](https://github.com/NicholasLudwig/osticket-prereqs/assets/104456331/1cf361d5-fec6-452b-bad1-e711fedca81d)

<br />
<p>
Test these changes by opening a web browser and entering 127.0.0.1. You should see the following image.
</p>
<br />

![test-iis](https://github.com/NicholasLudwig/osticket-prereqs/assets/104456331/dd9207a1-c49f-4f67-9ff1-9dbc8ecc4da6)

<br />

<p>
Once all the dependencies (PHP Manager, MySQL, etc) have been downloaded and installed, open IIS as an administrator.
</p>
<br />

![iis-admin](https://github.com/NicholasLudwig/osticket-prereqs/assets/104456331/5751a0e9-d56a-452d-85c8-95e069f0a8d4)

<br />
<p>
From within IIS, open PHP Manager > Register new PHP version by navigating to the folder where the dependencies were installed. Reload the server.
</p>
<br />

![php-setup](https://github.com/NicholasLudwig/osticket-prereqs/assets/104456331/e6b9c5e7-c568-4b42-b3a6-815b0c19ff81)

<br />

<p>
Download osTicket and extract the folder "upload" into C:\inetpub\wwwroot and rename it to "osTicket" ensuring there are no typos or spaces in the file name. Go back into IIS > Sites > Default > osTicket and click Browse *80.
</p>
<br />

![ost-browse80](https://github.com/NicholasLudwig/osticket-prereqs/assets/104456331/65e70fb1-84fa-4c2e-b39e-ae42f85fc08c)

<br />

<p>
osTicket Installer should open in the browser displaying currently enabled extensions.
</p>
<br />

![osticket-1](https://github.com/NicholasLudwig/osticket-prereqs/assets/104456331/49e7f33b-62f2-457f-a521-0ac7fea59d70)

<br />
<p>
Go back to IIS > Sites > Default > osTicket and double click PHP Manager. Once inside PHP Manager, enable the following extensions:
  <ul>
    <li>php_imap.dll</li>
    <li>php_intl.dll</li>
    <li>php_opcache.dll</li>
  </ul>
</p>
<p>
Refresh osTicket in the browser and observe the changes.
</p>
<br />

![ext-install](https://github.com/NicholasLudwig/osticket-prereqs/assets/104456331/7945ce83-ca01-4a53-ba67-14398e92a98d)

<p>
In the file directory C:\inetpub\wwwroot\osTicket\include, rename ost-sampleconfig.php to ost-config.php. Assign permissions to this file by right clicking > Properties > Security > Advanced. Allow full permission to everyone.  
</p>
<br />
<p>
Download and install HeidiSQL and create a new session using the credentials from installing MySQL. Once connected to the session, create a new database named osTicket. Continue setup for osTicket in the browser and finish installing.
</p>
<p>
Verify correct installation by going to <a href="http://localhost/osTicket/scp/login.php">osTicket Login</a> and entering the credentials created in the previous steps.
</p>

</p>
