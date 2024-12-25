<p align="center">
<img src="https://imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This walkthrough outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine: Windows 10, 4 vCPUs.
- osTicket Installation Files: Download and extract.
- Software Requirements:
- Internet Information Services (IIS) with CGI enabled.
  - PHP Manager and Rewrite Module. 
  - PHP 7.3.8 configured in C:\PHP. 
  - VC Redist and MySQL 5.5.62. 
  - HeidiSQL for database management.

<h2>Installation Steps</h2>

1. Set Up VM
2. Enable IIS (Internet Information Services)
3. Install Dependencies:
   - PHP Manager, Rewrite Module, VC Redist, MySQL 5.5.62.
   - Configure PHP in C:\PHP.
4. Configure IIS for PHP
5. Prepare osTicket Files
6. Enable PHP Extensions
7. Set Up Database Configuration
8. Complete Installation

<h2>1. Set Up VM</h2>

<p>
<img width="550" alt="Screen Shot 2024-12-08 at 8 49 33 PM" src="https://github.com/user-attachments/assets/e5f07583-2275-40c7-8975-4d6159ed0bc1">
>
/>
</p>
<p>
I created a Windows 10 VM in Azure named osticket-vm, configured it with 4 vCPUs, and logged in using Remote Desktop. This provided a clean, isolated environment for installing and configuring osTicket.
<br />

<h2>2. Enable IIS(Internet Information Services)</h2>

<p>
<img width="550" alt="Screen Shot 2024-12-08 at 8 55 26 PM" src="https://github.com/user-attachments/assets/4f2ea6e0-5199-4d37-b1f5-7a42096376d6">
/>
</p>
<p>
On the VM, I enabled IIS with the CGI feature by going to Control Panel -> Programs -> Turn Windows Features On or Off and selecting the required options under "World Wide Web Services." IIS serves as the web server to host osTicket.
<br />

<h2>3. Install Dependencies</h2>

<p>
<img width="325" alt="PHP in Windows C Unziped" src="https://github.com/user-attachments/assets/d32e4a9b-5fe6-4972-9aef-43aba3a687ba">
<img width="325" alt="IIS Rewrite" src="https://github.com/user-attachments/assets/111c0bd0-4df3-466b-860c-eeac46887f8a">
<img width="325" alt="HeidiSQL" src="https://github.com/user-attachments/assets/c3f4d766-bb22-43c4-818b-b98ed772c2fb">
<img width="325" alt="My SQL setup" src="https://github.com/user-attachments/assets/01c32556-d1bf-4f5b-8100-79f85c0aeb0f">
<img width="325" alt="Microsoft visual C++" src="https://github.com/user-attachments/assets/fd09180b-99ab-4be9-9753-13904974aae9">
<img width="325" alt="php manager" src="https://github.com/user-attachments/assets/52c9b0a2-c2c0-4f89-bc4d-0b56b73cf7e4">
</p>
<p>
From the osTicket-Installation-Files folder, I installed PHP Manager, Rewrite Module, PHP 7.3.8, VC Redist, and MySQL 5.5. These components are critical for running osTicket's backend and managing its database.
<br />

<h2>4. Configure IIS for PHP</h2>

<p>
<img width="550" alt="Register PHP file" src="https://github.com/user-attachments/assets/0172d6cb-f36a-465e-8e7e-946022b401c4">
</p>
<p>
In IIS Manager, I registered PHP by using PHP Manager -> Register new PHP version and selecting C:\PHP\php-cgi.exe. I restarted IIS to ensure it could process PHP files needed for osTicket.
<br />

<h2>5. Prepare osTicket Files</h2>

<p>
<img width="550" alt="rename osTicket in wwwroot" src="https://github.com/user-attachments/assets/0b910e46-28f0-474c-946f-efbb22219279">

</p>
<p>
I extracted the osTicket files from osTicket-v1.15.8.zip and moved the upload folder to C:\inetpub\wwwroot. After renaming the folder to osTicket, I restarted IIS to deploy the application.
<br />

<h2>6. Enable PHP Extensions</h2>

<p>
<img width="325" alt="Enabled osticket prereq" src="https://github.com/user-attachments/assets/5fbce533-2e85-4f00-860f-92f87870ce02">
<img width="325" alt="Osticket final page prereq" src="https://github.com/user-attachments/assets/b5c69b5a-d0bd-4d2e-bfb2-83627d13a53f">
<img width="325" alt="osticket prereq page changes" src="https://github.com/user-attachments/assets/160a2b80-09ba-429a-a7a0-f56b601ce3e5">


</p>
<p>
In IIS Manager, I used PHP Manager -> Enable or disable an extension to activate php_imap.dll, php_intl.dll, and php_opcache.dll. These extensions are necessary for email integration, internationalization, and performance optimization.
<br />

<h2>7. Set Up Database Configuration</h2>

<p>
<img width="325" alt="add odticket to database" src="https://github.com/user-attachments/assets/7bfa5f35-1915-438e-88ad-a84e8998b795">
<img width="325" alt="osticket added to database" src="https://github.com/user-attachments/assets/d6e9db5a-8a7f-40ad-8a05-0114c362cfdc">
<img width="325" alt="osticket security setting" src="https://github.com/user-attachments/assets/9156d94e-7ffc-48df-94b3-9d3e0a9da643">
<img width="325" alt="Screen Shot 2024-12-09 at 11 58 06 PM" src="https://github.com/user-attachments/assets/46b1e78f-df28-49c7-93cd-dda41cb91510">


</p>
<p>
I renamed ost-sampleconfig.php to ost-config.php in the folder C:\inetpub\wwwroot\osTicket\include and updated the file permissions to grant full access by removing inheritance and adding new permissions for "Everyone."
Using HeidiSQL, I connected to MySQL with the root credentials and created a new database named osTicket. This database stores all the data for the osTicket system.
<br />

<h2>8. Complete Installation</h2>

<p>
<img width="500" alt="Osticket database install login" src="https://github.com/user-attachments/assets/09290cfe-9ec3-4e42-85ef-6e97a10134ed">
<img width="500" alt="OsTicket Installed Congrats" src="https://github.com/user-attachments/assets/b6adf4c5-e227-4f3f-bbe6-ba6ea7f32df2">
</p>
<p>
In the browser, I navigated to http://localhost/osTicket/scp/login.php to finalize the installation by providing database details and configuring basic help desk settings. This completed the installation and made osTicket operational.

<br />
