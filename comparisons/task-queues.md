## Task Queue Libraries: Evaluation for MVP Orchestrator

This document reviews several open-source task queue systems that could serve as the core of a lightweight Distributed Science Grid (DSG) orchestrator. The focus is on suitability for local scientific workloads, LAN deployment, and flexibility in job formats (e.g., Python scripts, binaries, command-line tools).

---

### 🌐 Evaluation Criteria

- **Ease of setup**
- **LAN/local deployment friendliness**
- **Support for non-web jobs (CLI/science workloads)**
- **Retry/failure logic**
- **Monitoring or dashboard support**
- **Extensibility and community**

---

### 📊 Candidates

#### 1. **Celery**

- ✅ **Pros**:
  - Very mature and widely used
  - Supports retries, task chaining, and scheduling
  - Integrates with dashboards like Flower
  - Pluggable backend support (Redis, RabbitMQ, etc.)
- ❌ **Cons**:
  - Designed for Python-based web tasks; science/CLI use is clunky
  - Complex configuration
  - Hard to isolate failed or long-running CLI-based jobs

#### 2. **RQ (Redis Queue)**

- ✅ **Pros**:
  - Simple to set up (Redis + Python)
  - Task execution is transparent (Python functions)
  - Minimal boilerplate
  - Basic job monitoring with `rq-dashboard`
- ❌ **Cons**:
  - Poor multi-node orchestration logic out of the box
  - Not great for command-line jobs or parallel execution

#### 3. **Dramatiq**

- ✅ **Pros**:
  - Similar to RQ but more performant
  - Built-in retry and scheduling
  - Cleaner syntax than Celery
- ❌ **Cons**:
  - Still Python-focused
  - Less community support than Celery
  - No first-class support for CLI-based job wrapping

#### 4. **Huey**

- ✅ **Pros**:
  - Lightweight and beginner-friendly
  - Works with Redis or SQLite
  - Suitable for small, single-node deployments
- ❌ **Cons**:
  - Lacks multi-node coordination
  - Minimal dashboard support

#### 5. **Custom (Barebones Queue)**

- ✅ **Pros**:
  - Fully tailored to CLI science workloads
  - Easy to integrate with task metadata and node selection
  - No external dependencies (could be JSON+Flask or SQLite+API)
- ❌ **Cons**:
  - No advanced features (scheduling, chaining, dashboards)
  - Everything must be written manually (retries, logs, etc.)

---

### 🔄 Summary Comparison

| Feature            | Celery | RQ  | Dramatiq | Huey | Custom |
|--------------------|--------|-----|----------|------|--------|
| Easy to set up     | ❌     | ✅  | ✅       | ✅   | ✅     |
| LAN-friendly       | ❌     | ✅  | ✅       | ✅   | ✅     |
| CLI task support   | ❌     | ❌  | ❌       | ❌   | ✅     |
| Retry/failure logic| ✅     | ✅  | ✅       | ❌   | ✅*    |
| Built-in dashboard | ✅     | ✅  | ❌       | ❌   | ❌     |
| Multi-node aware   | ✅     | ❌  | ❌       | ❌   | ✅     |

> *Custom retry logic must be implemented by hand

---

### 🚀 Suggested MVP Direction

For MVP purposes, the best course may be to **build a custom lightweight task queue** that:

- Uses **JSON or SQLite** as a queue
- Supports **CLI-defined tasks**
- Includes basic metadata (node suitability, task status)
- Can evolve into a DAG-based or plugin-based system later

Alternatively, **RQ** could be prototyped with CLI job wrappers if Redis is acceptable and the need for dashboarding is minimal.

---

This document can be updated as prototypes are tested and more realistic science workloads are profiled.

