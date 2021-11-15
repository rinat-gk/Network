## What is Fibre Channel?

* From a high level, replaces SCSI disk cable with a network
* Protocol stack primarily used to send SCSI commands over the SAN
   * SCSI ---> Small Computer System Interface
   * Technically you could run IP over FC, but main application is SAN
   * RFC 2625 - IP and ARP over Fibre Channel
   * Standard "T11" per InterNational Commetee for Information Technology Standards (INCITS)
   * http://www.t11.org/
   * E.g. not IEEE or IETF
   * FCoE is T11's FC-BB-5 standard
   * Fibre Channel Protocol (FCP) is analogous to TCP

## Fibre Channel Topologies

* Support three types of topologies
* Point-to-Point (FC-P2P)
  * Initiator (server) and Target (storage) directly connected
* Arbitrated Loop (FC-AL)
  * Logical ring topology, similar to Token Ring
  * Implies contention is required on the ring
* Switched Fabric (FC-SW)
  * Logical equivalent to a switched Ethernet LAN
  * Switches manage the fabric allowing any-to-any communication without contention
    * Similar to how CSMA-CD is removed with Ethernet Switching

## Fibre Channel Port Types

* FC has different port types to define a port's function
* N_port - Node Port
  * End host (target or initiator) in P2P or Switched Fabric
* NL_port - Node Loop Port
  * End host in an Arbitrated Loop
* F_port - Fabric Port
  * Switch's port that connects to a Node Port
* FL_Port - Fabric Loop port
  * Switch's port that connects to a Node Loop Port
* E_Port - Expansion Port
  * Inter Switch Link (ISL)
* TE_port - Trunking Expansion Port
  * Extendedn ISL, analogous to an 802.1q trunk


## Fibre Channel Addressing

* FC addressing is analogous to IP over Ethernet
  * IP addresses are logical and manually assigned
  * Ethernet MAC addresses are Physical and burned in
* FC World Wide Names (WWNs)
  * 8 byte address burned in by manufacturer
* FC Identifier (FCID)
  * 3 byte logical address assigned by fabric

## FC World wide Names

* WWNs is FC's 8 byte physical address
* WWN is subdivided futher into ...
* World wide Node Name (WWNN or nWWN)
  * Switch, server or disk's physical address
* World wide Port Name (WWPN or pWWN)
  * Switch, server, or disk's port's physical address
  * E.g. a switches, HBAs, and arrays havemore than one port
* WWN is not used for data plane switching

## FC Identifiers

* FCID is FC's 3 byte logical address
* FCID id subdevided into three fields
  * Domain ID
     * Each switch gets a Domain ID
  * Area ID
     * Group of ports on a switch have an Area ID
  * Port ID
     * End station connected to switch gets a Port ID
* FCID is used for the actual data plane traffic switching

## Fibre Channel Domain IDs

* Domain IDs identify a switch in the fabric
* Can be manually assigned, Otherwise will be automatically assigned by the Principle switch
* Principle Switch is analogius to the STP Root Bridge, and chosen based on an election
* No configuration needed for PS election

## Fibre Channel Routing

* FC does not use flooding to build topology like Ethernet does
* Fabric Shortest Path first (**FSPF**) is used to route traffic between switches
  * Same Dijkstra SPF as OSPF and IS-IS
  * Node ID in the SPT is the FCID's Domain ID
  * Traffic is routed via lowest cost path between domain IDs
  * ECMP is supported for equal SPT branches
  * Unequal cost load distribution is not supported
* FSPF runs automatically as a Fabric Service
  * No configuration required
  * Can customize knobs, but typically not required
  * 
## Fibre Channel Logins

* Ethenet networks are connectionless
  * Traffic in the data plane results in topology learning in the control plane
* Fibe Channel networks are connection oriented
  * All end sattions must first register with the control plane of the fabric before sending any traffic
* Fabric registration has three parts
  * Fabric Login (FLOGI)
  * Port Login (PLOGI)
  * Process Login (PLRI)

## FLOGI, PLOGI & PLRI

* Fabric Login (FLOGI)
  * Node Port (N_Port) tells switch's Fabric Port (F_Port) it wants to register
  * Switch learns the WWNN and WWPN of Node
  * Switch assigns FCID to Node
* Port Login (PLOGI)
  * End-to-End login between Node Ports
  * Initiator tells Target it wants to talk
  * Used for applications such as end-to-end flow control
* Process Login (PLRI)
  * Upper layer protocol login negotiation between Node Ports 

## Fibre Channel Name Server

* Fibre Channel Name Server (FCNS) is analogous to ARP Cache
* Used to resolve the WWN (Physical address) to the FCID (Logical address)
* Like Principle switch and FSPF, FCNS is a distributed fabric service that requires no configuration

## Zoning

* By default all initiators learn about all targets during the login process
  * FCNS maintains the mappings of everyone's WWPN to FCID
* Servers mounting the wrong volumes can corrupt data
  * E.g. Windows NTFS & MBR not compatible with Linux GPT
* Zoning prevents this by limiting which resources an initiator can use
  * Zoning is analogous to ACLs in Ethernet & IP world
  * Associates WWN's, FCID's, aliases, etc. to control who can talk to who
* Like FCNS, Zoning is a distributed fabric service

## Virtual SANs (VSANs)

* Traditionally multiple SANs were designed as physical separate networks
  * i.e. "SAN Islands"
  * Physical separation is costly in terms of equipment, power, space, cooling, management, etc.
* VSANs solve the isolation problem similar to how VLANs segment broadcast domains
  * Isolates the management and failure domain of the network
  * Separates FLOGI, FCNS, Zoning, Aliases, etc. per VSAN
* With VSANs, E Ports now become TE Ports
  * Similar to 802.1Q trunks in Ethernet


## SAN Port Channeling

* Like Ethernet Port-Channeling, SAN PCs can be used to aggregate the bandwidth of physical links
* Supports Port Channeling Protocol (PCP) for negotiation of links
  * Similar to 802.3ad LACP in Ethernet
  
