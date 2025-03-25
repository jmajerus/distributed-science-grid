## Distributed Science Grid — MVP Task Queue Scaffold

This scaffold sets up a basic local task orchestrator using **Redis + RQ + rq-dashboard**, designed for scientific workloads that run shell commands or Python scripts across nodes on a LAN.

> 🚀 Built to grow into the Distributed Science Grid vision — starting small, staying useful.

---

### 🔄 Components

#### 1. **Redis**
In-memory data store used to manage the task queue.

#### 2. **RQ (Redis Queue)**
Lightweight Python task queue system for background jobs.

#### 3. **rq-dashboard**
A simple web UI to monitor job status, logs, and results.

#### 4. **Task layer**
Python wrapper (`run_shell_task`) that executes command-line jobs and returns:
- Exit code
- stdout / stderr
- Start and end timestamps
- Runtime duration

---

### 📚 Quickstart

#### 1. Install dependencies
```bash
pip install rq rq-dashboard redis
```

#### 2. Start Redis server (local machine)
```bash
redis-server
```

#### 3. Start a worker
```bash
rq worker
```

#### 4. Enqueue a task
```bash
python enqueue.py
```

#### 5. Start dashboard (optional)
```bash
rq-dashboard
```

Then open your browser to: [http://localhost:9181](http://localhost:9181)

---

### 🎡 File Layout

```bash
repo/
├── tasks.py            # Shell-executing task wrapper
├── enqueue.py          # Example job submission
├── requirements.txt    # Dependencies (for pip install -r)
├── task_descriptors/   # JSON task files (future feature)
└── README.md
```

---

### 🚀 Example Task

```python
# enqueue.py
from tasks import queue, run_shell_task

job = queue.enqueue(run_shell_task, "python3 simulate.py --steps 1000")
print(f"Enqueued job: {job.id}")
```

---

### 📈 What This Enables

- A **clickable local demo** for science orchestration
- A baseline for **job management** and **status monitoring**
- A path to build more advanced logic: task descriptors, resource matching, federated scheduling, etc.

---

### 🔧 Next Steps (Ideas)

- Add GPU/CPU capability checks for each node
- Use task descriptors (JSON files) to populate job metadata
- Auto-assign nodes via basic heartbeat + inventory
- Build a custom dashboard later if rq-dashboard feels limiting

---

Let this serve as your **launchpad** — no Kubernetes, no cloud, just a LAN, some science, and a purpose.

