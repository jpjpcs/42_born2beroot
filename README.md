# 42_born2beroot

The goal of this project is to create a virtual machine running linux that meets security and performance standards.

# 42_born2beroot Complete Guide

We have a completed guide provided by gemartin: https://github.com/gemartin99/Born2beroot-Tutorial/tree/main

This guide has some points that we should pay extra attention: 

1 - If you're going to do it with bonus, please do what is asked in subpoint "7. One we established the recommended 12 GB we must click on Create. If we are doing the bonus we might set 30 GB." of point "2. Virtual machine installation: ", but put exactly 30.8 GB instead of 30GB.

2 - In the subpoint "15. Select Guied - use entire disk and set up encrypted LVM. If you want to do the bonus select Manual and then click here" of the point "3. Debian Installation", go directlly to "8.1. Manual partition".

3 - In the subpoint "6. As the subject indicates, the size of the partition must be 500 megabytes.", put exactly 525.05 instead of 500mb. 

4 - Follow the tutorial and do it until 8.12 (included). Then jump to 8.19 (and do it).

5 - In the next points where you need to define the dimension of the partitions (similar to what I refered in point 3 above), you should convert Gibibyte to Gigabyte (using https://www.dataunitconverter.com/gibibyte-to-gigabyte/4) to include the right value on the field. For example, in subpoint "37. Size, as indicated in the subject, will be 10g." of point "8.1. Manual partition", 10 g (Gibibyte or GiB) is equivalent to 10.73741824 GB (Gigabyte). In subpoint 38, 39, 40, 41, 42, 43, we have to do the same, to guarantee that the partitions have the dimension that is asked in the bonus part: ![image](https://github.com/jpjpcs/42_born2beroot/assets/127231744/dd141d07-f8a4-4199-b77a-58a2d05e7b95).

5 -  After finishing the point "8.1. Manual partition", make the point "4.1 Installing sudo & configuration of users and groups" and point "4.2 Installing & configuring SSH" of the point "4. Virtual machine setup gear".

6 - After doing the 4.2 point, make the point "4.6 Connecting via SSH". Why? Because you will have to put a lot of commands, and its easier to copy/paste it to the linux terminal of your pc (which is not allowed in the environment of the Debian Gnu/Linux -  the "terminal" of the VM).

7 - In "4.6 Connecting via SSH", in the subpoint "2. Once there we will click on Network, click on Advanced so it shows more options, then we click on Port fowarding.", choose Bridge Adapter (Attached to:) and eno2 (Name:) in the Network. This will solve a lot of issues in the next points of the tutorial, once you don't have to configure any door anymore. It will be done automatically for you.

8 . At point 8.2 Wordpress & services configuration, subpoint "Lighttpd", we don't have to do the subpoint 4 (why? because we have done the configuration explained in the point above - 7.).

9. At point 8.2 Wordpress & services configuration, subpoint "WordPress configuration", subpoint "7. Once we have completed the previous steps we can go back to our browser and type localhost. You should see the following:", we should put our ip adress (command "ip a" in the terminal to check it) instead of localhost.

10. In the point "8.3 - Aditional service", subpoint "LiteSpeed", subpoint "6. Once we have completed the previous step we can connect. We will put in the search engine of our browser localhost:7080 we provide our login credentials and we will have access to everything.", we should put our ip address followed by ":" (example: http://10.11.248.100:7080)...7080 is the door of the service.

# Debian Version

In my project I used Debian 10.13. If you want to use the same version, follow the download link: https://cdimage.debian.org/cdimage/archive/10.13.0/amd64/iso-cd/debian-10.13.0-amd64-netinst.iso

# Commands for Evaluation

| Command                               | Description                                                              |
|---------------------------------------|--------------------------------------------------------------------------|
1.  Verify that no graphical interface is in use.
| ls /usr/bin/*session                   | Checks if there are no active graphical interfaces in use                |
2. Check that the UFW service is in use.
| sudo ufw status                       | Checks the status of the UFW (firewall) service                           |
| sudo service ufw status               | Checks the status of the UFW (firewall) service                           |
3. Check that the SSH service is in use
| sudo service ssh status               | Checks the status of the SSH service                                      |
| uname -v                              | Displays information about the operating system version                   |
4. Check that you are using the Debian 
| groups username                       | Checks the groups to which a user belongs                                 |
5. Check that your user is within the "sudo" and "user42" groups.
| getent group sudo                     | Checks that the user is within "sudo" group                               |
| getent group user42                   | Checks that the user is within "user42" group                             |
6. Create a new user and show that it follows the password policy we have created.
| sudo adduser name_user                | Creates a new user in the system                                          |
| sudo addgroup evaluating              | Creates a new group in the system named "evaluating"                      |
| sudo groupdel group_name              | Removes a group from the system                                           |
| sudo adduser name_user evaluating     | Adds a user to a specific group (in this case is the evaluating group)    |
| getent group evaluating               | Checks that the user is within "evaluating" group                         |
| sudo adduser name_user sudo           | Adds a user to the "sudo" group (superuser privileges)                    |
| hostname                              | Displays or sets the hostname (computer name)                             |
| sudo nano /etc/hostname               | Edits the hostname configuration file                                     |
| sudo nano /etc/hosts                  | Edits the system's name resolution configuration file (DNS)               |
| hostnamectl set-hostname <new_name>   | Changes the hostname                                                      |
| sudo reboot                           | Reboot the machine                                                        |
| lsblk                                 | Check all partitions                                                      |
| which sudo                            | Displays the full path to the "sudo" command executable-sudo is installed |
| dpkg -s sudo                          | Checks the installation status of the "sudo" package                      |
| dpkg -l | grep sudo                   | Shows that sudo is installed                                              |
| sudo adduser name_user sudo           | Adds a user to the "sudo" group (superuser privileges)                    |
| getent group sudo                     | Checks that the user is within "sudo" group                               |
| nano /etc/sudoers.d/sudo_config       | Edits the sudo configuration settings/rules                               |
| sudo visudo                           | Edits the sudoers file with safety                                        |
| cd /var/log/sudo && ls (at root@hostname:~# on the terminal) | Show that the path /var/log/sudo/ exists and contains at least one file |
| cat sudo_config (at sudo file)        | Show the logs                                                             |
| sudo nano /etc/pam.d/common-password  | Edits the common password configuration settings in PAM                   |
| sudo nano /etc/login.defs             | Edits the password configuration settings                                 |
| sudo chage --maxdays 30 --mindays 2 --warndays 7 username | change the pass definitions in the defs file          | 
16.
| dpkg -s ufw                           | Checks the installation status of the "ufw" package                       |
| sudo service ufw status               | Checks the status of the UFW (firewall) service                           |
| sudo ufw status numbered              | Lists the numbered rules of UFW                                           |

| sudo ufw status numbered              | Lists the numbered rules of UFW                                           |
| sudo ufw allow port-id (expl: 8080)   | Allows traffic on port 8080 through UFW. Creates the rule.                                   |
| sudo ufw delete num_rule              | Removes the specified rule by number in UFW                               |

| ssh newuser@localhost -p 4242         | Connects to "localhost" as "newuser" using SSH on port 4242               |
| crontab -e                            | Opens the editor to edit cron tasks                                       |
| sudo systemctl enable cron            | Enables the cron service to start at boot                                 |
| sudo systemctl disable cron           | Disables the cron service                                                 |
| chage -l <username>                   | Displays information about the user                                       |
 
 | ss -tuln                              | Lists all running TCP and UDP network connections                        |

 
 ### Compare the signature
- Create the signature: `shasum born2beroot.vdi`
- Place the signature in test.txt: `diff signature.txt test.txt`


# Questions
## What is a VM, why its used, and why is it important?

What is a VM: It is a resource that uses software instead of a physical computer to run programs or apps as if it was a real computer. Basically it simulates a computer system, having its own operating system and functions separately. For that reason, we can have more than one VM per machine. 

Why its used: It allows the creation of multiple simulated environments or dedicated resources from a single physical hardware system. Basicallly, it allows the creation of multiple machines and operating systems to be installed on a single computer. 

Why its important: It is important for conducting different tests on both hardware and software.
Can be used to test applications in a safe, separate environment. Works by using software to simulate virtual hardware and run on a host machine.

## What is the difference between CentOS and Debian?

Debian is more user-friendly, supports many libraries, filesystems and architecture, and its easier to update, while CentOS is more focused on enterprise usage.

![image](https://github.com/jpjpcs/42_born2beroot/assets/127231744/f9865187-e4f1-428d-8356-772351439959)

![image](https://github.com/jpjpcs/42_born2beroot/assets/127231744/6412f680-e70d-44dc-b8a5-2167871f41f8)

## Why did you choose Debian?

I followed the instructions from the recommended system PDF. Debian its easier to install and configure so better for personal server. Also, The subject itself explains that it is easier to do it in Debian and if you look for documentation/tutorials there are many and all of them have been done in debian.

## What are Apt and Aptitude?

Apt and aptitude are advanced package tools for installing and managing programs. 
Aptitude is an enhanced version of apt. 
## Aptitude and APT (Advanced Packaging Tool) Differences?
First difference: Aptitude is a high-level package manager while APT is lower level which can be used by other higher level package managers. 
Second difference: Apt only does exactly what is passed on the command line, while aptitude has better autonomous management. 
Third difference: Aptitude is smarter and will automatically remove unused packages or suggest installation of dependent packages
Fourth difference: Another big difference is the functionality offered by both tools. Aptitude offers better functionality compared to apt-get. Both are able to provide the necessary means to perform package management. However, if you are looking for a more feature-rich approach, Aptitude should be it.

## What is AppArmor?

AppArmor manages permissions and restrictions, protecting the system by creating security profiles for each program, restricting access to unused system resources.  
Its a Linux security module in the Linux Kernel system that provides Mandatory Access Control (MAC) security, allowing the system administrator to restrict the capabilities of a program. Basically it allows the system admin to restrict the actions that processes can perform. It is included by default with Debian. To check if its running we must write the command: aa-status.

## What is LVM?

LVM dynamically manages partitions by creating a group for partitions, allocating space dynamically on mass storage devices, and avoiding the need for physical disk formatting when reallocating space. Basically it allows us to easily manipulate the partitions or logical volume on a storage device, being more flexible than conventional partitioning schemes for storing volumes.

## What is UFW (Uncomplicated Firewall)?

UFW allows for simple configuration of the firewall.
UFW is a interface to modify the firewall of the device without compromising security. You use it to configure which ports to allow connections to and which ports to close. This is useful in conjunction with SSH, can set a specific port for it to work with.

## What is SSH?

SSH is a communication encryption technique between host and client. The communication is protected on both ends.
SSH or Secure Shell is an authentication mechanism between a client and a host. It uses encryption techniques so that all communication between clients and hosts is done in encrypted form. User on Mac or Linux can use SSH the terminal to work on their server via SSH.
Video: https://www.youtube.com/watch?app=desktop&v=qWKK_PNHnnA&ab_channel=Tinkernut

## What is Cron?

Cron allows for scheduling of programs or scripts to run at a specific time.

Cron or cron job is a command line utility to schedule commands or scripts to happen at specific intervals or a specific time each day. Useful if you want to set your server to restart at a specific time each day.

    cd /usr/local/bin – to show monitoring.sh
    sudo crontab -u root -e – to edit the cron job
    change script to */1 * * * * sleep 30s && script path – to run it every 30 seconds, delete the line to stop the job from running.




