<p align="center">
<img src="https://imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
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
I’m creating a Windows 10 VM in Azure, naming it osticket-vm, and configuring it with 4 vCPUs. This will act as a dedicated environment for installing osTicket without interfering with my local machine. Once the VM is ready, I log in using Remote Desktop to start the setup process.</p>
<br />

<h2>2. Enable IIS(Internet Information Services)</h2>

<p>
<img width="550" alt="Screen Shot 2024-12-08 at 8 55 26 PM" src="https://github.com/user-attachments/assets/4f2ea6e0-5199-4d37-b1f5-7a42096376d6">
/>
</p>
<p>
On the VM, I’m enabling IIS with the CGI option. This step is necessary because IIS serves as the web server that will host osTicket. I make sure the required application development features are checked so the server can process content.</p>
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
I’m installing key components from the osTicket installation folder: PHP Manager, Rewrite Module, PHP 7.3.8, VC Redist, and MySQL. Each of these plays a critical role in supporting osTicket’s functionality—PHP runs the backend logic, MySQL handles the database, and other tools provide compatibility and extensions.</p>
<br />

<h2>4. Configure IIS for PHP</h2>

<p>
<img width="550" alt="Register PHP file" src="https://github.com/user-attachments/assets/0172d6cb-f36a-465e-8e7e-946022b401c4">
</p>
<p>
Using the PHP Manager in IIS, I register the PHP executable file (php-cgi.exe) so the server can handle PHP files. Afterward, I restart IIS to ensure the changes take effect and confirm the server is ready to process PHP-based applications like osTicket.</p>
<br />

<h2>5. Prepare osTicket Files</h2>

<p>
<img width="550" alt="rename osTicket in wwwroot" src="https://github.com/user-attachments/assets/0b910e46-28f0-474c-946f-efbb22219279">

</p>
<p>
I’m extracting the osTicket files, moving them into IIS’s root directory (C:\inetpub\wwwroot\osTicket), and renaming the folder appropriately. Then, I reload IIS to apply the changes. This step essentially deploys the osTicket application so it’s ready to be accessed and configured.</p>
<br />

<h2>6. Enable PHP Extensions</h2>

<p>
<img width="325" alt="Enabled osticket prereq" src="https://github.com/user-attachments/assets/5fbce533-2e85-4f00-860f-92f87870ce02">
<img width="325" alt="Osticket final page prereq" src="https://github.com/user-attachments/assets/b5c69b5a-d0bd-4d2e-bfb2-83627d13a53f">
<img width="325" alt="osticket prereq page changes" src="https://github.com/user-attachments/assets/160a2b80-09ba-429a-a7a0-f56b601ce3e5">


</p>
<p>
I’m enabling specific PHP extensions—php_imap.dll, php_intl.dll, and php_opcache.dll—using the PHP Manager in IIS. These extensions provide essential functionality like email handling, internationalization, and performance improvements, which are crucial for osTicket to operate effectively.</p>
<br />

<h2>7. Set Up Database Configuration</h2>

<p>
<img width="325" alt="add odticket to database" src="https://github.com/user-attachments/assets/7bfa5f35-1915-438e-88ad-a84e8998b795">
<img width="325" alt="osticket added to database" src="https://github.com/user-attachments/assets/d6e9db5a-8a7f-40ad-8a05-0114c362cfdc">
<img width="325" alt="osticket security setting" src="https://github.com/user-attachments/assets/9156d94e-7ffc-48df-94b3-9d3e0a9da643">

</p>
<p>
I’m renaming the ost-sampleconfig.php file to ost-config.php and setting its permissions to allow full access for the system. Next, I open HeidiSQL to create a new database named osTicket, which will store all the application data. This step prepares the system for the final installation.</p>
<br />

<h2>8. Complete Installation</h2>

<p>
<img width="500" alt="Osticket database install login" src="https://github.com/user-attachments/assets/09290cfe-9ec3-4e42-85ef-6e97a10134ed">
<img width="500" alt="OsTicket Installed Congrats" src="https://github.com/user-attachments/assets/b6adf4c5-e227-4f3f-bbe6-ba6ea7f32df2">
</p>
<p>
In the browser, I’m entering the database details (username and password) to connect osTicket to the database. Once I complete the setup process, osTicket is installed and fully operational, ready to manage help desk tickets effectively.</p>
<br />
