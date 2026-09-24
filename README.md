# 🗓️ Smart Shift Scheduler & Workforce Allocation Tool

An interactive, constraint-aware workforce scheduling tool designed to automate weekly shift planning for retail and service teams. Built with a heuristic allocation algorithm that handles complex operational constraints, availability preferences, and employee compatibility.

🔗 **Live Demo:** [[https://yo.github.io/smart-shift-scheduler/](https://minchi-12.github.io/weekly_shift_scheduler/)]

## 📌 Problem Overview
In shift-based operational environments (cafes, retail stores, support desks), weekly roster scheduling involves balancing numerous operational hard constraints and employee preferences. Manual planning often leads to:
* Violation of mandatory rest periods between consecutive shifts
* Unbalanced workload distributions
* Shift under-coverage or rule violations (e.g., gender requirements for night shifts)
* Incompatibility conflicts between team members

## ⚙️ Scheduling Logic & Constraints

The application utilizes a **greedy heuristic with dynamic constraint propagation** (*Most Constrained Variable First*), prioritized as follows:

1. **Hard Operational Constraints:**
   - **Coverage Requirements:** Dynamically adjusted based on managerial presence and special events (e.g., dedicated cleaning crew mode).
   - **Consecutive Shift / Rest Period:** Prevents assigning morning opening shifts (09:00–14:00) to personnel who closed the previous night (19:00–24:00).
   - **One Shift Per Day Rule:** Strictly restricts multiple assignments per employee on the same calendar day.
   - **Interpersonal Conflicts:** Prevents scheduling incompatible employees on overlapping shift windows.
   - **Role & Gender Quotas:** Guarantees mandatory criteria (e.g., at least 1 male on closing shifts).

2. **Soft Preferences & Optimization:**
   - **Worker Availability:** Matches individual preferences (`Want`, `Flexible`, `Unavailable`).
   - **Fair Workload Distribution:** Prioritizes individuals furthest from their weekly shift target (min/max bounds).
   - **Shift Type Diversity:** Balances an employee’s assigned shifts across opening, mid-day, and closing rotations.

3. **Interactive Human-in-the-Loop Management:**
   - Instant slot replacement and conflict-checked manual override via a modal interface.
   - Excel / Google Sheets roster import (`.xlsx`) parsing employee preferences directly into the system.


## 🛠️ Tech Stack

* **Frontend:** HTML5, Modern CSS (Design Tokens, Responsive Grid), Vanilla JavaScript (ES6+)
* **Data Processing:** SheetJS (`xlsx.js`) for spreadsheet ingestion
* **Storage:** Local state persistence for seamless weekly rollover


## 🚀 How to Run Locally

No build tools or servers required:
1. Clone this repository:
   ```bash
   git clone [https://minchi-12.github.io/weekly_shift_scheduler/]([https://github.com/your-username/smart-shift-scheduler.git](https://minchi-12.github.io/weekly_shift_scheduler/))
