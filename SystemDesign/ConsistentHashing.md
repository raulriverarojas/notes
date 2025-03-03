# Consistent Hashing

Consistent Hashing is a distributed hashing technique used for load balancing and minimizing the need for rehashing upon addition or deletion of nodes.

- Useful for distributed storage systems
- The method of evenly allocating keys among a group of nodes in computer systems
- Reduces the amount of keys that must be relocated when adding or removing nodes
- Minimizes the impact on the system as a whole during node changes
- Represents a virtual ring structure known as a "hash ring"

## Main Goal of Technique
Reduce the number of remapping operations necessary when adding or removing nodes from the network.
