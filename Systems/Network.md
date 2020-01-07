# Network

source: https://openclassrooms.com/fr/courses/857447-apprenez-le-fonctionnement-des-reseaux-tcp-ip

## OSI model
* Open Systems Interconnection model
  * Each layer is **independent**
  * A layer can only interact with a **contiguous layer**

## Layers
|Layer|Id|Data|Host|Hardware|Commands
|-|-|-|-|-|-|
|**Physical**<br>machine ⇔ machine|RJ45 socket|10BT/100BT/1000BT<br>• crossed<br>• straight|collision handling (CSMA/CD) in half duplex|**Hub**<br>Bus topology: half duplex<br><br>on incoming data:<br>• send to all RJ45||
|**Data Link**<br>machine ⇔ network|MAC: b1:b2:b3:b4:b5:b6<br>• b1:b2:b3: constructor<br>• b4:b5:b6: card<br>ff:ff:ff:ff:ff:ff : broadcast|Frame<br>• MAC DST: 6<br>• MAC SRC: 6<br>• Protocol layer3: 2<br>• Data: 46-1500<br>• CRC: 4|if MAC DST is local MAC,<br>send data to layer3|**Switch**<br>Star topology: full duplex (TX + RX)<br><br>MAC table:<br>• RJ45 socket<br>• MAC<br>• VLAN<br>• TTL<br><br>on incoming data:<br>• MAC SRC + RJ45, reset TTL in table<br>• if MAC DST is not in table, send trame to all RJ45<br><br>Buffers trames to handle collisions|*ifconfig*|
|**Network**<br>network ⇔ network|IP: b1.b2.b3.b4/mask<br>• first in range: network<br>• last in range: broadcast<br>private IPs:<br>• 10.0.0.0/8<br>• 172.16.0.0/12<br>• 192.168.0.0/16|Datagram<br>• ???<br>• IP SRC: 4<br>• IP DEST: 4<br>• Data: \*|if IP DST is local IP,<br>send data to layer4|**Router**<br><br>Routing table:<br>• network (0.0.0.0: default)<br>• gateway IP (0.0.0.0: local)<br><br>on incoming data:<br>• if DST IP belong to a network in table, send to gateway IP (see ARP)|*route -n*|
