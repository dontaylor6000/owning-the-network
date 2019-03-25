# Owning the Network

### Introduction
We have covered a good number of tools so far that perform all sorts of packet
creation/capture/manipulation tasks, but most of these tools were created with a
specific goal in mind.  It turns out if you need to make some changes to how
these tols behave you need to build an entire new tool (or at least rebuild the
one you are using).  Because of this we introduce scapy.


> From [scapy.net](https://scapy.net/):
> Scapy is a powerful interactive packet manipulation program. It is able to forge
> or decode packets of a wide number of protocols, send them on the wire, capture
> them, match requests and replies, and much more. It can easily handle most
> classical tasks like scanning, tracerouting, probing, unit tests, attacks or
> network discovery (it can replace hping, 85% of nmap, arpspoof, arp-sk, arping,
> tcpdump, tethereal, p0f, etc.). It also performs very well at a lot of other
> specific tasks that most other tools can’t handle, like sending invalid frames,
> injecting your own 802.11 frames, combining technics (VLAN hopping+ARP cache
> poisoning, VOIP decoding on WEP encrypted channel, …), etc.

### Background


### Resources
* [The scapy python library](https://scapy.net/)
* [`/code`](../blob/master/code/)
* [AWS educate (Login link)](https://www.awseducate.com/signin/SiteLogin)
* [AWS Build link](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=CEG-4900Lab02&templateURL=https:%2F%2Fs3.amazonaws.com%2Fwsu-cecs-cf-templates%2Fceg4900lab1.yml)

### Task 1 -
Lets start with a very basic packet sniffer:
```
from scapy.all import *

def packet_callback(packet):
    print packet.show()

sniff(prn=packet_callback,count=1)
```

When executed with `sudo` the above will capture a single packet on any
interface on the system and output it like so:
```
###[ Ethernet ]### 
  dst       = 78:d2:94:35:2a:9d
  src       = 60:57:18:e6:95:3d
  type      = 0x800
###[ IP ]### 
     version   = 4
     ihl       = 5
     tos       = 0x0
     len       = 52
     id        = 20192
     flags     = DF
     frag      = 0
     ttl       = 64
     proto     = tcp
     chksum    = 0x4115
     src       = 192.168.1.121
     dst       = 35.164.197.9
     \options   \
###[ TCP ]### 
        sport     = 59152
        dport     = https
        seq       = 1436241650
        ack       = 3529910129
        dataofs   = 8
        reserved  = 0
        flags     = A
        window    = 298
        chksum    = 0x53f8
        urgptr    = 0
        options   = [('NOP', None), ('NOP', None), ('Timestamp', (10757512, 240368411))]

None
```

Now lets do something more interesting.
scapy as ping (ICMP, TCP, and UDP ping)


### Task 2 -
scapy as nmap


### Task 3 -
scapy as fuzzer

### Task 4
I'm tired of doing all the work for this class...  Find a github repository with
some scapy code and examples (that isn't a fork of https://github.com/0x90/uberscapy ).

* Describe what is so cool about it
* Pick one specific tool/technique/script and answer the following:
  * What doe sthe script do?
  * What kind of AWS environment would you need to test it out?


### Acknowledgement
Portions of this lab were derived from [Black Hat Python: Python Programming for
Hackers and Pentesters, by Justin Seitz](https://nostarch.com/blackhatpython).

Huge shoutout to [0x90](https://github.com/0x90) who has some seriously scary tools
available.
