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

Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Steps</h2>

1.) Start by creating a virtual machine at https://portal.azure.com/. Configure it with Windows 10 Pro, version 22H2, and ensure it has at least 2 vCPUs and 16 GB of memory.

2.) After creating your virtual machine, connect to it using its public IP address via the Remote Desktop Connection app.

![Screenshot 2024-12-05 212719](https://github.com/user-attachments/assets/f6b3006f-65f8-47db-905b-a2f42591621c)

![image](https://github.com/user-attachments/assets/2f24d8a9-c3d6-49cf-987c-8b059d9ea0bb)

3.) After connecting to your virtual machine, open the Control Panel, navigate to Programs, and select "Turn Windows features on or off."
  
![image](https://github.com/user-attachments/assets/0add3ffd-3182-4b48-acf8-b2e04f366e2b)


![image](https://github.com/user-attachments/assets/e18c877d-e900-4536-881b-81b2b58397d4)

4.) You will want to install / enable IIS in Windows with CGI and Common HTTP Features

World Wide Web Services -> Application Development Features -> [X] CGI [X] Common HTTP Features

![image](https://github.com/user-attachments/assets/d8d7567e-69f2-4ae7-a546-0e22622f6a4f)

![image](https://github.com/user-attachments/assets/e7905e44-c852-401e-b451-ab602357471e)

To make sure the IIS is installed / enabled go to a browser of your choice and search for 127.0.0.1 It should look something like this.

![image](https://github.com/user-attachments/assets/4c1a42fe-3b22-44f8-8820-f8956b35510c)

5.) Now that the IIS is enabled, From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) Go through the install wizard and complete the install.

![Screenshot 2024-12-08 204111](https://github.com/user-attachments/assets/afa4c638-3fc4-4968-8d2c-4f0c4e836c44)

6.) Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)


7.) After installing the Rewrite Module, create a folder named C:\PHP on the C: drive. Extract the contents of the PHP 7.3.8 zip file (php-7.3.8-nts-Win32-VC15-x86.zip) into the C:\PHP folder.

![image](https://github.com/user-attachments/assets/8918e59b-d847-4d6d-aed3-cefcca5f7aed)

8.) Next, download and install VC_redist.x86.exe from the installation files.

9.) Install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the installation files. In the setup wizard, agree to the terms, choose a Typical install, and proceed with installation.

![image](https://github.com/user-attachments/assets/70dff20b-46f3-48fb-a6e6-92c12138bdfc)

10.) Afterward, launch the Configuration Wizard. Choose Standard Configuration, select Install As Windows Service, and ensure Launch the MySQL Server automatically is checked. Use root as the username and Password1 as the password. For this lab, these simple credentials will suffice.

![image](https://github.com/user-attachments/assets/a9c2e3bc-65c8-4189-8e4b-31edc1af1a98)


11.) Before installing osTicket, configure IIS. Open IIS as an admin and select PHP Manager. Click Register new PHP version, then browse to the php-cgi.exe file in the PHP folder created earlier. After registering the PHP version, reload the IIS server in the management console.

![Screenshot 2024-12-05 213514](https://github.com/user-attachments/assets/d77cb9d3-edfb-4dae-b49f-b312e5e4cf1a)

![image](https://github.com/user-attachments/assets/1b860946-1dd9-4a3a-ba55-f7f55960649e)

![image](https://github.com/user-attachments/assets/d82bcc49-17dd-42c8-b6c1-45708115f2ae)

13.) Install osTicket v1.15.8 -Download osTicket from the Installation Files Folder -Extract and copy "upload" folder to c:\inetpub\wwwroot -Within c:\inetpub\root, Rename "upload" to "osTicket"

![image](https://github.com/user-attachments/assets/7a9c3f1e-95bb-44ac-aac8-034b17aad01e)

14.) Clicking on the "Browse*:80" within IIS brings up the installation guide to what settings need to be turned off for osTicket's installation to proceed.

![Screenshot 2024-12-05 213529](https://github.com/user-attachments/assets/f026139d-eadb-480c-afc1-b616f65b1b3e)

15.) Before installing osTicket, enable necessary PHP extensions in the IIS console. In the osTicket menu within IIS, open PHP Manager and click Enable or disable an extension. Enable the following extensions: php_imap.dll, php_intl.dll, and php_opcache.dll.

![Screenshot 2024-12-05 214426](https://github.com/user-attachments/assets/5693d9f6-154a-484c-839c-59e9eeec0706)

16.) After enabling the extensions in IIS, rename a file in the osTicket folder.

1. Open File Explorer and navigate to C:\inetpub\wwwroot\osTicket\include.
2. Rename ost-sampleconfig.php to ost-config.php.
3. Right-click the renamed file, select Properties, then go to the Security tab.
4. Click Advanced, disable inheritance, and choose Remove all inherited permissions from this object.
5. Add new permissions by clicking Add.

![Screenshot 2024-12-05 214720](https://github.com/user-attachments/assets/2661b3ec-fe92-40e8-9a93-5549cda85c6f)

![image](https://github.com/user-attachments/assets/00c419bc-37c5-4fab-9a39-15b0c62cacdd)

![image](https://github.com/user-attachments/assets/d94264ca-11ee-404d-8f60-a0cce4db09fa)

![image](https://github.com/user-attachments/assets/702b2007-b15b-48dc-952f-629c2a7ee76b)

![image](https://github.com/user-attachments/assets/34515a18-c26f-4379-a576-8a3dd032cd9a)

![image](https://github.com/user-attachments/assets/9492b7aa-82bb-4111-b36c-9b730762cb52)

17.) Once that is done we will continue to setup osTicket in the browser. Click Continue on the osTicket browser page. Fill out the page as required except the Database Settings at the bottom of the page.

![Screenshot 2024-12-05 215208](https://github.com/user-attachments/assets/20c7aa95-4090-4615-98d9-bb87439b6aa8)

18.) Download and install HeidiSQL from the installation files. Create a new session in HeidiSQL and enter the password set during the MySQL installation. In the new session, right-click on Unnamed and create a new database named osTicket.

![image](https://github.com/user-attachments/assets/676e058e-402a-4784-bc50-21bd0e9f324a)

![Screenshot 2024-12-05 215646](https://github.com/user-attachments/assets/055e2134-ea19-4e6b-9728-6c1668bc2ee1)

![Screenshot 2024-12-05 215759](https://github.com/user-attachments/assets/1c9c61bf-d569-43cf-9dbb-ee281be5a949)

19.) Once we have the new database setup go back to the osTicket browser and under MySQL Database type in osTicket.

![image](https://github.com/user-attachments/assets/9a2b9171-08d3-40b4-80d8-7fd1bf5b59ce)

20.) After everything is done, osTicket should be installed! 

However, some clean-up is required before using it. First, delete the setup folder found in C:\inetpub\wwwroot\osTicket. Next, go to C:\inetpub\wwwroot\osTicket\include and change the permissions of the ost-config.php file. Remove full access for Everyone and set the permissions to "Read" only.

![Screenshot 2024-12-05 220015](https://github.com/user-attachments/assets/eaba12b6-bc97-4920-b038-7979d9a3b41e)

21.) Now we can login using the osTicket Admin account information to login.

![image](https://github.com/user-attachments/assets/fb48d628-ea85-4d7d-b251-2a942e7c344a)

![Screenshot 2024-12-05 220157](https://github.com/user-attachments/assets/514f966c-c519-48d1-b9c0-e7c1fd9624ea)

</p>
<p>
osTicket is now installed and ready to use. I used it to learn how ticketing systems work and how to resolve tickets. In IT support, I collaborate with a team to address IT-related issues through a ticketing system. This lab served as a hands-on way to set up a ticketing system from scratch, providing a foundation for my future work in IT support.
</p>
<br />
