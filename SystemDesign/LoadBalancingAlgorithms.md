# Load Balancing Techniques

There are two forms of load balancing:

## Static Load Balancing
Predetermined number of tasks or resources that does not react to system state.

## Dynamic Load Balancing
Making real-time decisions to distribute network traffic or computational workload across multiple servers or resources.

## Static Algorithms

### Round Robin
- Requests are distributed to the resources in a sequential or rotational manner
- Easy to implement
- Could still lead to a server being overwhelmed

**When to use:**
- For apps where all servers or resources have similar performance and capacity
- When request order matters less than balanced distribution across servers
- In evenly distributed workloads such as simple web requests
- Simple environments with no complex resource requirements

### Weighted Round Robin
- Same as round robin but each resource or server has a weight associated with it
- Requests are routed based on available resource weights
- Resources with larger weights are given larger portion of requests
- Distribution is still cyclic

**When to use:**
- When resources have different capacities
- When you want to optimize resource utilization across all resources
- Helps in preventing smaller servers from being overloaded

### Source IP Hash Algorithm
- Networking load balancing technique that uses the source IP address to distribute requests
- Ensures that requests from the same source are routed to the same resource

**When to use:**
- When application needs session consistency
- Useful for routing users from specific regions to certain resources for performance or compliance

## Dynamic Algorithms

### Least Connection Algorithm
- Dynamic load balancing that assigns requests to a resource with least active connections

**When to use:**
- Ideal for applications with varying workload length
- Useful for applications where connection length can vary
- Ideal for applications with fluctuating traffic

### Least Response Time Algorithm
- Dynamic load balancing approach routes requests to resources with lowest response time
- Response time is calculated based on historical data
- Historical data for decision making is updated in real-time

**When to use:**
- Ideal for applications with heavy fluctuating user traffic where response time matters
- Useful for applications where resources have different capacities
- Useful for e-commerce and streaming sites

### Resource Availability Algorithm
- Distributes incoming requests based on resource availability of each server (CPU, memory, network bandwidth)
- Uses current server metrics to route requests

**When to use:**
- Useful for CPU-intensive and memory-intensive workloads
