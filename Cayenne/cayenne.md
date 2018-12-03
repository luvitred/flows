## Connecting CloudGate to Cayenne via LuvitRED ##

This tutorial helps you in getting your CloudGate Gateway conencted to your Cayenne Platform in jsut a few simple steps.
**LuvitRED** is visual tool for wiring edge-to-edge on CLoudGate gateways.

Start with installing LuvitRED on your CloudGate from [www.CloudGateUniverse.com](https://https://cloudgateuniverse.com/docs/luvitred) (Log in to your free account is needed)

### Configuring LuvitRED on CloudGate ###

Copy-paste the following json code in LuvitRED via 'Import From Clipboard':
    
    [{"id":"4a7c1ca6.cf2cb4","type":"debug","__package":"luvitred/core-core","__version":"0.1.0","name":"","active":true,"highlight":"blue","console":"false","complete":"true","x":950,"y":575,"z":"1f6594a7.05c46b","wires":[]},{"id":"4ab618cb.0e61e8","type":"mqtt in","__package":"luvitred/core-io","__version":"0.1.0","name":"MQTT from Cayenne","topic":"v1/username/things/clientID/data/channel","qos":"2","broker":"_ADD_","x":750,"y":575,"z":"1f6594a7.05c46b","wires":[["4a7c1ca6.cf2cb4"]]},{"id":"4c3725a6.9a9f64","type":"mqtt out","__package":"luvitred/core-io","__version":"0.1.0","name":"MQTT to Cayenne","topic":"10","qos":"0","queueenabled":false,"queue":"_ADD_","retain":"false","broker":"_ADD_","x":737.5,"y":500,"z":"1f6594a7.05c46b","wires":[]},{"id":"99ad34c4.bd6b8","type":"inject","__package":"luvitred/core-core","__version":"0.1.0","name":"Generate random #","key":"","topic":"","payload":"","payloadType":"rinteger","fromval":"0","toval":"100","repeat":"60","crontab":"","once":true,"x":275,"y":500,"z":"1f6594a7.05c46b","wires":[["348e1253.17d23e"]]},{"id":"348e1253.17d23e","type":"function","__package":"luvitred/core-core","__version":"0.1.0","name":"Configure payload","func":"if not msg then\n-- called on startup\nreturn\nend\n\nmsg.payload = 'temp,c=' .. msg.payload\nmsg.topic = 'v1/username/things/clientID/data/channel'\n\nreturn msg","startnil":false,"outputs":1,"x":512.5,"y":500,"z":"1f6594a7.05c46b","wires":[["4c3725a6.9a9f64"]]},{"id":"3a3ce2a2.435c86","type":"comment","__package":"luvitred/core-core","__version":"0.1.0","name":"README","info":"Hi There!\n\nPlease do not forget to change the topic in the 'MQTT from Cayenne' node and in the 'Configure payload' node.\nAlso adjust the MQTT Username, password and ClientID in the MQTT Config node to reflect your credentials.\n\nGood luck!","x":225,"y":425,"z":"1f6594a7.05c46b","wires":[]}]


Please do not forget to change the topic in the 'MQTT from Cayenne' node and in the 'Configure payload' node.
Also adjust the MQTT Username, password and ClientID in the MQTT Config node to reflect your credentials.


Once completed, press the red 'Deploy' button in the top right corner to compile the code in real time.

Good luck!
