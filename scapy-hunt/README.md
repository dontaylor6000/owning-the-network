**scapyHunt** - A series of Network Security puzzles and challenges designed to educate users on packet manipulation
and common network attacks. 

Creates a TUN/TAP interface for a software defined network, over which packets will be sent by the
user- either hand crafted or using a variety of tools- in order to achieve a given objective.

### How to Play
scapyHunt is a terminal-based game in which you will use common network attack vectors
and penetration testing methods to analyze and compromise a virtual network.

The network itself is completely defined by handcrafted packets which simulate a typical network setup.

All communications with the network must happen over the 'tap0' interface-
be sure to set the interface argument when using the tools listed below. For some starting information,
try the command 'ifconfig tap0'.

Have fun :)

### Goal
There is an FTP server somewhere on the network containing a very important document.
Locate the server, find a way to connect to the service and retrieve it.

#### Tools
* scapy
* nmap
* wireshark
* telnet/nc
* dsniff

#### Concepts
* Bash terminal-fu
* Packet capture and manipulation in scapy
* Packet analysis in wireshark
* Router modes of operation
* Network topography, gateways
* Basic telnet/nc commands

#### Hints
* You may need to find a way to see all of the traffic on the network.
* Other clients on the network might give you useful clues, if you can coerce them.
* The target will most likely be isolated from the immediate local network, and will have some preferred clients.

#### About

Uses scapy, a Python packet manipulation library.

http://www.secdev.org/projects/scapy/

-----

Recommended tools for use-

http://www.secdev.org/projects/scapy/ - Packet manipulation

https://www.wireshark.org/ - Packet sniffing

http://nmap.org/ - Network topography

http://www.monkey.org/~dugsong/dsniff/ - Collection of penetration testing tools, ie 'macof'

Note that some tools may require the user to specify the TUN/TAP interface, rather than a default interface.
