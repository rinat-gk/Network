
* interface san-port-channel 1
  * channel mode active
  * switchport mode E
  * switchport trunk allowed vsan 1
  * switchport trunk allowed vsan add 10
  * switchport speed 4000


* show fcns database
* show fcns database vsan 10

* show run zone
* zone name SERVER2 vsan 10
  * member pwwn 21:00:00:1b:32:07:32:23
  * member pwwn 21:00:00:04:cf:f3:73:5f
  * member pwwn 21:00:00:04:cf:84:b7:9b
* zoneset name VSAN10 vsan 10
  * member SERVER2
* zone commit vsan 10


* show zone active --> show active connections (targets and initiator) 
* show zoneset active
* 36.48
