# PacketLogger
Log network packets as you want.

## Usage
- Download the latest version for your API from [releases](https://github.com/PocketMine/PacketLogger/releases).
- Place the .phar in the plugins directory
- Start and stop the server to generate the default config file
- Edit the ```config.yml``` ([validate yaml](http://codebeautify.org/yaml-validator]))
- Start the server and connect. The logs are located in the `plugins/PacketLogger/` directory.

## Example config
Below a example ``config.yml`` that logs packets for the player with name `steve` and exclude some packets to reduce the size of the log.
```
#Configuration file for PacketLogger

#variables available: {name}, {clientId}, {ip}, {time}
logName: "{name}_{clientId}-{time}.log"

#These selectors will match when ANY of the conditions is met
selectors:
 mode: match #When match, it will allow when a selector is matched. When refuse, it'll log when there is no match
 name: #case insensitive
  - steve

 clientId:
  #- 123456

 ip:
  #- 192.168.0.1

#These filters decide what packets will be logged
filters:
 packetId: #Filter by the packet id (faster)
  default: true #Default value of the packets not specified here. true will log it, false will not
  #Available packet ID's can be found in https://github.com/PocketMine/PocketMine-MP/blob/master/src/pocketmine/network/protocol/Info.php
  0x8f: false # LoginPacket
  0x92: false # BatchPacket
  0x95: false # StartGamePacket
  0xba: false # CraftingDataPacket
  0xbf: false # FullChunkDataPacket
  0xc3: false # PlayerListPacket
```
