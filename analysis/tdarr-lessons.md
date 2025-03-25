## Lessons and Design Inspiration from Tdarr

This document captures practical insights from the architecture and user experience of [Tdarr](https://github.com/HaveAGitGat/Tdarr), an open-source, LAN-based media processing orchestrator. Although Tdarr was designed for video encoding, its structure and deployment model offer useful parallels for the Distributed Science Grid (DSG).

---

### 📂 Core Design Concepts to Borrow

#### 1. **LAN-Centric Node Orchestration**
- Central server with multiple worker nodes
- Workers register themselves and report capabilities
- Tasks assigned based on resource awareness (CPU, GPU)

✅ *DSG takeaway:* Adopt this model for local science clusters

#### 2. **Capability-Aware Scheduling**
- Nodes can be tagged or auto-identified as GPU-capable
- Server sends tasks only to suitable nodes

✅ *DSG takeaway:* Include hardware capability metadata (RAM, cores, GPU presence) in early node registration

#### 3. **Real-Time Web Dashboard**
- Displays node status, task queues, active jobs
- Central control point for visibility and basic management

✅ *DSG takeaway:* Prioritize even a minimal dashboard in the MVP

#### 4. **Pull-Based Task Distribution**
- Nodes poll or request work when available
- Avoids need for central push system with error-prone timing

✅ *DSG takeaway:* Keep this approach in MVP for simplicity and reliability

#### 5. **Task Chunking and Parallelism**
- Long jobs (e.g. video) can be split into smaller jobs and recombined later

✅ *DSG takeaway:* Plan for splitting large simulations, ML workloads, or data processing jobs into atomic chunks

#### 6. **Retry and Fault Tolerance**
- Retries on failure, with optional user intervention

✅ *DSG takeaway:* MVP can start with basic retry logic and manual dashboard overrides

---

### 🧪 Plugin/Template Architecture (Future Consideration)
- Tdarr uses plugins to define pipelines (e.g., filter, encode, clean)
- Users can customize task behavior with plugin stacks

⚠️ *DSG takeaway:* Consider a modular template/task system in later versions for chaining scientific tasks or simulation stages

---

### 🏆 Lightweight Deployment Model
- Tdarr runs on minimal hardware
- No Kubernetes or container orchestration required

✅ *DSG takeaway:* Aligns perfectly with DSG’s LAN-first, classroom/lab-deployable goals

---

### 🧰 Potential Code Reuse

The original **Tdarr v1** was open source under the [GPL-3.0 license](https://github.com/HaveAGitGat/Tdarr/blob/v1/LICENSE), meaning:
- You **may reuse code** in a compatible project
- You must **attribute the original authors**
- You must **keep derivative works under GPL-3.0**

Possible areas to investigate:
- Node registration and heartbeat logic (Node.js-based)
- Web dashboard layout and task display code
- CPU/GPU detection routines on worker agents

However, since Tdarr was rewritten and the newer versions are no longer open source, the v1 codebase is **archived** and not maintained. For practical purposes, it may be best to treat the codebase as architectural reference only.

---

### 🔍 Further Research

Archived open-source version:
- GitHub: [https://github.com/HaveAGitGat/Tdarr/tree/v1](https://github.com/HaveAGitGat/Tdarr/tree/v1)

Topics worth mining:
- Node <-> server communication protocol
- Plugin execution sandboxing
- Basic dashboard logic and layout

---

This document will continue to evolve as implementation begins. Future comparisons may also draw from other orchestration models and task queue systems (e.g., Celery, Nomad, Ray).

