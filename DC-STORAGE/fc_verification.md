
* interface san-port-channel 1
  * channel mode active
  * switchport mode E
  * switchport trunk allowed vsan 1
  * switchport trunk allowed vsan add 10
  * switchport speed 4000
* show flogi database
![flogi](https://user-images.githubusercontent.com/53332783/143298187-8caf9500-cb75-4e56-809e-ec5ad307a518.PNG)

* show fcns database
![fsnc](https://user-images.githubusercontent.com/53332783/143298567-3dea1d8e-ab9b-4057-bfa1-0fe0ad029635.PNG)
* show fcns database vsan 10

* show run zone
* zone name SERVER2 vsan 10
  * member pwwn 21:00:00:1b:32:07:32:23
  * member pwwn 21:00:00:04:cf:f3:73:5f
  * member pwwn 21:00:00:04:cf:84:b7:9b
* zoneset name VSAN10 vsan 10
  * member SERVER2
* zone commit vsan 10
![Zoneset](https://user-images.githubusercontent.com/53332783/143299175-2ba07a06-338e-478a-b81e-c243d8a270b3.PNG)


* show zone active --> show active connections (targets and initiator) 
* show zoneset active
* ![zone-active](https://user-images.githubusercontent.com/53332783/143299577-c568d3ba-d5fc-45c7-a24d-b7a7edea0d0d.PNG)
* show cfs application
![cfs](https://user-images.githubusercontent.com/53332783/143297642-c1944efe-8128-4aba-b3ae-81cf6e5528be.PNG)
* Configure fc port
![vsan-db](https://user-images.githubusercontent.com/53332783/143301430-a21decf8-66cd-4900-8972-0553cda740db.PNG)
![fc-port-create-and-reload](https://user-images.githubusercontent.com/53332783/143302006-0be1cc4d-310d-4f98-807d-5ebe4787ea7f.PNG)
* show fcdomain domain-list
![fc-domain](https://user-images.githubusercontent.com/53332783/143303069-2aed0bbe-aa86-4352-bbd8-03e558b7fc36.PNG)

