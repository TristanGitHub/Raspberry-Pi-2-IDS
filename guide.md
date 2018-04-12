### 1. Installing the Operating System
The Raspberry Pi website has an easy to follow getting started https://www.raspberrypi.org/help/videos/

### 2. Securing your Raspberry Pi
After installing the raspberry pi operating system, it is time to secure it. The security of your Raspberry Pi is important. Gaps in security leave your Raspberry Pi open to hackers who can then use it without your permission.

#### Change your default password
The default username and password is used for every single Raspberry Pi running Raspbian. So, if you can get access to a Raspberry Pi, and these settings have not been changed, you have root access to that Raspberry Pi.

So the first thing to do is change the password. This can be done via the raspi-config application, or from the command line.
    
    sudo raspi-config
    
#### Changing your username

It is also important to change your Raspberry Pi username to make more secure. All Raspberry Pis come with the default username pi, so changing this will immediately make your Raspberry Pi more secure.

To add a new user, enter:

    sudo adduser Lynda
   
You can check your permissions are in place (i.e. you can use sudo) by trying the following:

    sudo su

If it runs successfully, then you can be sure that the new account is in the sudo group.

Once you have confirmed that the new account is working, you can delete the pi user. Please note, though, that with the current Raspbian distribution, there are some aspects that require the pi user to be present. If you are unsure whether you will be affected by this, then leave the pi user in place. Work is being done to reduce the dependency on the pi user.

To delete the pi user, type the following:

    sudo deluser pi

This command will delete the pi user but will leave the /home/pi folder. If necessary, you can use the command below to remove the home folder for the pi user at the same time. Note the data in this folder will be permanently deleted, so make sure any required data is stored elsewhere.

    sudo deluser -remove-home pi
    
Login to the just created user and create a ssh key.
    
    ssh-keygen
    
 ### 2. Setup static ip
 Start by editing the dhcpcd.conf file
 
    sudo nano /etc/dhcpcd.conf
 
Scroll all the way to the bottom of the file and add one, or both of the following snippets. Depending on whether you want to set a static IP address for a wired connection or a wireless connection eth0 = wired, wlan0 = wireless.

You’ll need to edit the numbers in the snippet so they match your network configuration.
    
    interface eth0

    static ip_address=192.168.0.10/24
    static routers=192.168.0.1
    static domain_name_servers=192.168.0.1

    interface wlan0

    static ip_address=192.168.0.200/24
    static routers=192.168.0.1
    static domain_name_servers=192.168.0.1
    
