<p align="center">
<img src="https://i.imgur.com/SIOPg5j.png" alt="1"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>


In this lab, I installed osTicket from scratch using the required installation files. Before proceeding with the installation of the ticketing system, there are a few preliminary steps to follow. This lab was conducted on a Windows 10 Pro VM created on Azure. The installation files needed for reference and use are located <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">here.</a>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop Connection
- Internet Information Services (IIS)
- MySQL

- <h2>Operating Systems Used </h2>

- Windows 10 Pro</b> (21H2)

<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com/watch?v=ijCZ0CFE0C8)

<h2>Installation Steps</h2>

The entire process is conducted within a virtual machine hosted on Azure. To commence, I created a Windows 10 virtual machine and established a remote connection to it.

<p align="center">
<img src="https://i.imgur.com/9K4t6tA.png" alt="1"/>
</p>

Let's begin by installing Internet Information Services (IIS). We are installing osTicket locally, and it requires IIS to function. To enable IIS, follow these steps:

1. Open the Control Panel.
2. From the Control Panel, go to Programs and select "Turn Windows Features On or Off."
3. In the window that opens, expand "Internet Information Services."
4. Also, expand "Web Management Tools" and enable "IIS Management Console."
5. Click to expand "World Wide Web Services."
6. Now, expand "Application Development Features."
7. In the "Application Development Features" section, enable "CGI."
8. Finally, click "OK" to confirm your selections.

This configuration will ensure that IIS is set up correctly for the installation of osTicket.

<p align="center">
<img src="https://i.imgur.com/swmxmYh.png" alt="1"/>
</p>

Once IIS is enabled, proceed to download and install the necessary components:

1. PHP Manager for IIS (PHPManagerforIIS_V1.5.0.msi) from the installation files folder.
2. Rewrite Module (rewrite_amd64_en-US.msi) after installing PHP Manager for IIS.

Make sure to install these components in the specified order to ensure a smooth setup for osTicket.

<p align="center">
<img src="https://i.imgur.com/PFc6Cgm.png" alt="1"/>
</p>

After installing the Rewrite Module, proceed to create a new folder/directory called C:\PHP on the Windows (C:) drive. This newly created folder will serve as the destination for unzipping the contents from the PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) zip folder that you downloaded from the installation files. Extract all the contents from the zip folder into the C:\PHP directory.

<p align="center">
<img src="https://i.imgur.com/QyoEWJm.png" alt="1"/>
</p>

Following the previous steps, download and install VC_redist.x86.exe from the installation files.

<p align="center">
<img src="https://i.imgur.com/c13KBtf.png" alt="image"/>
</p>

Next, proceed with the installation of MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the installation files. Here are the steps to follow during the installation:

1. Run the MySQL setup wizard.
2. Accept the licensing terms by clicking "I agree."
3. Select "Typical" as the installation type.
4. Click "Install" to begin the installation process.

After the installation is complete, follow these steps to configure MySQL using the Configuration Wizard:

<p align="center">
<img src="https://i.imgur.com/PcEImUr.png" alt="extra"/>
</p>

1. Launch the MySQL Configuration Wizard.
2. Select "Standard Configuration."
3. Choose "Install As Windows Service."
4. Ensure that "Launch the MySQL Server automatically" is checked.
5. For credentials, set the username as root and the password as Password1.

Please note that in a real-world scenario, using such basic credentials is not recommended for security reasons. However, for the purposes of this lab, using the standard credentials root and Password1 will suffice.

<p align="center">
<img src="https://i.imgur.com/iZDovoN.png" alt="image"/>
</p>

<p align="center">
<img src="https://i.imgur.com/lOjIYOl.png" alt="image"/>
</p>

Before proceeding with the installation of osTicket, you need to configure IIS. Follow these steps:

1. Open IIS as an administrator.
2. In IIS, select "PHP Manager."
3. Within PHP Manager, choose "Register new PHP version."
4. Select "Browse" and navigate to the PHP CGI executable file (php-cgi.exe) located within the PHP folder you created earlier during the lab.
5. After registering the PHP version, reload the IIS server within the management console.

These configurations are necessary to ensure that osTicket runs correctly on your system.

<p align="center">
<img src="https://i.imgur.com/ZLPQKpp.png" alt="image"/>
</p>


From the installation files, download osTicket v1.15.8. Then, follow these steps:

1. Extract the downloaded osTicket folder.
2. Copy the contents of the "upload" folder.
3. Paste these contents into the following path: c:\inetpub\wwwroot.
4. Within the c:\inetpub\wwwroot folder, rename the "upload" folder to "osTicket."
5. After completing these steps, reload the IIS server to apply the changes.

This process will set up osTicket on your server for further configuration.

<p align="center">
<img src="https://i.imgur.com/YA5P1rJ.png" alt="image"/>
</p>

<p align="center">
<img src="https://i.imgur.com/OIG03ht.png" alt="image"/>
</p>

<p align="center">
<img src="https://i.imgur.com/D1jf9Lw.png" alt="image"/>
</p>

In the IIS console, follow these steps to enable the required extensions for osTicket:

1. Browse to Sites -> Default -> osTicket.
2. Click on "Browse *:80," and the osTicket installation page will appear.
3. To enable the necessary PHP extensions, click on PHP Manager while in the osTicket menu within IIS.
4. Select "Enable or disable an extension."
5. Enable the following extensions:
   - php_imap.dll
   - php_intl.dll
   - php_opcache.dll
  
This ensures that the required extensions are enabled and ready for the osTicket installation.

<p align="center">
<img src="https://i.imgur.com/FyY9CFk.png" alt="image"/>
</p>

<p align="center">
<img src="https://i.imgur.com/iAd6pHZ.png" alt="image"/>
</p>

Before proceeding with the osTicket installation, you need to rename a file and adjust its permissions. Follow these steps:

1. Navigate to C:\inetpub\wwwroot\osTicket\include.
2. Locate the file named ost-sampleconfig.php.
3. Rename it to ost-config.php.
4. Now, open the ost-config.php file's properties.
5. In the Properties window, go to the "Security" tab.
6. Click on "Advanced" to access advanced security settings.
7. In the "Advanced Security Settings" window, click on "Disable inheritance" and choose the option to "Remove all inherited permissions from this object."
8. Click "Apply" to remove inherited permissions.
9. Next, click "Add" to add new permissions.
10. In the "Permission Entry" window, set "Principal" to Everyone.
11. In the "Type" dropdown, select "Allow."
12. In the "Basic Permissions" section, check the box for "Full control."
13. Click "OK" to apply these new permissions.

These steps ensure that the ost-config.php file has the necessary permissions for osTicket to function correctly.

<p align="center">
<img src="https://i.imgur.com/em0McZW.png" alt="image"/>
</p>

<p align="center">
<img src="https://i.imgur.com/3jWlgJb.png" alt="image"/>
</p>

To proceed, follow these steps to download and install HeidiSQL, create a new session, and create a database named osTicket:

1. Download and install HeidiSQL from the installation files.
2. Launch HeidiSQL after the installation.
3. In HeidiSQL, go to "File" and select "New Session."
4. In the "Session manager" window, enter the following details:
   - Network Type: MySQL (TCP/IP)
   - Hostname/IP: Enter the address of your MySQL server.
   - User: root (assuming you used root as the MySQL username during installation)
   - Password: Enter the password you set during the MySQL installation.
5. Click "Open" to create the new session.
6. Once connected to the MySQL server, you will see a list of databases on the left side. Right-click on "Unnamed" and choose "Create new" -> "Database."
7. Name the new database as osTicket and click "OK" to create it.

Now you have created a new database named "osTicket" using HeidiSQL, and it's ready for the osTicket installation.

<p align="center">
<img src="https://i.imgur.com/0UbjgsM.png" alt="image"/>
</p>

In the osTicket browser window, follow these steps to set up osTicket using the MySQL credentials:

1. Open the osTicket browser window where you accessed the installation page.
2. Fill in the following details:
   - MySQL Hostname: Enter the address or hostname of your MySQL server.
   - MySQL Database Name: Use osTicket (the name of the database you created in HeidiSQL).
   - MySQL Username: Enter the MySQL username (typically root).
   - MySQL Password: Enter the MySQL password you set during the MySQL installation or HeidiSQL setup.
3. Continue filling out the other required details for your osTicket setup, such as your organization information, administrator account, and email settings, as prompted by the installation wizard.
4. Follow the on-screen instructions to complete the osTicket installation.

By using the MySQL credentials you've provided, osTicket will be able to connect to the database and complete the setup process.

<p align="center">
<img src="https://i.imgur.com/9ZhlwCy.png" alt="image"/>
</p>

After successfully installing osTicket, you should perform some cleanup tasks. Follow these steps:

1. Delete the setup folder found in C:\inetpub\wwwroot\osTicket.
2. Return to C:\inetpub\wwwroot\osTicket\include.
3. Locate the ost-config.php file.
4. Right-click on ost-config.php and select "Properties."
5. In the Properties window, go to the "Security" tab.
6. Click "Advanced" to access advanced security settings.
7. Find the entry for "Everyone" in the list of permissions.
8. Select the "Everyone" entry, and click "Edit."
9. In the "Permission Entry" window, change the "Basic Permissions" to "Read" instead of "Full control."
10. Click "OK" to apply the new permissions.

Now, the ost-config.php file no longer has full access for everyone and is set to "Read" only, which is more secure after the installation is complete.

With that, osTicket is now successfully installed and ready for use. In the upcoming labs, I will proceed to further configure it and then provide a brief demonstration of how a typical day-to-day workflow looks while using this tool.
