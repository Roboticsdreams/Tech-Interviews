
# System Design

[Tech-Interviews](../../../README.md) -> [References](../../References.md) -> [Online Tutorials](../../Online%20Tutorials/OnlineTutorials.md) -> [System Design](/SystemDesign/SystemDesign.md)

1. For searching some text in millions of record: Use inverted index

2. For ACID property: use RDBMS.

3. For Unstructured data: use NoSQL

4. Database Scaling: Horizontal (Preferred for NoSQL) or Vertical Sharding(Preferred for RDBMS)

5. Read Heavy System: use Read through Cache 

6. Low Latency Requirement: CDN + Load Balancer + Cache

7. Write-Heavy System: Use ASYNC Processing (kafka message queues)

8. Handle Complex Data like Videos, Images, Files etc: Go for Object storage (ex: Amazon S3)

9. For High Availability, Performance, & Throughput: Use Load Balancer

10. Global Data Delivery: Use CDN.

11. For Fast DB Queries: Database Indexing

12. Load Management on a Component: Use Rate Limiter.

13. Avoid Single Point of Failure:  Set up Disaster Recovery Data Centre

14. Fault-Tolerance: Write though cache + Master Slave Architecture.

15. Peer to Peer communication: Use WebSockets.

16. For VideoCall : Use WebRTC

17. For Data Integrity between 2 system: Use Checksum Algorithm.

18. Efficient Managing of the Servers: Use Consistent Hashing.

19. High Availability and Consistency Trade-Off: Eventual Consistency.

20. Cache Eviction Policy: LRU cache (generally preferred, but there are more)



HLD Playlist: https://lnkd.in/d8eDwYVA

LLD Playlist: https://lnkd.in/dJkgzKxf

Java Playlist: https://lnkd.in/dUNA6vsU

SpringBoot Playlist: https://lnkd.in/gz2A5ih2