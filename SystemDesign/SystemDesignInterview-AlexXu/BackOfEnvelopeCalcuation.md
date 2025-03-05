# Back of the Envelope Calculations & System Design Interviews

## 1. Back of the Envelope
Back of the envelope estimations are estimates you create using combination of thought experiments & common performance #s to get a good feel for which designs will meet your requirements.

To be able to effectively give a back of the envelope estimate you need to understand:
- Power of two
- Latency #s
- Capacity & availability #s

### Power of Two
- To get accurate calculations you need to know the data volume unit using the power of 2
- A byte is a sequence of 8 bits
- An ASCII char uses one byte of memory (8 bits)
- From this we can calculate common storage metrics in powers of 2 of a byte

### Power of 2 table
| Power of 2 | Value | Shortform |
|------------|-------|-----------|
| 10 | kilobyte | KB |
| 20 | megabyte | MB |
| 30 | gigabyte | GB |
| 40 | terabyte | TB |
| 50 | petabyte | PB |

### Latency numbers: length of computer operations
| Action | circa 2010 | Time |
|--------|------------|------|
| **Reads** | | |
| Read 1MB sequentially from disk | | 30ms |
| Read 1MB seq from network | | 10ms |
| Read 1MB seq from memory | | 250μs |
| Read random SSD | | 16μs |
| **Sends** | | |
| Send 2K bytes over 1Gbps network | | 20μs |
| Send packet Cali→Netherlands→Cali | | 150ms |
| Send 2K bytes over commodity network | | 44μs |
| **References** | | |
| Main memory reference | | 100ns |
| L2 cache reference | | 7ns |
| L1 cache reference | | 0.5ns |
| **Locks** | | |
| Mutex lock/unlock | | 100ns |

### Time Conversions
- 1ms = 1 millisecond = 10^-3s
- 1μs = 1 microsecond = 10^-6s
- 1ns = 1 nanosecond = 10^-9s

### Conclusions
- Compress data before sending over internet if possible
- Avoid disk & disk seeks

## Availability #s
- High availability is measured as a %
- SLA (service level agreement) is an agreement between service provider & a customer. Formally defines the level of uptime the service will deliver
- SLA uptime usually defined by nines, more nines the better

### Avail to downtime chart
| Avail % | Down/day | Down/year |
|---------|----------|-----------|
| 99% | 14.4 min | 3.65 days |
| 99.9 | 1.44 min | 8.77 hours |
| 99.99 | 8.64 seconds | 52.6 min |
| 99.999 | 864 milliseconds | 5.26 min |
| 99.9999 | 86.4 ms | 31.56s |

