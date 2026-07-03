# OSPF Single Area

## Objective:

Configure a OSPF Single Area (Area 0) for internal routing and advertise a default route to reach the internet via the ISP (ISPR1).
PCs should be able to communicate with each other across the network.

## Topology
![Topology](topology.png)


## Learning Outcomes
- Hands-on configurations for routers and OSPF.
- Verification of functioning dynamic routing.
- Modern OSPF practices prefer assigning OSPF for each interface individually.
- Passive-interfaces would still require to enter the config-router to do the configuration.
- Better to configure the router id manually and early, maybe before establishing OSPF.

CLI:
```
router ospf __pocessID__                #### To create a OSPF protocol or to enter the configuration of it.

## To configure OSPF in config-router panel ##
(config-router)
network __networkIP__ __wildcardMask__ __Area__             #### enable OSPF for specific network. The degree of tightness can vary with the network ip.
passive-interface __interface__                             #### turn interface into passive-interface.
default-information originate                               #### advertise default route. Use in router connecting to outside networks (ISP, for example).

## To configure in config-if panel ##
(config-if)
ip ospf __protocolID__ area __area__                        #### enable (and to include) the current port for OSPF, for the specific area. 

ip ospf hello-interval __seconds__                          #### to configure "Hello" timer. Must match with neighbours.
ip ospf dead-interval __seconds__                           #### to configure "Dead" timer. Must match with meighbours.

router-id __id__                                            #### to configure router id manually

show ip ospf database                                       #### to check configurations.
show ip ospf neighbor
show ip ospf interface
show ip ospf interface brief
```

