# Lab 3 - Owning the Network

### Introduction
We introduced scapy at a mid to high level in our in-class exercise last week.
In this lab we will be using scapy to actually perform several common attacks
using some of the more advanced features scapy provides.

Two things to keep in mind:
1. This lab will require more programming and google foo than previous labs, pay
   attention to Lab Talk for any communications or hints.
2. Please be sure to answer ALL questions asked about your process.  If you used
   a command, be sure to paste the command in your `lab3.txt`, if you have any
   issues please go out to lab talk!!!

### Background
In this challenge you will be analyzing network traffic in an attempt to gain
access to a FTP server containing a very important document.  Your task is to
connect to this service and retrieve it.

You will be using the following concepts:
* `bash` / terminal-fu
* packet capture / manipulation with `scapy`
* pcap analysis (wireshark or other)
* Router modes of operation (switch vs hub)
* Network topography
* gateways
* `nc`

This repository will guide you through the exercises but there will be a bit of
outside research required to answer some of the questions.

### Resources
* [The scapy python library](https://scapy.net/)
* [`/scapy-hunt`](../master/scapy-hunt)
* Your local Parrot OS Virtual Maching (no AWS support yet, will update here
  when it is available)

### Task 1 - Are you even listening?
To begin this lab, start up your Parrot OS VM (or ssh into your AWS Ubuntu
Public instance).  Clone this repository into your home directory and run the 
following command (editing as necessary for path differences):
``` 
sudo python ~/ceg-4900-lab3/scapy-hunt/scapyHunt.py
```
**Do not close this window!**  The above command needs to continue to run while
you are working on this lab.

You should notice a new networking interface available (`sudo tcpdump -D`)
called `tap0`.  This interface is being created by scapyHunt.py and simulates a
real network.  **Be sure to specify this interface when attempting to run
commands!**

1. Figure out as much as you can about the network. 
  * What is it's CIDR?
  * What  hosts are on the network?
  * What traffic do you see on this interface?

### Task 2 - Talk to me goose
It looks like we are not seeing much traffic on this network.  There are a
few different things that could be causing this.  We are going to focus on
one specific case.

1. How do networking hubs and switches differ when transferring packets to a
   device on the hub/switch?
2. What is a CAM Table on a network switch?
3. What is the goal of a CAM table overflow?
4. Using Scapy, develop a CAM table overflow and deploy it on your `tap0`
   interface.  (I do not care if you find a scapy cam table overflow online so
   long as you make it work and document where you obtained it and the author).

   Be sure to identify all key parts of the source code with comments and upload
   it along with your `lab03.txt` (please use a `.tar.gz` format).
5. If your CAM table overflow is successful you should now see additional
   traffic on the network.  Verify this with tcpdump/wireshark.

### Task 3 - The sincerest form of flattery
Now we should be seeing some traffic flowing on our network.  

1. Inspect this traffic in comparison to your previous nmap?
2. Investigate port knocking.  Describe what a port knock is.
3. Using scapy, perform the port knock that is happening between `10.5.0.4` and
   `10.5.0.6`.  (hint, this one may be easier for you to do on your own than
   copy someone elses work but the same rule applies, if you find it just source
   the location and author, make sure it works, and document it).  
   
   Be sure to include your `port-knocker.py`.  Describe your implementation, how
   you created it, and if there is any human interaction required to implement.
4. Check your network after your port knock with `sudo tcpdump -i tap0`.  What
   is new?
   (if you dont see anything new you might need to look over your port
   knocker)

### Task 4 - A whole new world
Take a look at what is going on on your internal network.

1. Who is talking with who?
2. Run an nmap on the new CIDR space and paste the output.  Are there any systems
   missing from your nmap that you see traffic from in tcpdump?  
3. Inspect those systems further with `nmap`.  What ports are open?

### Task 5 - Open Sesame
Lets get that top secret file!

1. What do you think the secret server IP is?  Why?  Connect to this server 
   with `nc` on the standard FTP port.
2. [It's dangerous to go alone! Take this.](http://www.nsftools.com/tips/RawFTP.htm)
3. Retrieve that file!  You'll need a username and password, which I wont give
   you, but is very easy to guess.  Paste the contents of the secret file here.


### Acknowledgement
Huge shoutout to [jfsulliv](https://github.com/jfsulliv) for uploading scapyhunt!

