# Fleet Incident Investigation — README

## 📌 What Is This Project?

The Ati Motors Autonomous Mobile Robot (AMR) fleet experienced an operational issue on **June 30, 2026, between 10:00 AM and 11:00 AM**. We've been given 3 data sources (telemetry, trip records, and system logs) and asked to **investigate**:

- What happened?
- Which robot was most affected?
- Why did it happen (root cause)?

This is a **Data Analytics + Observability** internship assignment — meaning we analyze the data and produce a real-world style "incident report," similar to what a company writes up after a server outage (an RCA — Root Cause Analysis report).

---

## 📂 Data Provided

| File | What It Contains | What It Gives Us |
|---|---|---|
| `telemetry.csv` | Each robot's health data over time (battery, CPU, network latency, position) | **Metrics** — numeric readings tracked over time |
| `trips.csv` | Each robot's trip record (start, end, status) | **Traces** — lifecycle of a task |
| `events.log` | System-generated notable events (warnings, errors) | **Logs** — text-based event records |

Together these three form a classic "observability" data stack — which is why the assignment is called **Fleet Observability**.

---

## ✅ How to Complete the Project (Step-by-Step)

### Step 1 — Load & Explore the Data
Load all three files into Python with Pandas. First, just explore — how many robots, how many rows, any missing values.

### Step 2 — Merge the Data
Join telemetry + trips + events using `robot_id` and `timestamp`, so you get full context at each point in time — what a robot's health looked like and what event occurred at that moment.

### Step 3 — Build a Timeline
Sort everything chronologically to build a clear **timeline**. This becomes your story: "10:05:12 — Robot_01 starts trip → 10:05:55 — battery low warning → 10:06:10 — network latency spike → 10:06:20 — trip cancelled."

### Step 4 — Find Anomalies (At Least 5)
Look for anything abnormal in the data:
- Battery level suddenly increasing (without charging)
- A robot's position suddenly "jumping"
- CPU usage spiking to 95%+
- Duplicate log entries
- A trip that never completes or cancels (blank trip_end)

For each anomaly, explain: **what you found / why it's abnormal / what operational impact it could have.**

### Step 5 — Identify the Most Critical Robot
Compare all robots — which one had the most, or most severe, issues. Back this up with evidence, not just intuition.

### Step 6 — Determine Root Cause
Bucket your anomalies into:
- **Robot behavior** (battery, hardware)
- **System/software behavior** (bugs, duplicate logs, stuck trips)
- **Network conditions** (latency spikes)

Whichever category is most present and most correlated with the actual failure is your likely root cause. State your assumptions clearly.

### Step 7 — Find One Bonus Issue
Something not directly asked about but worth flagging — e.g., a trip that never got closed out, or a duplicated log line (a data-quality bug).

### Step 8 — Prepare Deliverables
1. **Jupyter Notebook** — all code + charts + explanations
2. **Summary PDF (max 3 pages)** — timeline, anomalies, root cause, assumptions, bonus finding
3. **5-minute screen recording** — explain your approach, assumptions, findings, and uncertainties (you'll need to record this yourself)

---

## 🛠️ Tools You'll Use
- **Python** (Pandas, NumPy, Matplotlib/Seaborn)
- **Jupyter Notebook**
- **PDF export tool** (Word, or generate directly from Python)
- **Screen recorder** (Loom, OBS, or your phone/laptop's built-in recorder)

---

## 🧠 Concepts Covered
- Data Cleaning (missing values, duplicates)
- Data Merging/Joining (SQL-style JOIN logic)
- Time-Series Analysis
- Anomaly Detection (threshold-based + logical-impossibility checks)
- Correlation Analysis
- Root Cause Analysis (RCA)
- Observability fundamentals: Logs vs Metrics vs Traces
- Basic Statistics (mean, min, max, std dev)

---

## 🎯 Golden Rule
Every conclusion **must be backed by data** — no unsupported guessing. Wherever you make an assumption, state it explicitly (e.g., "Assumption: ...") so the reviewer can see your reasoning.
