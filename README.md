# RapidTable AI — Heuristic-Based Seating Optimization

RapidTable AI is an interactive, intelligent queue and table allocation management system designed for high-throughput restaurant environments. The engine replaces simple first-come-first-served logic with a dynamic priority-scoring heuristic to maximize seat occupancy and minimize peak-hour idle times.

## 🧠 The AI Heuristic Engine Explained

The core of the system relies on a mathematical heuristic function that dynamically calculates a priority score for every waiting party:

$$Score = TimeComponent + SeatFillingComponent + GroupSizeWeight$$

### 1. Multi-Tiered Time Component
To prevent customer burnout while prioritizing efficiency, wait times are weighted aggressively over time:
* **$\le$ 10 minutes:** $+10\text{ points}$ per minute.
* **> 10 minutes:** $+30\text{ points}$ per minute (exponentially bumps long-waiting guests to the front).

### 2. Seat Filling Efficiency (Capacity Optimization)
Tables are structured in modular 4-seat units. The algorithm checks how tightly a party fills a configuration:
* **Perfect Fit Bonus:** $+50\text{ points}$ if a party completely fills the allotted seat blocks (zero empty chairs).
* **Inefficiency Penalty:** $-20\text{ points}$ if a small party wastes more than half of an allocated layout.

### 3. Special Scenario Weighting
* Large groups ($>4$ people) receive an automatic $+20\text{ point}$ nudge to compensate for the natural difficulty of accommodating larger parties.

## 🛠️ Tech Stack & Architecture
* **Frontend UI:** Tailwind CSS & Lucide Icons (Clean, responsive dashboard layout).
* **Core Logic:** Pure Vanilla JavaScript (Client-side simulation matrix tracking dynamic countdowns and priority queue sorting).
