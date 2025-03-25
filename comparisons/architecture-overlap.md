## Architecture Comparison: Distributed Science Grid and Existing Systems

This document outlines areas of **overlap, inspiration, and divergence** between the Distributed Science Grid (DSG) and three major categories of existing systems:

- [BOINC](https://boinc.berkeley.edu/) (volunteer scientific computing)
- [Kubernetes](https://kubernetes.io/) and related orchestration frameworks
- [Tdarr](https://github.com/HaveAGitGat/Tdarr) (LAN-based distributed media encoding)

We aim to learn from each of these systems while proposing a model tailored to **LAN-first, science-focused, resource-aware orchestration.**

---

### 📁 Overlap with BOINC

| Capability                  | BOINC                          | Distributed Science Grid (Proposed) |
|----------------------------|--------------------------------|-------------------------------------|
| Distributed task execution | ✅ Yes                         | ✅ Yes                              |
| Volunteer compute model    | ✅ Yes                         | ✅ Yes (opt-in or federated)       |
| Idle-time utilization      | ✅ Yes                         | ✅ Yes                              |
| Public science support     | ✅ Yes                         | ✅ Yes                              |
| Remote monitoring (GUI)    | ✅ Partial                     | ✅ Full dashboard planned          |
| Local network visibility   | ✅ Manual, via config          | ✅ Automatic node discovery        |
| Task pull model            | ✅ Yes                         | ❌ Push or hybrid model            |
| Node awareness             | ❌ No                          | ✅ Yes (resource-aware)            |
| Scheduling tasks by node   | ❌ No                          | ✅ Yes (orchestrated)              |
| Multi-stage pipelines      | ❌ No                          | ✅ Yes (planned support)           |
| Workflow graphing          | ❌ No                          | ✅ Eventual DAG/pipeline support   |
| LAN-first architecture     | ❌ No                          | ✅ Core design goal                |

---

### 🥐 Overlap with Kubernetes (and K3s)

> Kubernetes is a general-purpose orchestration platform used to manage containerized workloads at scale. DSG borrows concepts from Kubernetes while reducing complexity and tailoring functionality to scientific workflows and volunteer compute contexts.

| Capability                        | Kubernetes                   | Distributed Science Grid (Proposed) |
|----------------------------------|------------------------------|-------------------------------------|
| Task scheduling                  | ✅ Yes                       | ✅ Yes                              |
| Node capability awareness        | ✅ Yes (via kubelet/node API)| ✅ Yes                              |
| Container-based workloads        | ✅ Strongly built-in         | ✅ Optional support planned         |
| Horizontal scaling               | ✅ Yes                       | ✅ Federated clusters (future)     |
| Multi-node awareness             | ✅ Yes                       | ✅ Yes                              |
| Health checks / task monitoring  | ✅ Yes                       | ✅ Planned (simplified)            |
| Failover / rescheduling          | ✅ Yes                       | ✅ Eventual feature                 |
| Declarative job descriptions     | ✅ YAML-based                | ✅ (Likely JSON/YAML)              |
| Local-first deployment           | ❌ No (typically cloud-first)| ✅ Yes (K3s overlaps here)           |
| General-purpose infra            | ✅ Yes (broad scope)         | ❌ Science-focused, simplified      |
| DevOps complexity                | ❌ High                      | ✅ Minimal-barrier design           |

#### ⚡ Note on K3s

[K3s](https://k3s.io/) is a lightweight Kubernetes distribution developed by Rancher Labs. It is more approachable for small clusters, edge computing, and local-first setups. DSG may draw further inspiration from K3s' simplified deployment and reduced overhead model, especially for science clusters running in labs, classrooms, or hobbyist environments.

---

### 🔄 Overlap with Tdarr

| Capability               | Tdarr                        | Distributed Science Grid (Proposed) |
|-------------------------|------------------------------|-------------------------------------|
| LAN-first orchestration | ✅ Yes                       | ✅ Yes                              |
| Node capability tracking| ✅ CPU/GPU type aware        | ✅ Similar approach                 |
| Distributed task queue  | ✅ Centralized server model  | ✅ Similar pattern                  |
| Home-friendly install   | ✅ Yes                       | ✅ Design goal                      |
| GUI/Dashboard           | ✅ Yes                       | ✅ Planned                          |
| Task monitoring         | ✅ Yes                       | ✅ Yes                              |
| Media-specific          | ✅ Video transcoding only    | ❌ Science workloads instead        |
| Extensibility/plugins   | ✅ (for encoding workflows)  | ✅ Eventually, for task types       |

---

### ✅ Summary of Overlaps

| Category            | BOINC       | Kubernetes/K3s  | Tdarr       |
|---------------------|-------------|------------------|-------------|
| Distributed tasks   | ✅          | ✅              | ✅          |
| Public-good mission | ✅          | ❌              | ❌          |
| Idle device use     | ✅          | ❌              | ✅          |
| GPU awareness       | ❌          | ✅              | ✅          |
| LAN support         | Manual      | ❌ (except K3s) | ✅          |
| Lightweight setup   | ✅          | ❌              | ✅          |
| Task orchestration  | ❌          | ✅              | ✅          |
| Multi-stage workflows| ❌         | ✅              | ❌          |
| Local-first design  | ❌          | ❌ (K3s ✅)     | ✅          |
| Science focus       | ✅          | ❌              | ❌          |

---

The Distributed Science Grid seeks to combine the **purpose-driven mission** of BOINC, the **intelligent orchestration** of Kubernetes, and the **user-friendly, LAN-first approach** of Tdarr to create a practical, extensible, and equitable platform for public-benefit research computing.

This is not a reinvention. It is a recombination — with purpose.

