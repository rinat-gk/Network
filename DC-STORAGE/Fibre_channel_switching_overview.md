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
