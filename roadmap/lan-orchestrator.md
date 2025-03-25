# Roadmap: LAN-Orchestrated Prototype

## 🎯 Goal

Build a lightweight orchestration framework that can be deployed on a local network of computers (e.g., in a home, lab, or classroom) to distribute scientific workloads intelligently across available CPU and GPU resources.

---

## 🧱 Phase 1: LAN-First MVP

**Key Features:**
- Node discovery and registration
- Capability reporting (CPU, GPU, RAM, disk)
- Job submission interface (simple CLI or web UI)
- Task queueing and assignment
- Status dashboard (active, failed, completed)
- Support for simple tasks (e.g., media transcoding, numeric simulations, AI training jobs)

**Technology Considerations:**
- Python or Node.js for rapid prototyping
- Lightweight networking (e.g., ZeroMQ, WebSocket, REST API)
- JSON or YAML for job description formats
- Optional container support (Dockerized tasks)

---

## 📈 Future Enhancements

- Remote/Federated mode (multi-LAN or cloud bridge)
- Public opt-in node registry with opt-in permissions
- Support for task chaining (pipeline-style workflows)
- Adaptive scheduling based on node availability and priority
- Task verification/redundancy for trust models

---

## 🤝 Collaboration Opportunities

Looking for contributors with experience in:
- Distributed systems
- Container orchestration
- Frontend dashboards
- Open science and research workflows
- Ethical infrastructure design

We encourage sharing ideas, proof-of-concepts, or even just thoughtful criticism.
