# Protocol Layers
Networks are defined by a variety of protocols, separated into layers of abstraction building on top of one another. This keeps complexity of networks in check by encapsulating a message with a series of headers each with a singular responsibility.

| OSI | DoD | protocols | devices/apps |
| --- | --- | --- | --- |
| Layers 5: Session, 6: Presentation, 7: Application | application | http, ssh, dns, dhcp | browsers, servers |
| Layer 4: Transport | host-to-host | tcp, udp | gateway |
| Layer 3: Network | internet | ip, icmp | routers, firewalls |
| Layer 2: Data Link | network | arp | switch, bridge |
| Layer 1: Physical| network | ethernet | hub |

Thus when a Host makes an HTTP request:
1) the message body is wrapped by HTTP headers responsible for describing the format of the message
1) then by TCP headers responsible for describing the packeting strategy
1) then by IP responsible for specifying the source and destination addresses
1) then by ARP responsible for identifying the network hardware cards of the hosts at those addresses
1) and then by ethernet responsible for organizing the data to be streamed through the network wires

The message is then unwrapped, layer by layer, until the original message reaches the intended server.

Wireshark and tcpdump are excellent tools to sniff individual packets and reveal the layers surrounding each message.