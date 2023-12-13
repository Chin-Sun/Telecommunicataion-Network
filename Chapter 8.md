**pdf. file**  
*blue___---don't understand*  
*red___----important trial details*  
*yellow-highlight--- important*  
# TCP/IP
Transmission Layer：  
Top of IP : **Transmission Control Protocol (TCP)** and **User Datagram Protocol (UDP)**  
Examples of the protocols include TCP (protocol = 6), UDP (protocol = 17), and ICMP (protocol = 1).
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
In a Class A address (0.0.0.0 - **127**.255.255.255)(*addresses are identified by the first bit set to 0*), the first octet represents the network portion, and the remaining three octets are for host addresses.   
In a Class B address (**128**.0.0.0 - 191.255.255.255)(*addresses are identified by the first two bits set to 10*), the first two octets represent the network portion, and the remaining two octets are for host addresses.   
In a Class C address (**192**.0.0.0 - 223.255.255.255)(*addresses are identified by the first three bits set to 110*), the first three octets represent the network portion, and the last octet is for host addresses.   
Class D addresses are identified by the first four bits set to 1110, and the rest all bits are for multicast groups.  Class E addresses are identified by the first four bits set to 1111.   

**An ID that contains all 1s or all 0s has a special purpose：**    
-host ID--all 0: broadcast the packet to all hosts on the network(**x.x**.x.x)   
-Internet ID--all 1: the packet is broadcast on the local network(x.**x**.x.x)     
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
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/packets%20fragmention%202.JPG)  "fragmention 2")   
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/packets%20fragmention.JPG  "fragmention")   

**Internet Control Message Protocol (ICMP)**(with protocol number 1)  
PPT slide 16:  
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/ICMP.JPG  "ICMP")  
Echo request and echo reply messages:  
```Type 8 is used for echo request while type 0 for echo reply.``` The code field is set to zero for both types. The sequence number field is used to match the echo reply message with the corresponding echo request message. The identifier field can be used to differentiate different sessions using the echo services. The data from the echo request message is simply copied in the echo reply message and can be used for diagnostic
purposes. The data field is of variable length.    
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/echo.JPG  "echo")    

## User Datagram Protocol (UDP): unreliable & connectionless
**UDP vs IP**: UDP is a very simple protocol that provides only two additional services beyond IP: demultiplexing and error checking on data.     
--IP knows how to deliver packets to a host, but does not know how to deliver them to the specific application in the host. 
--UDP adds a mechanism that distinguishes among multiple applications in the host.   
--IP checks only the integrity of *its header*. 
--UDP can optionally check the integrity of *the entire UDP datagram*.    

Applications that use UDP include Trivial File Transfer Protocol, DNS, SNMP, and Real-Time Protocol (RTP).  
**UDP datagram**  
The source port identifies the particular application to receive replies.  
The UDP checksum field detects errors in the datagram, and its use is optional. The source host  gives all 0s to checksum if don't want to ask the destination host to compute.  
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/UDP.JPG  "UDP datagram")    
**UDP Pseudoheader**  
The pseudoheader is also **created by the source and destination hosts** only during the checksum computation and is **not transmitted**
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/UDPheader.JPG  "UDP Pseudoheader")  

## Transmission Control Protocol (TCP): 
reliable & connection-oriented & in-sequence(flow control) & *relieable* byte-stream service(e.g. Selective Repeated ARQ)  
### TCP Operation and Reliable Stream Service
--TCP connection establishment phase：transmission control block (TCB)=a connection record     
--data transfer phase： use Selective Repeat ARQ to implement reliablity  
--connection termination phase: terminate independently  
**Segment**  
--Source port and destination port: The source and destination ports identify the sending and receiving applications.  


### TCP Connection
**TCP连接建立**：三报文握手：  
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/TCP_connection_built  "Connection") 

**TCP连接断开**：四报文挥手：
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/TCP_断开连接  "Connection") 
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/TCP_断开连接2  "Connection") 
### TCP reliable byte-stream transfer
TCP可靠传输1-2-3

### TCP Congestion Mechanism
1. slow start慢开始算法：设置cwnd=1, ssthresh是拥堵窗口的门限值。一开始，发送方传输数据从1个数据段，即数据段0，开始。收到接收方对数据段0的确认后，将cwnd以指数的形式增加，cwnd=1+1=2，并传输2数据段。依次重复，直到cwnd=ssthresh为止。
2. cwnd=ssthresh 拥塞避免congestion avoidance：发送方收到接收方对data segments的确认后，每次都线性加1，cwnd=9+1=10.直到发生拥塞。拥塞的检验方法是，A发送方发送的数据包18丢失。B接收方收到A发送的数据包19，对A发送对数据包17的确认，告知A，数据包18丢失。在连续三次执行这个操作后，A重传数据包18，B对A发送对数据包21的确认。
3. fast retransmit 快重传：拥塞发生后，cwnd被设置为1, 新的ssthresh=原来的ssthresh/2，cwnd继续按照指数的形式增长。直到cwnd=ssthresh，cwnd线性加1.直到拥塞避免，执行快重传和快恢复
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/congestion_4.JPG  "congestion avoidance")  
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/congestion_5.JPG  "fast retransmit") 

### TCP Flow Control
1. A传输数据给B， B对A进行流量控制，限制A的传输数量，比如500。  
2. seq=数据位置(A的TCP报文段中)；data是数据；A每次传输100的数据给B。  
3. 如果中途有数据丢失， B给发送一个确认数据，通过ACK=1表明是确认数据段，ack=201表示前面200个数据已发送(待发送的数据段起始位置为201)，rwnd=300表示B把传输窗口设置为了300。
4. A收到B发送的确认数据段，继续传递301-400。直到A把B设置的新传输窗口中的所有数据传输完毕，等到计时器超时。
5. A的计时器超时，A重传传送失败的201-300数据。
6. B给A发送确认数据段，重新设置传递数据数量。假设rwnd=0，则A启动持续计时器，并给B发送零窗口探测报文(携带1字节数据)。
7. 如果B的窗口有空余，则给A发送确认数据，设置rwnd为空余的数值空间；如果没有空余，则给A发送确认数据，依旧设置rwnd=0
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/TCP_flow_control1.JPG  "1")  
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/TCP_flow_control2.JPG  "2")  

### TCP超时重传时间设置

Routing Information Protocol (RIP) ?
Dynamic Host Configuration Protocol (DHCP) provides a mechanism for the temporary allocation of IP addresses to hosts


