# **ETHERCHANNEL**

* What is EtherChannel
  * Technique for aggregating the bandwidth of physical links together

## *EtherChannels consists of two parts*
* Port-Channel interface
  * Logical interface representing the link bundle
* Member interfaces
  * Physical links that are part of the link bundle

## *LAG goal is to hide the member interfaces from the upper layer protocols*
* E.g. STP sees one 2Gbps link not 2 x 1Gbps link
* Result is active/active forwarding instead of active/standby with STP
