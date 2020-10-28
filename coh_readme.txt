
10.0.0.131

acct: cpt409
pw: testtest

server: admin
pw: coh123!


in servers.cfg, change advertisedIP to serverip
in ssms, change cohauth.dbo.server
	-> ip = 10.0.0.131
	-> leave inner ip as 127.0.0.1

cohdb.dbo.ents -> change account to access level 11

to create an account = https://10.0.0.131

make sure virtual intel vt-x/ept is checked when setting up VM

to change IP:
change dbo
change server.cfg (advertisedIP)



#### Introduction ####
This VM has been developed in response to the problems people were having getting a City of Heroes SCoRE based server running. Included in the archive are offline backups of some of some useful guides from https://ourowiki.ouro-comdev.com

This VM is based on Server 2012r2, it is running the i26 code, all services are active except the queue_server by default, the auction house has been pre-populated with recipes and salvage.

#### Setup VMWare Version ####
(For a guide with images see the guides section “I25 Create VMWare 15 Virtual Machine - Project_ Ouroboros”)

1. Open VMWare 15 and click Create a New Virtual Machine.
2. Select "I will install the operating system later" and click Next.
3. Choose Windows Server 2012 from the dropdown menu and click Next.
4. Choose a name and location for your VM, and make a note of the location you choose for a later step.
5. The options you select here do not matter, just click Next.
6. Click the Customize Hardware button.
7. Change Memory to 8192MB (you can also just click 8GB to the left of the slider).
8. Click on Processors, and change the number of cores to 4 (PROC = 1).
9. Click on Network Adapter, and select the Bridged option. Then click the Close button.
10. Click Finish to close this window.
11. Right click on the VM you've just created, and select Settings.
12. The Hardware window will reopen, click the Add button.
13. Choose Hard Disk, and click Next.
14. Select SCSI as the disk type, and click Next.
15. Select "Use an existing virtual disk," and click Next.
16. Select the VMWare v2 image you downloaded (it must be extracted from the 7z archive first), and click Finish.
17. Select the first Hard Disk (not the 127GB one we just added) and click the Remove button.
18. Select the new Hard Disk, click the Advanced button, and change the Virtual device node dropdown menu to SCSI 0:0 (this should be the first option in the list, you may have to scroll up)
19. In the folder you chose for the VM in step 4, you will find a *.vmx file, open this in Notepad or any text editor, and add firmware = "efi" as a new line at the bottom, then save and close the file.
20. Run the VM. The Administrator password is coh123!

#### Setup Hyper-V Version ####
(For a guide with images see the guides section “I25 Community Virtual Machines - Project_ Ouroboros”)

1. Add new Virtual Machine
2. Select Next add a Name. Click Next
3. Select Generation 2 and next.
4. Set memory to 8192 or higher and click next.
5. Select your HyperV LAN connection and click next.
6. Choose "Use Existing Virtual Hard Disk" and navigate to the supplied VHDX. Click Finish.
7. Right click on the new Virtual Machine and pick settings.
8. Increase the number of processors supplied to the VM to at least 4. Click Ok.
9. Right click on the virtual machine and click start.

#### Common Setup ####
This VM will automatically log on, we recommend you change the password to one of your own, by clicking ctrl-alt-del and “change password”. The password is coh123! by default.

Once your VM machine is installed, run the “Set or change your external IP” from the desktop, here you can use your local network IP if you plan to use this on your home network only, or your internet IP (or domain name) if you plan to run this online for others to connect.

In the case of Internet play you will need to open or redirect ports on your router, and forward them to the LAN IP of the VM. Unfortunately, we cannot script the opening of the ports for you as the procedure will vary on the make and model of your router.
The ports you will need to open / forward are:
tcp/udp 11228
tcp/udp 18716-19000
tcp/udp 80
tcp/udp 443
tcp/udp 7000

You can re-run the “Set or change your external IP” as often as you need.

Once you have completed the steps above you are ready to start up your server, to do this run the “Start up your server” script, this will load the server, maps will be loaded as demanded during play. Alternatively run the “Start up your server with all maps (Minimum 32GB RAM)”, this will pre-load all commonly used maps (49 maps) into memory, this will improve zoning time for players during play, however you will need a minimum of 32GB of RAM in your server to support this.

You will need to create accounts for your players. Aleena’s web portal is preinstalled, you can access this via the start menu, or by browsing to https://YOURSERVERIP/ from a connected computer. Alternatively, there is a start menu shortcut to "Coh DBTool" in the tools section. This application gives you access to many useful GM functions, such as creating accounts, importing and exporting characters, and shard management.

There is a test GM account already preinstalled.
Username: test
Password: coh123!

#### Client Install ####
In order to install the correct version of the client on your players computers, you should browse to the account portal via https://YOURSERVERIP/, there you will find a link to the download. Download and then unzip the cityofheroes.zip to your hard disk, create a shortcut to "CityOfHeroes.exe -auth YOURSERVERIP -patchdir i26" Run the application via this shortcut and login with the account created in the above steps.

#### Other Information ####
Xammp is installed and set up, however to secure this you should consider setting up SSL, this can only be done once you have a domain name. More details can be found in the guides under “Account Portal - Project_ Ouroboros”.

Inside the folder C:\xampp\htdocs:
you will find a tequila client, and a creamsoda client. If you plan to switch between existing online versions and your own server, and don't wish to have your server conflicting due to file changes through tequila, use cream soda for your private server. A set up guide for this is located in folder guides.

There is a sample manifest is located in C:\xampp\htdocs, it must be updated for your specific setup and will not work for your server as it stands. A guide for doing this is located in the guides folder.

For more advanced users, you can find links to the configuration files in start menu to help with changing your configurations.

A copy of the Guides folder is located in C:\Guides.

///////////////////////////////////////////////////////////


