## SAN SWITCHES

* Connect servers to storage
   * Traditionally FC to FC switches
   * Server is called the **initiator**
   * Storage is called the **target**
* Like IP routers, can do protocol conversations
   * FC to iSCSI
   * FC to FCoE
   * FC to FCIP
* Directors vs. Switches
   * Directors are Just Bigger switches
     * Think Catalyst 6509 vs Catalyst 2960
   * Higher port density
   * Higher redundancy (power, supervisors, line cards)


#### Host Bus Adapters (HBAs)

* NIC card for SAN
  * Connects servers and storage to SAN switches
* Typically three types of HBAs
  * Fibre Channel HBAs
    * SAN traffic only
    * 1/2/4/8/16 Gbps
  * iSCSI HBAs
    * 1/10 Gbps LAN plus iSCSI hardware offload
  * FCoE Converged Network Adapter (CNA)
    * E.g. "Unified Fabric"
    * 10Gbps LAN plus FCoE hardware offload
