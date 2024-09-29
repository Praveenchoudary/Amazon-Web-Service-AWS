An Application Load Balancer (ALB) is a service provided by cloud computing platforms, such as Amazon Web Services (AWS), that distributes incoming web traffic across multiple targets, such as Amazon EC2 instances, containers, or IP addresses, within one or more availability zones. ALBs operate at the application layer (Layer 7) of the OSI model and are designed to efficiently route and balance traffic based on content, making them well-suited for modern web applications.

So, what is AWS Load Balancing?
A Load Balancer distributes the load evenly to multiple instances. This means when a request comes to the Load Balancer from a client, it sends the request to one of the available instances. Here is an example:

* You, the client, type www.foo.com in your browser.
* Your request goes over the internet to the Load Balancer responsible for www.foo.com.
* The Load Balancer forwards your request to a web server.
* The web server receives the request and sends back the homepage of www.foo.com via the Load Balancer.
* Your browser receives the www.foo.com page you requested.
* All this obviously done in a few milliseconds.

  

  How Packet flow from Client to Server or how does a packet flow within the 7 layers of the OSI Model?
The journey of a packet from a client to a server typically involves the seven layers of the OSI (Open Systems Interconnection) model. Each layer in the model performs specific functions, and the packet goes through these layers during transmission. Here’s a high-level overview:

1. Physical Layer (Layer 1):
— Deals with the physical connection between devices.
— Transmits raw bits over a physical medium like cables.

2. Data Link Layer (Layer 2):
— Responsible for creating a reliable link between two directly connected nodes.
— Frames the raw bits into frames and adds addressing (MAC addresses).

3. Network Layer (Layer 3):
— Manages logical addressing and routing of packets between devices.
— Adds IP addresses to frames and determines the next hop based on routing tables.

4. Transport Layer (Layer 4):
— Ensures end-to-end communication and flow control.
— Breaks down large messages into smaller segments.
— Adds source and destination port numbers.

5. Session Layer (Layer 5):
— Establishes, maintains, and terminates sessions between applications.
— Manages dialog control and synchronization between devices.

6. Presentation Layer (Layer 6):
— Deals with the syntax and semantics of the information exchanged.
— Translates data between the application layer and the lower layers.
— Handles data compression, encryption, and formatting.

7. Application Layer (Layer 7):
— Provides network services directly to end-users or applications.
— Supports communication and data exchange between applications.
— Examples include HTTP, SMTP, and FTP.

When a packet travels from a client to a server:

- At the client, the packet starts from the Application Layer, where it’s encapsulated with layer-specific headers and data.
- The packet then goes down through the layers (Presentation, Session, Transport, Network, Data Link, Physical) in sequence.
- At each layer, additional information is added to the packet.
- The packet is transmitted across the physical medium.
- At the server, the packet goes up through the layers in the reverse order (Physical, Data Link, Network, Transport, Session, Presentation, Application).
- At the Application Layer of the server, the original data is extracted.

This process of encapsulation and decapsulation at each layer ensures that the data is correctly transmitted and received between the client and server in a structured and standardized manner.

Type of Load Balancers:
AWS offers three types of load balancers to suit different needs:

1. Application Load Balancer (ALB): Best suited for routing HTTP/HTTPS traffic and provides advanced application-level routing and content-based routing.

2. Network Load Balancer (NLB): Ideal for handling TCP/UDP traffic with extremely high performance and low latency, often used for TCP-based applications.

3. GateWay Load Balancer (GWLB): Gateway Load Balancers excel at distributing traffic across multiple servers (high availability) and optimizing network performance (fast response times) for web applications and services.

Each type is designed to cater to specific use cases and provides different features and capabilities.


Examples of Load Balancers:
AWS Application Load Balancer (ALB)
AWS Network Load Balancer (NLB)
AWS Gateway Load Balancer (GWLB)
F5 BIG-IP
NGINX
HAProxy
Citrix ADC
Microsoft Azure Load Balancer
Google Cloud Load Balancer

When to use Application Load Balancer (ALB):
AWS Application Load Balancer (ALB) is referred to as an L7 (Layer 7) load balancer because it operates at the application layer of the OSI model. The OSI model has seven layers, and the application layer (Layer 7) is the highest. ALB specifically focuses on routing and load balancing HTTP and HTTPS traffic at the application layer, making decisions based on content, such as URL paths and headers.

Use ALB when:

1. Routing Based on Content: ALB is designed for routing traffic based on content, allowing you to create rules to direct requests to different target groups based on the content of the request.

2. Support for Containers: ALB is well-suited for containerized applications, offering features like host-based and path-based routing to different containers.

3. WebSockets and HTTP/2 Support: ALB supports WebSocket communication and HTTP/2, providing efficient communication channels for modern web applications.

4. SSL/TLS Offloading: ALB can offload SSL/TLS termination, freeing backend servers from the overhead of encryption and improving overall performance.

5. Integration with AWS Services: ALB integrates seamlessly with various AWS services, including AWS ECS (Elastic Container Service) and AWS Lambda, providing a flexible and scalable solution for modern application architectures.

6. Advanced Health Checks: ALB supports advanced health checks, allowing you to define custom health check conditions based on the application’s response.

In summary, ALB is suitable for scenarios where advanced content-based routing and application-layer features are required, making it a powerful choice for modern web applications and microservices architectures.

When to use Network Load Balancer (NLB):
AWS Network Load Balancer (NLB) is referred to as an L4 (Layer 4) load balancer because it operates at the transport layer of the OSI model. The OSI model has seven layers, and the transport layer (Layer 4) is responsible for end-to-end communication and flow control. NLB specifically focuses on routing and load balancing at the transport layer, making decisions based on IP protocol data.

Use NLB when:

1. TCP/UDP Load Balancing: NLB is designed for routing and load balancing TCP and UDP traffic, making it suitable for a wide range of applications, including those that don’t rely on HTTP.

2. Extreme Performance and Low Latency: NLB provides high-performance and low-latency load balancing, making it suitable for scenarios where fast and efficient handling of network traffic is critical.

3. Static IP Addresses: NLB offers static IP addresses, which can be important in scenarios where clients need to connect to a stable IP address.

4. Handling Millions of Requests Per Second: NLB is designed to handle millions of requests per second, making it suitable for high-throughput applications.

5. Support for Elastic Network Interfaces (ENIs): NLB supports assigning Elastic Network Interfaces to the load balancer nodes, providing a more scalable and flexible network architecture.

6. Direct Server Return (DSR) Mode: NLB supports Direct Server Return (DSR) mode, where the load balancer forwards packets to the backend servers, and the servers respond directly to the clients. This can reduce the load on the load balancer for certain use cases.

In summary, NLB is suitable for scenarios where low-level transport-layer routing and high-performance load balancing are required, making it a good choice for a variety of network-intensive applications.

When to use Gateway Load Balancer(GWLB):
AWS Gateway Load Balancer (GWLB) is designed for scenarios where you need to route traffic between different virtual appliances or network functions in your network architecture.

Use GWLB when:

Advanced Networking Architectures: GWLB is designed for complex networking architectures where you need to route traffic through a set of virtual appliances or network functions, such as firewalls, intrusion detection systems, or WAN accelerators.
Network Function Virtualization (NFV): If you are implementing Network Function Virtualization, where specific network functions are virtualized and run as software, GWLB can play a crucial role in efficiently directing traffic through these virtualized functions.
Hub-and-Spoke Architectures: GWLB is well-suited for hub-and-spoke network architectures where traffic needs to traverse specific paths between different segments of your network.
Load Balancing for Virtual Appliances: When you have multiple virtual appliances (e.g., firewalls) and you want to distribute traffic among them for load balancing and high availability, GWLB can be a suitable choice.
Support for IP Protocol and Port Ranges: GWLB provides support for routing traffic based on IP protocol and port ranges, offering flexibility in handling various types of network traffic.
Integration with AWS Services: If your networking architecture involves integrating with other AWS services, such as Amazon VPC, AWS Transit Gateway, or AWS Direct Connect, GWLB is designed to work seamlessly within the AWS ecosystem.
To choose between AWS Application Load Balancer (ALB), Network Load Balancer (NLB), and Gateway Load Balancer (GWLB), consider the following use cases:

1. Use AWS ALB When:
— Layer 7 (Application Layer) Routing: ALB is ideal for applications that require content-based routing, such as routing based on URL paths or headers.
— WebSockets and HTTP/2 Support: ALB supports WebSocket communication and HTTP/2, making it suitable for modern web applications.
— Containerized Applications: ALB is well-suited for containerized environments, offering features like host-based and path-based routing for containers.

2. Use AWS NLB When:
— Layer 4 (Transport Layer) Load Balancing: NLB is designed for TCP and UDP load balancing, making it suitable for various non-HTTP applications.
— High Performance and Low Latency: NLB provides high performance and low-latency load balancing, making it suitable for applications that demand extreme performance.
— Static IP Addresses: NLB offers static IP addresses, which can be essential when clients need to connect to stable IP addresses.

An additional advantage of NLB is Sticky sessions, in AWS Network Load Balancer (NLB) enables directing a client’s requests to the same target for the duration of the session, maintaining session persistence. Example: Imagine an e-commerce website where a user adds items to their shopping cart. With sticky sessions, if the user’s first request goes to Server A, all their subsequent requests within the same shopping session (adding more items, viewing the cart, etc.) will also be sent to Server A. This ensures a seamless and persistent experience for the user throughout their session by maintaining the connection to the same server.

3. Use AWS GWLB When:
— Routing Between Virtual Appliances: GWLB is designed for routing traffic between virtual appliances or network functions, such as firewalls or WAN accelerators, VPN.
— Advanced Networking Architectures: If your architecture involves complex hub-and-spoke configurations or Network Function Virtualization (NFV), GWLB can efficiently direct traffic through these segments.
— Support for IP Protocol and Port Ranges: GWLB provides flexibility in routing traffic based on IP protocol and port ranges.


