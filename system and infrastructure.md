### **5. System and Infrastructure**

This group addresses limitations and considerations in server infrastructure, memory, CPU utilization, connections, and disk I/O.

---

#### **Key Topics and Answers**

---

#### **5.1 Server Memory and CPU Utilization**
- **How much memory can a single process use?**
  - Depends on the operating system:
    - **32-bit systems**: ~4GB (limited by addressable memory space).
    - **64-bit systems**: Practically unlimited, constrained by physical RAM and OS limits.
  - Example: Node.js by default limits memory to **1.4GB** for 32-bit and **2GB** for 64-bit systems (configurable with the `--max-old-space-size` flag).

- **How can high CPU utilization impact performance?**
  - High CPU usage can:
    - Slow down request handling.
    - Cause timeouts or errors in high-traffic scenarios.
  - Mitigation: Use load balancing, caching, and asynchronous processing.

---

#### **5.2 Maximum Connections for Servers**
- **What are the connection limits for servers?**
  - **Apache**: Default is **150 concurrent connections**, configurable with `MaxRequestWorkers`.
  - **Nginx**: Default is **512 concurrent connections** per worker process.
  - **Node.js**: Limited by the system's maximum open file descriptors (`ulimit`).

- **How can connection limits be increased?**
  - Tune server configuration (`worker_processes` in Nginx, `MaxRequestWorkers` in Apache).
  - Use a reverse proxy or load balancer (e.g., HAProxy, AWS Elastic Load Balancer).

---

#### **5.3 Disk I/O and Read/Write Limits**
- **What are the limits for disk I/O operations?**
  - **SSD (Solid State Drive)**:
    - Read/write speed: ~500MB/s (SATA), ~3,500MB/s (NVMe).
    - IOPS: ~90,000-100,000.
  - **HDD (Hard Disk Drive)**:
    - Read/write speed: ~80-160MB/s.
    - IOPS: ~100-200.

- **How to optimize disk I/O?**
  - Use SSDs for databases and high-performance workloads.
  - Implement caching mechanisms (e.g., Redis, Memcached).
  - Optimize database queries to reduce disk reads/writes.

---

#### **5.4 Network Throughput and Latency**
- **What are the typical bandwidth limits for servers?**
  - Bandwidth depends on hosting provider and plan:
    - **AWS EC2**: Up to 25Gbps for certain instance types.
    - **Google Cloud**: Varies from 2Gbps to 32Gbps.
    - **Azure**: Up to 30Gbps for high-performance VM series.

- **How does latency affect performance?**
  - High latency causes slower data transfers and increased load times.
  - Mitigation: Use CDNs, reduce payload size, and minimize round trips.

---

#### **5.5 Virtual Machines and Containers**
- **What are the resource limits for VMs and containers?**
  - **Virtual Machines**:
    - Limited by the hypervisor (e.g., VMware, Hyper-V).
    - Memory and CPU allocation depend on physical resources.
  - **Docker Containers**:
    - By default, containers can use all host resources unless limits are set.
    - Use `--memory` and `--cpus` flags to limit resource usage.

---

#### **5.6 Power and Cooling Constraints**
- **How do power and cooling affect infrastructure?**
  - High-performance servers generate heat, requiring efficient cooling systems.
  - Downtime due to power failure can be mitigated with:
    - **UPS (Uninterruptible Power Supply)**.
    - **Generator backups**.

---

Would you like to delve deeper into a specific subtopic or move to the next group?