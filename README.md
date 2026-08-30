# David's Notes
- Kafka manifests as a cluster of servers, with each server referred to as a broker
- Data is generally stored in binary format but can leverage compression algorithms
- Avro is the most common data serialization format with Kafka
- Topics are generally replicated across 3 brokers; (generally 1 leader and the replicated ones being an in sync replica "ISR")
- Zookeeper manages brokers and performs in leader election for partitions (legacy software going away after 4.0; not as secure as KRaft)
- Stephane Maarek's course on Udemy is good. Focus on sections 1-4, 7, and 13.

# To figure out
- Kafka TTL information