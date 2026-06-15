#VLSM
![topology](topology.ong)

Given network address = 192.168.5.0/24
Sequence being Large > Medium > Small. So starting with LAN2, 64 hosts.

/26 provides exactly 64 hosts but that would not be enough for network and broadcast addresses.
/25 is the better option.

/25 comes with a block size of 128. Therefore:
Addresses for LAN2 =

network: 192.168.5.0/25
subnet mask: 255.255.255.128
broadcast: 192.168.5.127 (128 - 1 because 128 is the network for the next subnet)
first usable: 192.168.5.1
last usable: 192.168.5.126
usable hosts: 126

Continue with the second largest, LAN1 with 45 hosts.
From LAN2, LAN1's network = 192.168.5.128
/26 provides 64 hosts and /25 with 32 hosts. /26 is selected.
Block size = 64

network: 192.168.5.128/26
subnet mask: 255.255.255.192
broadcast: 192.168.5.191 (128 + 64 -1)
first: 192.168.5.129
last: 192.168.5.190
usable: 62

LAN3 with 14 hosts next.
From LAN1, LAN3's network = 192.168.5.192
/28 provides 16 hosts
Block size = 16

network: 192.168.5.192/28
subnet mask: 255.255.255.240
broadcast: 192.168.5.207 (192 + 16 - 1)
first: 192.168.5.193
last: 192.168.5.206
usable: 14 

LAN4 with 9 hosts.
From LAN3, LAN4's network = 192.168.5.208
/28 with 16 hosts will be kept using as /29 only provides 8 addresses.

network: 192.168.5.208/28
subnet mask: 255.255.255.240
broadcast: 192.168.5.223 (208 + 16 - 1)
first: 192.168.5.209
last: 192.168.5.222
usable 14


last network remaining is the router-to-router connection. 2 hosts are needed.
Since network and broadcast should not be assigning to end hosts, /30 with 4 hosts is better.
From LAN4, this network starts with 192.168.5.224

network: 192.168.5.224/30
subnet mask: 255.255.255.252
broadcast: 192.168.5.227 (224 + 4 - 1)
first: 192.168.5.225
last: 192.168.5.226
usable: 2

#Learning Outcome
 - End hosts nested within the same router don't need to do static routes. They do ARP automatically.
 - Beware not to configure duplicate next-hop as each router can deliver packets for the subents with the same next-hop address.