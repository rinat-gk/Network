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
