# Peer-to-Peer Protocol And Data link Layer
## Points I didn't understand----Now I get it
- Data Transfer: this state information provides a context that the layer-n peer processes use to track the exchange of PDUs. The context’s value-added services: in-order delivery of SDUs.
- control information, fields, time-out mechacinasm。 How is it set up? Where is the location?
- what is HDLC? when do we need to use it?
### 1. PDU
- Layer n peer processes carry out a protocol to provide servcie to layer n+1.
- Layer n protocol uses the services of layer n-1.
A Peer-to-Peer Model: involves the interaction of two or more processes or entities through the exchange of Protocol Data Units(PDU).  
![img](https://github.com/Chin-Sun/Telecommunicataion-Network/blob/main/img/PDU%26SDU.PNG "PDU")

### 2. Why do we need SUD?
- Abstraction and Layering: Networking models, like the OSI (Open Systems Interconnection) model or TCP/IP model, use a layered approach. Each layer communicates with its adjacent layers using a specific unit of data, abstracting the complexity of lower layers. SDUs help in this abstraction.
- Boundary Definition: SDUs define the boundaries of data at different layers.  
For instance, in the OSI model:  
At the Application Layer (Layer 7), the SDU is the data itself, such as an email or a webpage.  
At the Transport Layer (Layer 4), the SDU could be a segment or a datagram, containing parts of the application's data.
- Encapsulation and Decapsulation:  
Data encapsulation occurs when one layer adds its own header or control information to the SDU received from the upper layer.  
Decapsulation happens when the receiving layer removes its header to access the SDU and pass it to the upper layer.  
- Error Control and Flow Control:  
SDUs help in error detection, correction, and flow control mechanisms at different layers.
At the **Transport Layer**, SDUs are used to perform **error checking** and **control the flow of data**.  
- Transmission Over Networks: When data passes through different networks with varying characteristics (e.g., LAN, WAN), SDUs help adapt data to suit the requirements of each network.
- Facilitating Multiplexing and Demultiplexing: SDUs aid in multiplexing (combining multiple data streams into a single transmission) and demultiplexing (extracting individual data streams from a combined transmission) at different layers.

#### State information
State information typically includes various details and parameters associated with the communication session or connection setup. Some examples of state information might include:  
- Connection Status: Indicates whether the connection is open, closed, or in a particular state (e.g., established, terminated, or waiting).  
- Session Identifiers: Unique identifiers or session keys assigned to identify and manage a particular communication session or connection.  
- Protocol-Specific Parameters: Parameters specific to the communication protocol being used, such as sequence numbers, acknowledgment numbers, flags, timeouts, window sizes, etc.  
- Error Handling Information: Information related to error detection, recovery mechanisms, or error control (e.g., checksums, error codes, retransmission counts).  
- Resource Allocation: Details about allocated resources, such as buffer space, bandwidth, or any resources reserved for the communication session.
#### Value-Added Services:
**Each layer provides services that enhance the overall communication process beyond basic data transmission.**   
For instance, in the OSI model:  
- Network Layer (Layer 3): Provides routing services, allowing packets to traverse multiple networks.  
- Transport Layer (Layer 4): Ensures reliable data delivery, handles flow control, and provides error-checking mechanisms like checksums.  
- Application Layer (Layer 7): Offers user services, defining protocols for specific applications like HTTP for web browsing or SMTP for email.  

**Examples of Value-Added Services:**
- In-Order Delivery: Ensures data is received in the same order it was sent, preventing data misinterpretation or corruption.
- Error Detection and Correction: Using checksums or error-correcting codes to ensure data integrity.
- Flow Control: Managing the speed of data transmission to match the receiver's processing capabilities, avoiding data loss due to overflow.

#### Connectionless Services
-  Each unit carries the **necessary addressing information** to ensure it reaches its intended **destination** independently.
-  information is sent as **individual**, **self-contained units** **without** the need for establishing and maintaining a dedicated **connection** between sender and receiver.
-  Connectionless services offer simplicity and efficiency but might lack certain features of connection-oriented services, such as guaranteed delivery, error correction, or sequencing.
-   **real-time** or **speed** tasks intead of *reliability* tasks.
-   Examples: (except TCP, every protocol we know is connectionless services) UDP, IP, HTTP, HTTPS, SMTP, DNS, DHCP

####  Service Features:
- Arbitrary Message Size or Structure: Some protocols or service models allow flexibility in the size or structure of messages transmitted. They don't impose strict limits on the length or format of data being sent.  
- Sequencing: Refers to the ordering of data packets or messages. Some protocols ensure that transmitted data is received and processed in the correct order at the receiver's end.
- Reliability: Reliability ensures that data transmission is accurate and complete. Reliable protocols employ error detection, retransmission of lost packets, and acknowledgment mechanisms to ensure successful delivery.  
- Timing: Timing aspects involve synchronization and coordination between sender and receiver to manage transmission times, delays, and timeouts for efficient communication.  
- Pacing: Pacing involves controlling the rate at which data is transmitted to match the speed at which the receiver can process it, preventing overwhelm or congestion.
- Multiplexing: Multiplexing allows multiple data streams to be transmitted over a single communication channel simultaneously. It enables the sharing of network resources efficiently.
### 3. End to End versus Hop by Hop
- **End to End:** Communication spans across **the entire network(OSI; TCP/IP model)**, potentially involving multiple intermediate nodes or segments, enabling communication between devices situated at different parts of the network.
- **Hop by Hop:** Communication happens directly between devices within a single network segment
-  a "hop" refers to the movement of data from one network device or node to another. Each network device (like routers, switches, or gateways) through which data passes between source and destination constitutes a hop.
#### TCP vs. UDP
- UDP vs. TCP:
- TCP is a connection-oriented protocol that guarantees reliable, ordered, and error-checked delivery of data. It includes mechanisms for sequencing, acknowledgment, and retransmission of lost packets, ensuring data integrity and ordering.
- UDP, on the other hand, is a connectionless protocol that does not provide the same level of reliability or sequencing. UDP packets are typically sent without establishing a connection and do not guarantee delivery, ordering, or error correction.
- UDP does not maintain a connection state or provide mechanisms for packet sequencing, acknowledgment, or flow control.
- Additionally, UDP does not perform congestion control. If a congested network leads to packet loss or delay, UDP does not attempt to alleviate congestion or retransmit lost packets.
#### End to End system initiating error recovery（error detecting + retransmission） 
- Acknowledgment and Retransmission (ARQ): If the receiving end detects missing or corrupted data (using sequence numbers or checksums), it sends negative acknowledgments (NAKs) or does not send positive acknowledgments (ACKs). This prompts the sender to retransmit the missing or damaged data.
- Timeout Mechanisms: End systems set timeouts for receiving acknowledgments.
- Selective Repeat or Go-Back-N: These are techniques used in protocols like TCP to recover lost or corrupted data.
- Error Detection and Correction Codes: End systems can use error detection and correction codes (such as CRC or checksums) to identify and rectify errors in received data.
- Higher-Layer Protocols: Some application-layer protocols handle error recovery independently.

#### control information, fields, time-out mechacinasm
- Transport Layer (Layer 4 - OSI Model): This layer manages end-to-end communication and includes protocols like TCP and UDP.  
   -Timeout Mechanisms: Implemented within the transport layer protocols, such as TCP's retransmission timeout (RTO) mechanism. The value for the timeout is dynamically adjusted based on network conditions (Round-Trip Time - RTT) to handle packet loss or delays.  
 -Control Information: TCP and UDP headers contain control information fields (e.g., sequence numbers, acknowledgment numbers) necessary for reliable data delivery.
- Network Layer (Layer 3 - OSI Model):  Responsible for routing packets through the network.  
  - Control Information: Protocols like IP (Internet Protocol) add control information (source and destination IP addresses) to data packets for proper routing.  
  - Fragmentation and Reassembly: Handles segmentation and reassembly of packets if the network requires breaking data into smaller fragments.
- Data Link Layer (Layer 2 - OSI Model):  
  - Manages the physical transmission of data.  
  - Control Information: Includes addressing information (MAC addresses) for data link protocols like Ethernet.  
  - Flow Control: Provides mechanisms for managing data flow between nodes to avoid congestion.
- Application Layer (Layer 7 - OSI Model):
  - Topmost layer where application-specific protocols operate (e.g., HTTP, FTP, SMTP).
  - Timeout Mechanisms: Handled by application-layer protocols. For instance, an email client may implement a timeout mechanism to wait for server responses.
  - Control Information: Fields related to specific application data (e.g., MIME types, content length in HTTP).

### Stop And Wait *ARQ (Automatic Repeat Request)*
**The need of sequence number:**  
- Given 1 bit for ARQ: can recognize and discard the retransmitted ARQ due to time out when the delayed ARQ arrive early
- Given 1 bit for data: can discard the new one due to the loss of ARQ which causes the retransmission the new data.
**Information frames(I-frames): user packets, control frames and time-out mechanisms.**
- CRC: follows control frame. CRC includes ACKs (Acknowledgment) and NAKs (Negative Acknowledgement)

### Go-Back-And N
**HDLC** stands for High-Level Data Link Control
- The number of bits that can be allotted within a header per sequence number is limited to some number, say, m, which then allows us to represent at most 2^m possible sequence numbers, so the sequence numbers must be counted using modulo 2^m.
-  the window size Ws is 2^m - 1 or less and assume that the current sent window is 0 up to Ws - 1.
-  The reason that we use Ws=2^m-1: the receiver will not receive frame Ws until the acknowledgment for frame 0 has been received at the transmitter.
### Selective Repeat ARQ
**The Selective Rpeat ARQ**unique features:  
- the receive window is made larger than one frame so that the receiver can accept frames that are out of order but error free.  
- the retransmission mechanism is modified that only individual frames are retransmitted.  
- Selective Repeat ARQ = 出现error(帧丢失),该帧重传，通过设置发送NCK=该帧的S；后续收到的帧都存起来，R+1， 但还是发送ACK=error帧的S；直到丢失的帧重新接收到，ACK=最后的S的数值+1=R
- Go-Back-N ARQ = 出现error(帧丢失) ，发送NAK=该帧的S/此时的R；后续的帧全部不接受，R保持原值(R不加1)；等到重现传送从丢失帧开始的后续帧Ws-1个
----------------------------------------------------------------------------------------------------------------------------------------------
- without delay-bandwidth
- nf is very large-->n0==0
- Pf = error probabality
**Delay Bandwidth**
- for Stop and Wait: L = 2(t_prop+t_proc)R
- for GO Back N: L= Ws-1
- for Selective Repeat ARQ : None delay-bandwidth

### 3. Data Link Controlｓ？？？？　
#### Framing ??这一块重看---总结一下
- what is framing???? why do we need it?
- why do we need to delineate characters? How can we use these characters?
- What is GFP?
- FCS (Frame Check Sequence)
#### the difference between PPP and IP
PPP and IP work together in establishing and maintaining point-to-point communication links, with PPP handling the lower-level establishment and encapsulation of various network-layer protocols (including IP), while IP manages the routing and delivery of packets between devices across networks.
#### Point-to Point link, End-to-end link, Hop-by-Hop link
- Point-to-Point link: A point-to-point link is a type of connection established between two specific nodes or devices, providing a direct communication path between them.
- End-to-End link: An end-to-end link refers to the communication path between the source and destination nodes, which might involve multiple intermediate nodes or networks in between.
- Hop-by-Hop Link refers to the transmission method where data passes through a series of intermediate nodes, traveling from one node to another until it reaches the final destination

### HDLC Data Link Control
#### HDLC vs. PPP
- Versatility: PPP is more versatile and can accommodate various network layer protocols, while HDLC is more specific and often used in specific WAN and telecommunication settings.  
- Error Detection and Authentication: PPP offers better error detection and authentication mechanisms compared to HDLC, making it more secure and suitable for authentication-based network connections.  
- Standardization: HDLC is a standard protocol defined by ISO, whereas PPP has evolved with more features like authentication and support for multiple network layer protocols.
#### Typical Frame Exchanges
Use Unumberd Frame to build a connection first. Then Use a unique mode. Finally, use an unnumbered frame to terminate the connection. 
**Normal Response Mode**: include Information Frame, Superviser Frame  
- unbalanced+balanced
- Primary A---> Secondary B, C,.....  
**Asynchronous Balanced Mode**: Asynchronous Balanced Mode  
- balanced
- Primary A ---> Secondary B only one

### Conception Analysis
#### The difference between connectionless unacknowledged service and connectionless acknowledged service
**Connectionless Unacknowledged Services**
- UDP
- IP
- HTTP
**Connectionless Acknowledged Services:**
- Address Resolution Protocol (ARP)
- Internet Control Message Protocol (ICMP)
