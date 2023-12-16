# Peer-to-Peer Protocol And Data link Layer
## Points I don't understand
- Data Transfer: this state information provides a context that the layer-n peer processes use to track the exchange of PDUs. The context’s value-added services: in-order delivery of SDUs.
- 
### 1. PDU
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

### 1.Service Features:
- Arbitrary Message Size or Structure: Some protocols or service models allow flexibility in the size or structure of messages transmitted. They don't impose strict limits on the length or format of data being sent.  
- Sequencing: Refers to the ordering of data packets or messages. Some protocols ensure that transmitted data is received and processed in the correct order at the receiver's end.
- Reliability: Reliability ensures that data transmission is accurate and complete. Reliable protocols employ error detection, retransmission of lost packets, and acknowledgment mechanisms to ensure successful delivery.  
- Timing: Timing aspects involve synchronization and coordination between sender and receiver to manage transmission times, delays, and timeouts for efficient communication.  
- Pacing: Pacing involves controlling the rate at which data is transmitted to match the speed at which the receiver can process it, preventing overwhelm or congestion.
- Multiplexing: Multiplexing allows multiple data streams to be transmitted over a single communication channel simultaneously. It enables the sharing of network resources efficiently.
### End to End versus Hop by Hop
- **End to End:** Communication spans across **the entire network**, potentially involving multiple intermediate nodes or segments, enabling communication between devices situated at different parts of the network.
- **Hop by Hop:** Communication happens directly between devices within a single network segment 
