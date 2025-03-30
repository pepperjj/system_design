# 🧠 4-Week System Design Interview Study Plan (Free + Comprehensive)

## 👤 Who This Is For
- Intermediate-level senior software engineer
- No formal system design training
- Goal: Interview prep + master distributed systems & microservices
- Constraint: Prefer **free** and **open** resources

---

## 🗓️ Weekly Overview

| Week | Focus Area                          | Main Deliverable                   |
|------|-------------------------------------|-------------------------------------|
| 1    | Fundamentals & Approach             | Design a URL Shortener             |
| 2    | Distributed Systems + Microservices | Design a Rate Limiter              |
| 3    | Scalability & Fault Tolerance       | Design Twitter Feed or WhatsApp    |
| 4    | Mock Interviews & Mastery           | Design Dropbox or Uber Dispatch    |

---

## ✅ Week 1: System Design Fundamentals

### 🎯 Goals
- Learn core concepts and interview approach
- Understand latency, availability, scalability, caching, sharding

### 📚 Learn
- [System Design Primer](https://github.com/donnemartin/system-design-primer)  
  - “How to approach a system design interview”  
  - Load Balancer, Caching, Database, Sharding
- [karanpratapsingh/system-design](https://github.com/karanpratapsingh/system-design)  
  - Core concepts + YouTube visuals
- [ByteByteGo – YouTube](https://www.youtube.com/@ByteByteGo)

### 🧠 Practice
- **Design: URL Shortener**
  - Requirements, hashing, DB, redirect flow, scalability

### 🛠️ Deliverable
- Draw diagram using [Excalidraw](https://excalidraw.com/)
- Compare with [karanpratapsingh’s solution](https://github.com/karanpratapsingh/system-design#url-shortener)

---

## ✅ Week 2: Distributed Systems & Microservices

### 🎯 Goals
- Learn CAP theorem, replication, queues
- Understand microservices and communication

### 📚 Learn
- [karanpratapsingh/system-design](https://github.com/karanpratapsingh/system-design)
- [DDIA Notes](https://github.com/Yang-Yanxiang/Data-Intensive-Application-Notes)
- [Microservices.io](https://microservices.io/patterns/index.html)
- [ashishps1/awesome-system-design-resources](https://github.com/ashishps1/awesome-system-design-resources)

### 🧠 Practice
- **Design: Rate Limiter**
  - Token bucket, Redis TTL, distributed quota

### 🛠️ Deliverable
- Diagram on Excalidraw
- (Optional) Code in Go/Python
- Compare with [karanpratapsingh’s Rate Limiter](https://github.com/karanpratapsingh/system-design#rate-limiter)

---

## ✅ Week 3: Scaling & Fault Tolerance

### 🎯 Goals
- Handle real-world scale
- Learn retries, durability, eventual consistency

### 📚 Learn
- [ByteByteGo - YouTube](https://www.youtube.com/@ByteByteGo)
  - Twitter Feed, WhatsApp system
- [karanpratapsingh - WhatsApp Design](https://github.com/karanpratapsingh/system-design#whatsapp)
- [Uber Engineering Blog](https://eng.uber.com/)
- [ashishps1 curated list](https://github.com/ashishps1/awesome-system-design-resources)

### 🧠 Practice
- **Choose 1**:
  - Twitter Feed (fanout)
  - WhatsApp (delivery + sync)

### 🛠️ Deliverable
- Full diagram + flow explanation
- Optional: Simulate Kafka-based pub/sub

---

## ✅ Week 4: Mock Interview + Mastery

### 🎯 Goals
- Practice mock interviews
- Apply learned patterns

### 📚 Learn
- [System Design Cheatsheet](https://gist.github.com/vasanthk/485d1c25737e8e72759f)
- [SystemDesign.one](https://systemdesign.one/)

### 🧠 Practice
- **Mock Designs**:
  - Dropbox (file sync, metadata)
  - Uber Dispatch (matching, location)

### 🛠️ Deliverable
- 45-minute mock session
- Use Excalidraw
- Review trade-offs + reflect

---

## 🧰 Tools & Links Summary

| Tool/Repo                                      | Purpose                                 |
|-----------------------------------------------|------------------------------------------|
| [System Design Primer](https://github.com/donnemartin/system-design-primer) | Core knowledge + practice                |
| [karanpratapsingh/system-design](https://github.com/karanpratapsingh/system-design) | Walkthroughs + diagrams                  |
| [ByteByteGo](https://www.youtube.com/@ByteByteGo) | Visual explainers                        |
| [ashishps1 curated](https://github.com/ashishps1/awesome-system-design-resources) | Deep dives + reference                   |
| [SystemDesign.one](https://systemdesign.one/) | Practice + mock interviews               |
| [Excalidraw](https://excalidraw.com/)         | Diagramming tool                         |