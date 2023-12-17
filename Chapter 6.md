# Medium Access Control Protocol----MAC (Data Link Layer数据链路层)
Medium Access Control(MAC) Techniques:  
- Static Channelization
- Dynamic Medium Access Control  
  - Scheduling  
  - Random Access
### Points I don't understand:
- What is Transfer Delay?????? how to calculate?
### Switched Networkds
- Point-to-Point Connections: Switched networks create individual, dedicated connections between two communicating devices (nodes) for the duration of a communication session.
- Dedicated Communication Paths: When two nodes need to communicate, the network establishes a dedicated path between them, ensuring that other devices do not share this specific path during that time.
- Resource Allocation: Switched networks efficiently allocate network resources, allowing different connections to use the same physical infrastructure without interfering with each other.
- Types of Switching: There are different types of switching used in switched networks, including Circuit Switching and Packet Switching:  
  - Circuit Switching: Establishes a dedicated communication path between nodes for the duration of the communication session. Examples include traditional telephone networks.
  - Packet Switching: Divides data into packets that are independently routed across the network, allowing shared use of network resources. Examples include networks based on protocols like TCP/IP.
- Scalability and Efficiency: Switched networks offer scalability, enabling multiple simultaneous connections without congestion, thereby enhancing network efficiency.
- Example: Ethernet networks utilizing switches to create dedicated communication paths between devices within a LAN (Local Area Network) are an example of switched networks. When devices communicate within an Ethernet LAN, the switch forwards data directly to the destination device without sharing the data across the entire network, enhancing efficiency and reducing collision and congestion.

### Approaches of channel sharing techniques :
Ring Network has features of both approaches.  
**Centralized**  
Definition:   
- In a centralized approach, there's **a central point** or station that manages or controls the **communication among multiple stations** within the network.
**Distributed**  
Definition:  
- In a distributed approach, communication occurs **directly between all stations** **without the requirement for a central control** point or station.

### Delay-bandwidth Product and MAC Performance
The selection of a MAC protocol for a given situation depends on delay-bandwidth product and throughput efficiency.  
**Delay-Bandwidth Product:**  
- Definition: The delay-bandwidth product refers to **the maximum amount of data** that can be "in flight" over a network link based on its bandwidth and delay characteristics.
- Delay Time **t_prop**: Refers to the time taken for a data packet to travel from the sender to the receiver through a network.
**Throughput Efficiency:**  
- Definition: Throughput efficiency refers to **the ratio of** the **actual data transmitted rate** **over** the network to the **maximum potential data transfer rate**.
- For instance, some protocols might be more efficient in **handling high traffic loads** and **minimizing collisions** (e.g., **CSMA/CD** in **Ethernet**), while others might be optimized for **lower latency** or **improved fairness** in sharing the medium (e.g., CSMA/CA in **wireless networks**).  

this figure represents the relationship between the load on a communication channel, the resulting frame transfer delays, and how these factors vary concerning the parameter 'a.' It illustrates how the delays increase as the channel becomes overloaded and how different values of 'a' affect the network's capacity utilization and coordination efficiency.  

### MAC vs. HDLC
#### Differences
**Purpose:**  
- **MAC** protocols primarily focus on controlling access to the **shared communication medium** among **multiple devices**, **managing collisions**, and providing **fair access**.
- **HDLC**, is designed for **reliable** **point-to-point** or **multipoint** data transfer, offering **framing**, **error control**, and **flow control** mechanisms.
**Scope:**
- **MAC** protocols are more commonly associated with **LANs** or **wireless networks** where multiple devices share a common communication medium.
- **HDLC** is often used in point-to-point or dedicated connections, including **WAN links**, **leased lines**, or **serial connections**.
**Application:**
- **MAC** protocols are used to manage and regulate access to the shared communication channel to avoid collisions and ensure efficient data transmission among multiple devices.
- **HDLC** is used for reliable data transfer and communication between directly connected nodes or over dedicated links.

## Random Access
### Alpha
- **S**: Let S be **the arrival rate of new frames** to the system **in units of frames/X seconds**(for example, If the rate of frame arrivals is 5 frames/X seconds, it signifies that, on average, 5 frames arrive or are transmitted within a span of X seconds.). S is normalized throughput.  
-  We assume that **all frames eventually make it through** the system, so **S** also **represents the throughput** of the system. Now **the actual arrival rate** to the system consists of **new arrivals and retransmissions**.

  
- For a given value of S, say, S = 0.05, there are two associated values of G. This is in agreement with our intuition that the system has two modes: one associating a small value of G with S, that is, S ≈ G, and another associating a large value of G with S, that is, G  S when many stations are backlogged.
- the graph also shows that values of S beyond 1/2e are not attainable.
-  Note that the maximum value of S occurs at G = 1/2, which corresponds to a total arrival rate of exactly one frame per vulnerable period. This makes sense since two or more arrivals in a vulnerable period result in a collision.
![image](https://github.com/Chin-Sun/Telecommunicataion-Network/img/Alpha.JPG "Throughput S versus load G" )

### Slotted Alpha
- Synchronization with Time Slots: Slotted ALOHA introduces a synchronized timing mechanism where **time is divided into discrete slots or intervals**, each representing **a specific time unit**.  
- Time Slot Constraint: Stations participating in Slotted ALOHA are restricted to **initiating transmissions** only at the **beginning** of these predefined time slots.
- Frame Transmission and Time Slot Occupation: Frames transmitted in Slotted ALOHA are assumed to be of **constant size** and **occupy precisely one-time slot**.
- So that's why the vulnerable time is X instead of 2X
- Note that the maximum value of S=1/e occurs at G = 1

### Carrier Sense Multiple Access
The CSMA schemes improve over the ALOHA schemes by reducing the vulnerable period from one- or two-frame transmission times to a single propagation delay t_prop.

## CSMA-CD(Carrier Sense Multile Access / Collision Detection)
- When the channel becomes idle, **stations contend for the channel** by **transmitting and listening to the channel** to see if they have successfully captured
the channel.
- A station with a frame **first senses** the channel and **transmits if the channel is idle**. 
- If the channel is **busy**, the station **uses one of the possible strategies from CSMA**; that is(Non-persistent: ), the station **persist and attempt transmission** with probability **p**; Or with the probability, the station can use back-off immediately.
- If a **collision is detected during transmission**, then **a short jamming signal is transmitted** to ensure that **other stations know that collision has occurred** **before aborting the transmission**. 
- The station stop transmission. It uses the backoff algorithm to schedule a future resensing time and then retransmits.
  
- **1-persistent CSMA-CD** can be analyzed by assuming that time is divided into **mini slots** of length **2t_prop seconds** to ensure that stations can always detect a collision. Each **contention interval** takes **2t_prop seconds**.


