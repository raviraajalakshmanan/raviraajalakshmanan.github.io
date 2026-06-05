---
layout: page
title: Papers
description: Papers worth reading in distributed systems, systems design, and beyond.
permalink: /papers
---

Papers that come up repeatedly as foundational, widely cited, or worth the time — collected here as a reference.

---

## Audio Notes

AI-generated system design deep-dives from my study notes in Tamil.

[Listen on Spotify](https://open.spotify.com/show/2Ld88Vh1MYYi297garBH0S?si=fbf701da91654264)

---

## Systems

**Causality and ordering**

- **★ [Time, Clocks, and the Ordering of Events in a Distributed System](https://lamport.azurewebsites.net/pubs/time-clocks.pdf)** (1978) — Lamport. Introduces the happens-before relation and logical clocks for reasoning about event ordering across processes without a shared global clock.

**Fault tolerance**

- **[The Byzantine Generals Problem](https://lamport.azurewebsites.net/pubs/byz.pdf)** (1982) — Lamport, Shostak & Pease. Defines the problem of reaching distributed agreement when some nodes may behave arbitrarily or maliciously. The conceptual foundation for Byzantine fault-tolerant systems.

**Consensus**

- **[In Search of an Understandable Consensus Algorithm (Raft)](https://raft.github.io/raft.pdf)** (2014) — Ongaro & Ousterhout. Presents Raft, a consensus algorithm designed for understandability, managing replicated logs and equivalent in result to Multi-Paxos. Widely recommended as the entry point before Paxos.

- **★ [Paxos Made Simple](https://lamport.azurewebsites.net/pubs/paxos-simple.pdf)** (2001) — Lamport. Lamport's own simplified description of the Paxos consensus algorithm, which underlies much of production distributed systems thinking.

- **★ [Impossibility of Distributed Consensus with One Faulty Process](https://groups.csail.mit.edu/tds/papers/Lynch/jacm85.pdf)** (1985) — Fischer, Lynch & Paterson. Proves that no deterministic algorithm can solve consensus in a fully asynchronous system with even one faulty process — the FLP impossibility result.

**CAP and consistency models**

- **[CAP Twelve Years Later: How the "Rules" Have Changed](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed/)** (2012) — Brewer. Brewer revisits the CAP conjecture, clarifying common misinterpretations and examining how practitioners should reason about consistency and availability tradeoffs.

- **★ [Brewer's Conjecture and the Feasibility of Consistent, Available, Partition-Tolerant Web Services](https://users.ece.cmu.edu/~adrian/731-sp04/readings/GL-cap.pdf)** (2002) — Gilbert & Lynch. The formal proof of the CAP theorem: a distributed system cannot simultaneously guarantee consistency, availability, and partition tolerance.

- **[A Critique of the CAP Theorem](https://arxiv.org/abs/1509.05393)** (2015) — Kleppmann. Argues that CAP's definitions are too narrow for practical use, and proposes a more precise framework for reasoning about consistency models and failure modes.

---

### Storage systems that shaped the industry

- **★ [The Google File System](https://research.google/pubs/pub51/)** (2003) — Ghemawat, Gobioff & Leung. Describes a distributed file system built on commodity hardware that treats failure as normal rather than exceptional. Influenced HDFS and much of what followed.

- **★ [Bigtable: A Distributed Storage System for Structured Data](https://research.google/pubs/pub27898/)** (2006) — Chang et al. Presents Google's sparse, distributed, multi-dimensional sorted map — the model behind many wide-column databases. Builds on GFS and Chubby.

- **★ [Dynamo: Amazon's Highly Available Key-value Store](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf)** (2007) — DeCandia et al. Describes Amazon's eventually consistent key-value store, covering consistent hashing, quorum-based reads/writes, versioning, and application-assisted conflict resolution.

- **[The Log-Structured Merge-Tree](https://www.cs.umb.edu/~poneil/lsmtree.pdf)** (1996) — O'Neil et al. Introduces the LSM-tree storage structure underlying Cassandra, RocksDB, LevelDB, HBase, and most modern write-heavy databases.

- **★ [Spanner: Google's Globally-Distributed Database](https://research.google/pubs/pub39966/)** (2012) — Corbett et al. Describes a globally distributed database notable for TrueTime — GPS and atomic clock-based timestamps used to achieve external consistency across datacenters.

---

### Computation and data processing

- **★ [MapReduce: Simplified Data Processing on Large Clusters](https://research.google/pubs/pub62/)** (2004) — Dean & Ghemawat. Presents a programming model for large-scale batch processing that hides fault tolerance, scheduling, and data distribution behind a map-and-reduce abstraction.

- **[Kafka: A Distributed Messaging System for Log Processing](https://notes.stephenholiday.com/Kafka.pdf)** (2011) — Kreps, Narkhede & Rao. Describes a persistent, replicated commit log optimized for high-throughput data ingestion and replay, treating the log as a first-class system primitive.

- **[Resilient Distributed Datasets](https://www.usenix.org/system/files/conference/nsdi12/nsdi12-final138.pdf)** (2012) — Zaharia et al. Introduces RDDs, a fault-tolerant in-memory abstraction for distributed computation that recovers from failures using lineage rather than checkpointing.

- **[The Dataflow Model](https://research.google/pubs/pub43864/)** (2015) — Akidau et al. Presents a unified model for batch and streaming computation, introducing event time, watermarks, windows, and triggers for processing out-of-order data at scale.

---

### Coordination, scheduling, and control planes

- **★ [The Chubby Lock Service for Loosely-Coupled Distributed Systems](https://research.google/pubs/pub27897/)** (2006) — Burrows. Describes a distributed lock service for coarse-grained locking, leader election, and reliable small-metadata storage. The design pattern behind ZooKeeper, etcd, and Consul.

- **[ZooKeeper: Wait-free Coordination for Internet-scale Systems](https://www.usenix.org/legacy/event/atc10/tech/full_papers/Hunt.pdf)** (2010) — Hunt et al. Presents a coordination service providing primitives for leader election, configuration management, and group membership through a hierarchical namespace.

- **★ [Large-scale Cluster Management at Google with Borg](https://research.google/pubs/pub43438/)** (2015) — Verma et al. Describes Google's cluster manager, covering job scheduling, resource isolation, failure handling, and the operational experience of running large fleets of machines.

- **[Borg, Omega, and Kubernetes](https://research.google/pubs/pub44843/)** (2016) — Burns et al. Retrospective on three generations of Google container management, examining the design decisions and lessons learned across a decade of production systems.

---

### Transactions and distributed databases

- **[Calvin: Fast Distributed Transactions for Partitioned Database Systems](https://cs.yale.edu/homes/thomson/publications/calvin-sigmod12.pdf)** (2012) — Thomson et al. Proposes a protocol that avoids distributed coordination at commit time by globally ordering transactions before execution, enabling ACID guarantees without two-phase commit overhead.

- **[Highly Available Transactions: Virtues and Limitations](https://arxiv.org/abs/1302.0309)** (2014) — Bailis et al. Formally characterizes which transactional isolation and consistency guarantees can be achieved without coordination across nodes and which cannot.

- **[COPS: Scalable Causal Consistency for Wide-Area Storage](https://www.cs.cmu.edu/~dga/papers/cops-sosp2011.pdf)** (2011) — Lloyd et al. Presents a causally consistent wide-area storage system, offering stronger guarantees than eventual consistency without the latency cost of strong consistency.

---

### Latency, reliability, and operability

- **★ [The Tail at Scale](https://research.google/pubs/pub40801/)** (2013) — Dean & Barroso. Examines how high-percentile latency in large distributed systems dominates end-to-end response times, and introduces techniques like hedged requests and micro-partitions to reduce latency variability.

- **★ [Dapper: A Large-Scale Distributed Systems Tracing Infrastructure](https://research.google/pubs/pub36356/)** (2010) — Sigelman et al. Describes Google's distributed tracing system, which tracks requests across services to provide visibility into latency and failures in large-scale deployments.

- **[Google SRE Book](https://sre.google/sre-book/table-of-contents/) · [SRE Workbook](https://sre.google/workbook/table-of-contents/)** — Google's documentation on site reliability engineering: error budgets, SLIs, SLOs, incident management, and operational patterns for large-scale services.

---

### Caching, load, and social-scale systems

- **[Consistent Hashing and Random Trees](https://www.cs.princeton.edu/courses/archive/fall09/cos518/papers/chash.pdf)** (1997) — Karger et al. Introduces consistent hashing, a technique for distributing keys across nodes such that only a small fraction of keys need remapping when nodes are added or removed.

- **[Scaling Memcache at Facebook](https://www.usenix.org/system/files/conference/nsdi13/nsdi13-final170_update.pdf)** (2013) — Nishtala et al. Describes the architecture of Facebook's Memcached deployment at scale, covering hot-key handling, cache invalidation, regional replication, and consistency tradeoffs.

- **[TAO: Facebook's Distributed Data Store for the Social Graph](https://www.usenix.org/system/files/conference/atc13/atc13-bronson.pdf)** (2013) — Bronson et al. Presents a distributed data store optimized for read-heavy social graph workloads, with a tiered cache hierarchy and geographically distributed architecture.

---

## Machine Learning

- **[Attention Is All You Need](https://arxiv.org/abs/1706.03762)** (2017) — Vaswani et al. Introduces the Transformer architecture, replacing recurrence with self-attention for sequence modeling tasks.
- **[Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361)** (2020) — Kaplan et al. Establishes empirical scaling laws relating model performance to compute, data, and parameter count.

## Programming Languages & Verification

- **[Out of the Tar Pit](https://curtclifton.net/papers/MoseleyMarks06a.pdf)** (2006) — Moseley & Marks. Argues that accidental complexity — particularly mutable state — is the primary source of difficulty in large software systems.
