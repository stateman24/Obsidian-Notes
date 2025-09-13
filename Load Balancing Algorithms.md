#DistributedSystems #SoftwareDevelopment 
Algorithms for load balancing are strategies for effectively allocating workloads among several servers or resources. 
Load balancing algorithms can be broadly categorized into two types: 
1. ***Dynamic load balancing**  
2. ***Static load balancing.***
## Static Load Balancing Algorithms

Static load balancing involves predetermined assignment of tasks or resources without considering real-time variations in the system. This approach relies on a fixed allocation of workloads to servers or resources, and it doesn’t adapt to changes during runtime.
### Types of Static Load Balancing Algorithms
#### 1. Round Robin Load Balancing Algorithm
The Round Robin algorithm is a simple static load balancing approach in which requests are distributed across the servers in a sequential or rotational manner. It is easy to implement but it doesn’t consider the load already on a server so there is a risk that one of the servers receives a lot of requests and becomes overloaded.
##### When to use Round Robin Load Balancing Algorithm
- Ideal for applications where all servers have similar capacity and performance.
- Works well for evenly distributed workloads, such as basic web requests.
- Best suited for simple environments without complex resource needs.
- Useful in setups where request order matters less than balanced distribution across servers.
#### 2. Weighted Round Robin Load Balancing Algorithm
The Weighted Round Robin algorithm is also a static load balancing approach which is much similar to the round-robin technique. The only difference is, that each of the resources in a list is provided a weighted score. Depending on the weighted score the request is distributed to these servers. 
- Servers with higher weights are given a larger proportion of the requests.
- The distribution is cyclic, similar to the round-robin technique, but with each server receiving a number of requests proportional to its weight.
- If a server reaches its processing capacity, it may start rejecting or queuing additional requests, depending on the server's specific behavior.
##### When to use Weighted Round Robin Load Balancing Algorithm?
- When servers have different capacities or performance levels.
- Ideal for environments where servers vary in resources (CPU, memory, etc.).
- Useful when you want to maximize resource utilization across all servers.
- Helps in preventing smaller servers from overloading while efficiently using larger servers.
#### 3. Source IP Hash Load Balancing Algorithm

The Source IP Hash Load Balancing Algorithm is a method used in network load balancing to distribute incoming requests among a set of servers based on the hash value of the source IP address. This algorithm aims to ensure that requests originating from the same source IP address are consistently directed to the same server.
If the load balancer is configured for session persistence, it ensures that subsequent requests from the same source IP address are consistently directed to the same server. This is beneficial for applications that require maintaining session information or state.
##### When to use Source IP Hash Load Balancing Algorithm?
- Ideal for applications needing session consistency, like online banking, where the same user must connect to the same server throughout a session.
- Useful when users from specific regions should connect to dedicated servers for better performance or compliance.
- Effective when a few IPs generate most of the traffic, ensuring balanced load distribution without random switching.
## Dynamic Load Balancing Algorithms
Dynamic load balancing involves making real-time decisions about how to distribute incoming network traffic or computational workload across multiple servers or resources. This approach adapts to the changing conditions of the system, such as variations in server load, network traffic, or resource availability.
### Types of Dynamic Load Balancing Algorithms
#### 1. Least Connection Method Load Balancing Algorithm
The Least Connections algorithm is a dynamic load balancing approach that assigns new requests to the server with the fewest active connections. The idea is to distribute incoming workloads in a way that minimizes the current load on each server, aiming for a balanced distribution of connections across all available resources. 
- To do this load balancer needs to do some additional computing to identify the server with the least number of connections. 
- This may be a little bit costlier compared to the round-robin method but the evaluation is based on the current load on the server.
##### When to use Least Connection Load Balancing Algorithm?
- Ideal for applications where some requests take longer to process than others (e.g., video streaming or large file uploads).
- Useful when some connections stay active longer, as it ensures new requests go to servers with fewer active connections.
- Great for systems with fluctuating traffic, as it balances based on real-time server load rather than just counting requests.

#### 2. Least Response Time Method Load Balancing Algorithm
The Least Response method is a dynamic load balancing approach that aims to minimize response times by directing new requests to the server with the quickest response time. 
- It considers the historical performance of servers to make decisions about where to route incoming requests, optimizing for faster processing.
- The dynamic aspect comes from the continuous monitoring of server response times and the adaptive nature of the algorithm to route incoming requests to the server with the historically lowest response time.
##### When to use Least Response Time Load Balancing Algorithm?
- Ideal for applications with heavy, fluctuating user traffic where response time matters.
- Great for apps like e-commerce sites or streaming services, where a quick response improves user experience.
- Works well when servers have different load levels, as it directs traffic to the server that’s both available and responds the fastest.
#### 3. Resource-based Load Balancing Algorithm
The Resource-Based Load Balancing algorithm distributes incoming requests based on the current resource availability of each server, such as CPU usage, memory, or network bandwidth. Rather than just routing traffic equally or based on past performance, this algorithm evaluates the current "resource health" of each server to decide where new requests should go.
##### **When to Use Resource-Based Load Balancing Algorithm?**
- Useful for applications that perform CPU-intensive or memory-heavy tasks.
- Works well when servers have different resource levels, as the algorithm adapts to each server’s real-time capacity.
- Ensures availability by routing requests to the least overloaded servers, reducing downtime risks.

[[Change Data Capture (CDC) Pipeline]]