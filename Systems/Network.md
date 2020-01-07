# Network

## OSI model
* Open Systems Interconnection model
  * Each layer is **independent**
  * A layer can only interact with a **contiguous layer**

## Layers
|Layer|Id|Data|Host|Hardware|
|-|-|-|-|-|
|Physical<br>machine ⇔ machine|RJ45 socket|10BT/100BT/1000BT<br>• crossed<br>• straight|collision handling (CSMA/CD) in half duplex|Hub<br>Bus topology: half duplex<br>• send to all RJ45|
|Data Link<br>machine ⇔ network|MAC on 6 bytes:<br>• 3 for constructor<br>• 3 for card<br>ff:ff:ff:ff:ff:ff : broadcast|Trame:<br>• DST: 6<br>• SRC: 6<br>• Protocol layer 3: 2<br>• Data: 46-1500<br>• CRC: 4|if DST is local MAC,<br>send Data to layer 3|Switch<br>Star topology: full duplex (TX + RX)<br>CAM table: RJ45 socket, MAC, VLAN, TTL<br>• SRC + RJ45, reset TTL in CAM<br>• if DST is not local MAC, send trame to all RJ45<br>Buffer trames to handle collisions|
