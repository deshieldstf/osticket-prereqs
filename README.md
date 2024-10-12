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

- Windows 11</b> (22H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- osTicket Installation Files
- Heidi SQL

<h2>Installation Steps</h2>

We'll create a Virtual Machine (VM) using the Microsoft Azure portal. We will be using a VM which is a remote computer. We are using a VM in order to protect our physical machine just in case something breaks. Create a resource group and title it "osTicket". Afterwards, create a VM with 2-4 VCPUs with 8GB ram. In this example I will be using 2 VCPUs.

<img width="467" alt="Screenshot 2024-10-11 at 6 07 17 PM" src="https://github.com/user-attachments/assets/e00d9d7c-972c-417d-a194-01646780b28f">

<img width="459" alt="Screenshot 2024-10-11 at 6 07 29 PM" src="https://github.com/user-attachments/assets/ad6285f6-d89b-4068-b8b2-a4dff8e9aa9f">



Next, connect to your newly created VM using RDP using the public IPv4 address. If you are a Mac, user you will have to download _Windows App_, previously known as Microsoft RDP.

<img width="1144" alt="Screenshot 2024-10-11 at 6 12 29 PM" src="https://github.com/user-attachments/assets/a8a3d9e5-7a9b-47f3-aeff-5e2090f4a89d">



Now that you are connected to your VM, you will have to enable Internet Informations Server (IIS) which is a webserver that will be serving up OS Ticket. Access the _Control Panel_ then select _Uninstall a Program_ under 'Programs'. Off to the left select "Turn windows features on or off". A list will appear then you will enable _Internet Information Services_ <b>WITH CGI </b>.

<img width="563" alt="Screenshot 2024-10-11 at 6 25 06 PM" src="https://github.com/user-attachments/assets/c39a64bd-8a33-4baa-94cb-7b4d3a8add90">



Now that you have enabled IIS, we need to install Web Platform Installer. I have provided a link here: https://drive.google.com/drive/folders/1b80Cfj42RsL2K-iELi_oJdokMil6Oupt?usp=drive_link
That link will provide you with all of the material you need to download to get osTicket up and running. 

<img width="1121" alt="Screenshot 2024-10-11 at 6 41 09 PM" src="https://github.com/user-attachments/assets/89d9551a-346c-49af-aae5-12db9b08bd17">



Next, install "PHPManagerforIIS" and "Rerwite_amd64"

<img width="496" alt="Screenshot 2024-10-11 at 6 39 21 PM" src="https://github.com/user-attachments/assets/7d3d2180-6d58-4f76-b13d-4a19ab663d6c">

<img width="493" alt="Screenshot 2024-10-11 at 6 40 35 PM" src="https://github.com/user-attachments/assets/3b5feba0-84bf-4e0a-97c7-d5bfe3307619">



Next we will create the directory C:\PHP and extract the PHP files into the new folder we create.

<img width="808" alt="Screenshot 2024-10-11 at 6 50 52 PM" src="https://github.com/user-attachments/assets/2e10fcef-9622-4b24-bc33-95a127dabb3c">

<img width="809" alt="Screenshot 2024-10-11 at 6 50 59 PM" src="https://github.com/user-attachments/assets/ddc98056-90d1-4c91-8a37-d3a24c3990bd">



Afterwards, install Visual C++ and MySQL.

<img width="478" alt="Screenshot 2024-10-11 at 6 54 05 PM" src="https://github.com/user-attachments/assets/9120a9d0-2205-4a9c-aedc-cfd322081dcd">

<img width="494" alt="Screenshot 2024-10-11 at 6 54 28 PM" src="https://github.com/user-attachments/assets/6ed0532c-ee69-465c-ab15-fd44b63c86bf">



Open IIS and Run as an Administator. Register the PHP from within IIS and reload IIS (Open IIS, Stop and Start the server).

<img width="386" alt="Screenshot 2024-10-11 at 6 59 44 PM" src="https://github.com/user-attachments/assets/2e9803eb-8ef5-4559-ab3e-4cdcf4e9df5d">

<img width="1277" alt="Screenshot 2024-10-11 at 7 03 51 PM" src="https://github.com/user-attachments/assets/eb9fc3b8-1656-46f2-bcc9-545be03add1e">

<img width="530" alt="Screenshot 2024-10-11 at 7 00 34 PM" src="https://github.com/user-attachments/assets/56e6b8e4-d9df-4dc4-8793-eac1b411407f">

<img width="849" alt="Screenshot 2024-10-11 at 7 00 54 PM" src="https://github.com/user-attachments/assets/6da08eb2-afde-4855-907d-25a1d37687df">

<img width="202" alt="Screenshot 2024-10-11 at 7 05 19 PM" src="https://github.com/user-attachments/assets/5e0a4317-94a2-474f-a028-e1bc27929830">



Now, we are ready to install osTicket. Download osTicket. Then extract and copy the "Upload" folder into:
- c:\inetpub\wwwroot. Afterwards rename the folder to <b>_osTicket_</b>.
Afterwards, reload IIS (Open IIS, Stop and Start the server)

<img width="810" alt="Screenshot 2024-10-11 at 7 12 39 PM" src="https://github.com/user-attachments/assets/4eb138da-ba5b-4f2f-b6aa-3dbe02ffb7cb">



Once inside IIS manager go to Sites > Default > osTicket on the right, click "Browse*.80" from there your default browser should open osTicket webserver.

<img width="1280" alt="Screenshot 2024-10-11 at 7 15 21 PM" src="https://github.com/user-attachments/assets/d3a20fd6-74c6-4a1e-ad91-c0941d6735d3">



Go back into IIS manager and enable some extensions. Click Sites > Default > osTicket. Then double click on PHP manager. Click “Enable or disable an extension”
- Enable: php_imap.dll
- Enable: php_intl.dll
- Enable: php_opcache.dll

<img width="1280" alt="Screenshot 2024-10-11 at 7 19 11 PM" src="https://github.com/user-attachments/assets/91766bfc-e1dc-4cd8-9782-ada27632ae48">



Go back into c:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php and rename the file to:
- c:\inetpub\wwwroot\osTicket\include\ost-config.php
- Assign permissions to ost-config.php
- Disable inheritance->Removeall New Permissions->Everyone->all

<img width="360" alt="Screenshot 2024-10-11 at 7 26 07 PM" src="https://github.com/user-attachments/assets/6032341c-2483-406e-9cab-d0a9ae7ca1bb">


Afterwards continue setting up osTicket in the browser (click Continue) then you will name the Helpdesk to your liking. Select a default email that will receive emails from customers who submit tickets. Continue Setting up osticket in the browser.

- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: Password1
- Click “Install Now!”

<img width="847" alt="Screenshot 2024-10-11 at 9 41 46 PM" src="https://github.com/user-attachments/assets/ea0f53c2-94f9-40b3-9857-b064d3f063f1">

You have successfully installed osTicket!

Clean up 
- Delete: C:\inetpub\wwwroot\osTicket\setup
- Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
