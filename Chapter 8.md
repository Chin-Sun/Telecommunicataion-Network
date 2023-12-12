# TCP/IP
Transmission Layer：  
Top of IP : **Transmission Control Protocol (TCP)** and **User Datagram Protocol (UDP)**  
## The TCP/IP Architecture
The TCP/IP protocol suite usually refers not only to the two most well-known protocols
called the Transmission Control Protocol (TCP) and the Internet Protocol (IP) but also
to other related protocols such as the User Datagram Protocol (UDP), the Internet
Control Message Protocol (ICMP) and the basic applications such as HTTP, TELNET,
and FTP.   
(Application Layer)FTP/HTTP--TCP(Transmission Layer)
(Application Layer)SNMP/DNS--UDP(Transmission Layer)
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/TCP%20suite.JPG  "TCO/IP protocol suite")
Protocol Data Units(PDU): --TCP--segments; ---UDP---datagrams; ----IP(Internet Layer)---packets  
In the below Figure, the IP packet is encapsulated into an Ethernet frame.  The network interface can use a variety of technologies such as Ethernet, token ring, ATM, PPP over various transmission systems, and others.  
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/TCP%20suite.JPG  "TCO/IP protocol suite")
Internet Protocol (IP)?
Internet Control Message Protocol (ICMP)?
Routing Information Protocol (RIP) ?
Dynamic Host Configuration Protocol (DHCP) provides a mechanism for the temporary allo-
cation of IP addresses to hosts

## TCP congestion control mechanism
