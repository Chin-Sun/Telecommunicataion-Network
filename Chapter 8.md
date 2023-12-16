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
**reliable & connection-oriented & in-sequence(flow control) & *relieable* byte-stream service(e.g. Selective Repeated ARQ)**  

- As indicated in Chapter 2, a TCP connection is uniquely identified by four parameters: the sender IP address and port number, and the destination IP address and port number. An end system can therefore support multiple simultaneous TCP connections. Typically the server is assigned a well-known port number and the client is assigned an ephemeral port number.
-  The segment contains a header with address information that enables the network to direct the segment to its destination application process. The segment contains a sequence number that corresponds to the number of the first byte in the string that is being transmitted. The segment also contains an Internet checksum. The TCP receiver performs an error check on each segment it receives.
-  The receiver will accept out-of-order but error-free segments, so the receive buffer can have gaps where bytes have not been received. The receiver keeps track of the oldest byte it has not yet received. It sends the sequence number of this byte in the acknowledgments it sends back to the transmitter. The receive window slides forward whenever the desired next oldest byte is received.
### TCP Operation and Reliable Stream Service
-- TCP connection establishment phase： transmission control block(TCB)=a connection record       
-- data transfer phase： use Selective Repeat ARQ to implement reliablity    
-- connection termination phase: terminate independently    
#### Segment
--Source port and destination port: The source and destination ports identify the sending and receiving applications.  
#### TCP CHECKSUM

### TCP Connection
#### Tcp Connection Establishment
1. **Host A** sends a **connection request** to host B by **setting the SYN bit**. Host A also registers its **initial sequence number** to use **(Seq_no = x)**.  
2. **Host B** *acknowledges the request* by **setting the ACK bit** and indicating ***the next data byte** to receive* **(Ack_no = x + 1)**. The “*plus one*” is needed because *the SYN bit consumes one sequence number*. At the same time, host B also *sends a request* by **setting the SYN bit** and registering its **initial sequence number** to use **(Seq_no = y)**.  
3. **Host A** *acknowledges the request* from B by **setting the ACK bit** and **confirming the next data byte** to receive **(Ack no = y + 1)**. Note that **the sequence number** is set to **x + 1**. On receipt at B the connection is established.  
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/connection_three_handshake.JPG  "TCP Three Handshakes") 
**Seq_no=:** A-->B, transfer data from A to the **Seq_no bit** of B.  Seq_no都是别人的第一个空余位
**Ack_no=:** A-->B: tell B, starting the ACK+no bit of A is ok for the next byte from B; ACK_no都是表示自己的第一个空余位

- If during a connection establishment phase, one of the hosts decides to **refuse a connection request**, it will *send a reset segment* by **setting the RST bit**  
- each **SYN message** can specify options such as *maximum segment size*, *window scaling*, and *timestamps*.  
- the **initial sequence number** should be **different** each time **a host requests a connection**. If the initial sequence number is always unique, the delayed segment is very unlikely to possess a legal sequence number and thus can be detected and discarded. Reason : If a host always uses the same initial sequence number, old segments
cannot be distinguished from the current ones.
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/connection_diffetent.JPG_Seq_no "Delay_result") 
**Note:**  
-server host B: passive open--socket, bind, listen, and accept
-client host A: active open--socket call (t1 ), connect(t2)
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/detailed_connection.JPG "More details about Connection Establishment")

#### Data Transfer: flow control
 A reliable delivery service to applications--- Selective Repeat ARQ protocol with a sliding-window mechanism (**byte basis** instead of on packet basis)   
 Advantages:    
 - prevent the sender from overwhelming the receiver with too much data.
  
**Process**
1. t0: After connection establishment, host B as a server sends byte to A. In this segment, B advertised window size (Win=1024), and expect the next byte received from A to have a sequence number(ACK_no=2000) in host B. Since host B has set the ACK when establishing connection with A, host B only need to register Seq_no=xx. Seq_no is that A expects to receive data from B to have a sequence number in host A.  
2. t1: A receive the above byte from B. And then A sends byte to B. The byte includes the    
   - Seq_no=2000(ask B to put the byte to the Sequence number bit in B)    
   - ACK_no=xx (tell B, next byte from B should be put starting from xx bit in A), Since the previous byte from B doesn't have any data, the ACK_no in A is still xx.  
   - Win= 512(tell B, the window size is 512. After exceeding this window size of 512, B is not allowed to transfer any data)  
   - data=1025~2048(This number is limited by A itself.)  
3. t2: A continues to transfer new data which includes 1024 bytes. And B delay to send the acknowledgement for the previous data from A.  
4. t3: B sends data to A and register ACK_no=2000+1024*2=4048(it also tell A, B has received the previous data correctly), Seq_no=xx, Win=512(new window size for A), Data=1~128  
5. t4: A sends data to B and register ACK_no=xx+128; Seq_no=4048, Win=1024(shrink window size to new size of 1024 bytes); Data = 4028~4048+512    
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/flow_control.JPG "flow control")

**Advantages of Delay lay transmission so that the acknowledgments can be piggybacked to the data segment**  
- reduce the waste of bandwidth
- **Solution**: Nagle algorithm---TCP transmits all the characters that have been waiting in the buffer in a single segment.
- **Problem of the above algorithm:** We hope whether TCP buffer characters or not depends on the congestion condition of the network. *When delay is small, implying that the network is lightly loaded, only a few characters are buffered before an acknowledgment arrives. In this case TCP has the luxury of transmitting short segments. However, when delay is high, indicating that the network is congested, many more characters will be buffered. Here, TCP has to transmit longer segments and less frequently. In some cases the Nagle algorithm needs to be disabled to ensure the interactivity of an application even at the cost of transmission efficiency.* 
- **Problem of the above algorithm--silly window syndrome:**  It can be avoided by having the receiver not advertise the window until the window size is at least as large as half of the receive buffer size, or the maximum segment size. The sender side can cooperate by refraining from transmitting small segments.  

**Maximum Segment Size (MSS)**  
- TCP provides **16 bits** to specify the MSS option, so the maximum block of data that can be carried in a segment is **65,495 bytes**;  
- The Max Data size is  65,535 **-** 20 bytes for the IP header **-** 20 bytes for the TCP header. Then the overhead would only be **0.06 percent.**  
- In TCP **the default MSS** is **536 bytes**. The corresponding **IP packet** is then **576 bytes** long. In this case **40 bytes** out of every **576 bytes**, that is, **7 percent** are overhead.  
- Ethernet limits the MSS to 1460 bytes
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/head_overhead.JPG "Overhead")

**Sequence Number Wraparound and Timestamps**  
-*Wraparound:*  32-bit sequence number--->2^32 bytes;  But TCP uses Selective Repeat ARQ, so the maximum allowable window size is 2^31 bytes. Therefore The 32-bit sequence number wraps around  
-*Timestamps--Round-Trip time:* In a T-1 line(1.544 Mbps) the time required is (2^32 × 8)/(1.544 × 106) = 6 hours. In a T-3 line (45 Mbps), the wraparound will occur in 12 minutes.  

   **1 Mbps = 10^6 bps** (when calculation, you need to switch Mbps to bps because it is based on bits' calculation)  
   
- The original TCP specification assumed a maximum segment lifetime (MSL) of 2 minutes. Clearly, sequence number wraparound becomes an issue for TCP operating over very highspeed links.
- 
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/wrapround.JPG "? wrapround")

**Delay-Bandwidth Product and Advertised Window Size**  
- round-trip time = 100 ms;  The number of bytes in **T1 line(1.544 Mbps)** is 1.544 × 10^6 × 0.100/8 = 19,300 bytes.  
                             The number of bytes in **T3 line(45 Mbps)** is 562,500 bytes  
-  The **normal maximum advertised window size** is only **65535**, which is not enough for the T-3 line.  
-  The **window scale option**, however, **allows a window size of up to 65,535 × 214 = 1 gigabyte**, which is enough to handle these cases.  

**Chinese version of Process**  
1. A传输数据给B， B对A进行流量控制，限制A的传输数量，比如500。    
2. seq=数据位置(A的TCP报文段中)；data是数据；A每次传输100的数据给B。  
3. 如果中途有数据丢失， B给发送一个确认数据，通过ACK=1表明是确认数据段，ack=201表示前面200个数据已发送(待发送的数据段起始位置为201)，rwnd=300表示B把传输窗口设置为了300。  
4. A收到B发送的确认数据段，继续传递301-400。直到A把B设置的新传输窗口中的所有数据传输完毕，等到计时器超时。  
5. A的计时器超时，A重传传送失败的201-300数据。  
6. B给A发送确认数据段，重新设置传递数据数量。假设rwnd=0，则A启动持续计时器，并给B发送零窗口探测报文(携带1字节数据)。  
7. 如果B的窗口有空余，则给A发送确认数据，设置rwnd为空余的数值空间；如果没有空余，则给A发送确认数据，依旧设置rwnd=0  
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/TCP_flow_control1.JPG  "1")  
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/TCP_flow_control2.JPG  "2")  

#### TCP Connection Termination
(1) Upon receiving a FIN segment, a TCP entity informs its application that the other entity has terminated its transmission of data.  
(2) Host B sends an **ACK segment** to **acknowledge receipt of the FIN segment from A**. Note that the FIN segment uses one byte, so the ACK is **5087** in the example.  
(3) The **direction of the flow from B to A is still open**. host B **sends 150 bytes** in one segment, **followed** later by a **FIN segment**. Host A sends an acknowledgment.  
(4) The TCP in host **A** then enters the TIME_WAIT state and starts the TIME_WAIT timer with an initial value set to twice the maximum segment lifetime (2MSL).  

The **only valid segment** that can arrive while host A is in the TIME_WAIT state is a **retransmission of the FIN segment** from host B (for example, if host A’s ACK was lost, and host B’s retransmission time-out has expired). If such a FIN segment arrives while host A is the TIME_WAIT state, then the ACK segment is retransmitted and the TIME WAIT timer is restarted at 2MSL.???  

(5) When the TIME_WAIT timer expires, host A closes the connection and then deletes the record of the connection.  

![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/TCP_graceful_close.JPG  "TCP Graceful Close")   

**The TIME WAIT state protects future incarnations of the connection from delayed segments.**  
- The first MSL accounts for the maximum time a segment in one direction can remain in the network  
- the second MSL allows for the maximum time a reply in the other direction can be in the network.  

TCP provides for an abrupt connection termination through reset (RST) segments.
- **An RST segment is a segment with the RST bit set.**
If an application decides to terminate the connection abruptly, it issues an ABORT command, which causes TCP to discard any data that is queued for transmission and to send an RST segment. A TCP module that receives the RST segment then notifies its application process that the connection has been terminated.  

example:  

- an RST segment is sent when a connection request arrives for an application process that is not listening on the given port.
- an application in host A may crash. The TCP module in host B, unaware of the crash, may then send a segment.
#### TCP STATE TRANSITION DIAGRAM
![GitHub set up](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/Chapter8/state_transition.JPG  "State Transition Diagram")   

#### TCP Congestion Control
The **advertised window** does not prevent the buffers in the **intermediate routers** from **overflowing**, hence the **congestion situation**.

-Because the **IP layer does not** **implement a mechanism to control congestion**, it is up to the **higher layer to detect congestion** and take proper actions.  

The objective of conjestion flow have each sender transmit just the right amount of data to keep the network resources **utilized but not overloaded**.

Solution: the TCP protocol defines another window, called the **congestion window**, which specifies the maximum number of bytes that a TCP sender is allowed to **transmit with the assumption that congestion will not be triggered with the given amount of data**.


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


