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

### *EtherChannel Pros & Cons*

##### Pro - cheap incremental upgrade solution
* E.g. 2 x 10GigE likely cheaper than moing to 40GigE or 100GigE
##### Pro - adds link layer redundancy
* E.g. 4 x 10GigE likely has better  resiliency than 1 x 40GigE
##### Con - flows cannot exceed the bandwidth of an individual link
* E.g. 2Gbps LAG is not a 2Gbps pipe, but 2 x 1Gbps pipes
* LAG adds lanes to the highway but does't increase the speed limit
##### Con - flows can get polarized to one member of the LAG
* LAG supports load distribution but not load balancing
* E.g. 1 x 40GigE gives better throughput than 4 x 10GigE
