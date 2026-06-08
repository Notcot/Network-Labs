# Static Routing Basic Lab

## Objective:
Configure static routes so PC1 can communicate with PC2 through two routers (R1, R2).

## Topology
![Topology](topology.png)

## IP Addressing

| Device | Interface     | IP Address      | Subnet Mask     |
|--------|---------------|-----------------|-----------------|
| R1     | Gi0/0         | 10.1.1.1        | 255.255.255.0   |
| R1     | Gi0/1         | 10.2.2.1        | 255.255.255.0   |
| R2     | Gi0/0         | 10.2.2.2        | 255.255.255.0   |
| R2     | Gi0/1         | 10.3.3.1        | 255.255.255.0   |
| PC1    | -             | 10.1.1.10       | 255.255.255.0   |
| PC2    | -             | 10.3.3.10       | 255.255.255.0   |

## Static Routes

**R1:**
```cisco
ip route 10.3.3.0 255.255.255.0 10.2.2.2
```
R2:
```cisco
ip route 10.1.1.0 255.255.255.0 10.2.2.1
```

# Learning Outcomes
Fundamental concepts and terminologies for router configurations and netwoorking.
As well as basic git CLI.

## Router Config
2911 routers are used because of them being the standard models recommended in Cisco Network Academy.

**CLI**
Enable configurations:
```
enable
```

Configure router:
```
configure terminal
```

Set router host name:
```
hostname "name"
```

Set FastEthernet or GigabitEthernet port ip addresses:
```
interface Gi0/0

interface Fa0/0
```

Set addresses for ports; ip and subnet mask:
```
ip address x.x.x.x 255.x.x.x
```

Enable port:
```
no shutdown
```

Show current configurations:
```
show ip interface brief
```

## Networking Concepts

- Routers have multiple id addresses with each port having their own.
- Having different subnet ranges for different sets of connections is preferrable.
- Be ware of which ip belongs to which router port while managing static routes.