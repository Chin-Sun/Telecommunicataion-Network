**pdf. file**
*blue___---don't understand*  
*red___----important trial details*  
*yellow-highlight--- important*  
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
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/Application_Transmission.JPG  "Encapsulation of PDUs in TCP/IP")  

## Internet Protocol (IP):   
**a network ID and a host ID**.    
(**32bits** IP address)The network ID must be obtained from an organization authorized to issue IP addresses.. The host ID is assigned by the network administrator at the local sit.          
*The routers that interconnect the intermediate networks may discard packets when they encounter congestion. The responsibility for recovery from these losses is passed on to the transport layer.*???? why it is the transport layer??  

![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/routers.JPG  "How to connect with each other")  

**IP packet format**: a header part and a data part  
**header**---Version: the type of IP (IPv**4**)  
          ---Internet header length: 4bit-->32bit IP header; 5bit--->40 IP header  
          ---Total of length: 16bit---2^16 bits for the total number of IP
          ---Time to live
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/IP.JPG  "IPv4")
*A node (such as a router or a multihomed host) may have multiple network interfaces. In this situation an IP address is
usually associated with the network interface or the network connection rather than with the node. Then the node has a unique **host ID**(192.1.0.**6**), just like computers connected with this network interface(190.1.0)*       
**Class A, B, C, D, E:**   
In a Class A address (0.0.0.0 - **127**.255.255.255)(*addresses are identified by the first bit set to 0*), the first octet represents the network portion, and the remaining three octets are for host addresses. In a Class B address (**128**.0.0.0 - 191.255.255.255)(*addresses are identified by the first two bits set to 10*), the first two octets represent the network portion, and the remaining two octets are for host addresses. In a Class C address (**192**.0.0.0 - 223.255.255.255)(*addresses are identified by the first three bits set to 110*), the first three octets represent the network portion, and the last octet is for host addresses. Class D addresses are identified by the first four bits set to 1110, and the rest all bits are for multicast groups.  Class E addresses are identified by the first four bits set to 1111.   

**An ID that contains all 1s or all 0s has a special purpose：**    
-host ID--all 0: broadcast the packet to all hosts on the network(**x.x**.x.x)   
-Internet ID--all 1: the packet is broadcast ++on the local network(x.**x**.x.x)++   
-host ID--all 1: a host not to know its IP address immediately afterbeing booted up.  
 
**Subnet Addressing:** Class B:  NetworkID(8).NetworkID(8).SubnetID(9bits).HostID(7bits) 
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/subnet.JPG  "SubnetID")  

**IP Routing**: H, G-----*For example, the H flag indicates whether the
route in the given row is to a host (H = 1) or to a network (H = 0). The G flag indicates
whether the route in the given row is to a router (gateway; G = 1) or to a directly
connected destination (G = 0).*   

**Classless Interdomain Routing (CIDR)**---slides P12
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/P12.JPG  "CIDR")  

**Address Resolution**--red line on pdf.file  (*Address Resolution Protocol (ARP) only knows the IP address*)  
**Reverse Address Resolution Protocol (RARP)**: RARP only knows the *MAC* address  

**Packets Fragmentation** The flags field has three bits: one unused bit, one “don’t fragment” (DF) bit, and one “more fragment” (MF) bit. If the DF bit is set to 1, it forces the router not to fragment the packet. The MF bit tells the destination host whether or not more fragments follow. If there are more, the MF bit is set to 1; otherwise, it is set to 0. The fragment offset field identifies the location of a fragment in a packet.  
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/packets fragmention 2.JPG  "fragmention 2")   
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/packets fragmention.JPG  "fragmention")   

**Internet Control Message Protocol (ICMP)**(with protocol number 1)
PPT slide 16:
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/ICMP.JPG  "ICMP")  
Echo request and echo reply messages:
++Type 8 is used for echo request while type 0 for echo reply.++ The code field is set to zero for both types. The sequence number field is used to match the echo reply message with the corresponding echo request message. The identifier field can be used to differentiate different sessions using the echo services. The data from the echo request message is simply copied in the echo reply message and can be used for diagnostic
purposes. The data field is of variable length.  
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/echo.JPG  "echo")    

Routing Information Protocol (RIP) ?
Dynamic Host Configuration Protocol (DHCP) provides a mechanism for the temporary allocation of IP addresses to hosts

## TCP congestion control mechanism
