# Medium Access Control Protocol----MAC (Data Link Layer数据链路层)
Medium Access Control(MAC) Techniques:  
- Static Channelization
- Dynamic Medium Access Control  
  - Scheduling  
  - Random Access
  
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


