# Internet Protocol (IP)
IPv4 addresses are 32-bit addresses divided into 4 "octets" - 8-bits (or 1 byte) separated by a dot(.)

Example
>192.168.56.100

Which in binary is
>11000000.10101000.00111000.01100100

IP addresses exist on a series of ranges that represent the type of server they inhabit:

| - | First octet | Second octet | Third octet | Fourth octet |
| --- | --- | --- | --- | --- |
| Class A | Network | Host | Host | Host |
| Class B | Network | Network | Host | Host |
| Class C | Network | Network | Network | Host |

Classes help us separate which octets represent the network address from the octets representing the host address. There are special rules for the first octet that help separate each class into their own ranges:

| Class | Rule | Range |
| --- | --- | --- |
| A | First bit is 0 | 0 - 127 |
| B | First two bits are 10 | 128 - 191 |
| C | First three bits are 110 | 192 - 223 |

The range between 224 - 255 are reserved for special Class D and E networks.

## Subnet
The subnet mask helps mathematically separate a host address from its network address using bits set to 1s. 

Example
>255.255.255.0

which in binary is
>11111111.11111111.11111111.00000000

When applied to our IP example above:
>192.168.56.100

The first three octets are masked, leaving just 100.

## CIDR
Classless Inter-Domain Routing is how ISPs can allocate a group of IPs to their clients, and is usually denoted by an IP address followed by a slash and a number which represents the number of 1 bits.

For example, a /24 represents 255.255.255.0
/25 represents 255.255.255.128
