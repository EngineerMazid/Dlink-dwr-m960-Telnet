**DWR-M960 -v1.1.50Beta1**

Discovered a hidden way to change the DWR-M960 Telnet password.
The Telnet port is open, but when attempting to log in using "root", the password is consistently incorrect.
So I decided to extract the firmware using binwalk. After extraction, I obtained two HTML files for system commands.Two specific web UI pages allow running commands:

**Log in to the router and change the URL to 192.168.0.1/syscmd.htm**  or  ***192.168.0.1/debug.htm***
![dlink1](https://github.com/EnginnerMazid/Dlink-dwr-m960-Telnet/assets/152702183/c5ab77b2-4102-4443-be57-134cbefc4f40)

![dlink2](https://github.com/EnginnerMazid/Dlink-dwr-m960-Telnet/assets/152702183/c1e43213-d65c-4fdf-b7dc-f09d3fef75a7)

![dlink3](https://github.com/EnginnerMazid/Dlink-dwr-m960-Telnet/assets/152702183/61b79a49-86bb-4e79-abfb-303b1afc333e)

![dlink4](https://github.com/EnginnerMazid/Dlink-dwr-m960-Telnet/assets/152702183/4e1557ad-9da0-418f-b18e-66350e48fe42)
 
## Run the following commands: *passwd -d root*
![dlink5](https://github.com/EnginnerMazid/Dlink-dwr-m960-Telnet/assets/152702183/147b95b1-696a-435e-b8b1-f7804359b301)


These commands will remove the root password, allowing Telnet login without it.
We now have root shell access for these routers. Unfortunately, in the root shell, you can't create any files or change anything. I decided to upgrade BusyBox, but it seems the device doesn't have much space, and the root shell was not allowing us to download or make any changes even after remounting. I was not able to make any changes. Every time the router reboots, you need to start this process again.

![dlink6](https://github.com/EnginnerMazid/Dlink-dwr-m960-Telnet/assets/152702183/13d4a79a-514a-4ada-b081-848dc70d37f6)

