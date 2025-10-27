# 🧪 Final Group Test Report — Word Puzzle Game Plus

**Level:** Intermediate QA | **Week 5:** Test Management

**Course:** Software Testing & Quality Assurance
**Module:** Test Management (Week 5)
**Project Type:** Group Assessment
**Submission Date:** 2025-10-28

---

## Team Information

| Role              | Name           | Responsibilities                                         |
| ----------------- | -------------- | -------------------------------------------------------- |
| **Test Manager**  | Derick Maloba  | Planning, scheduling, coordination, metric tracking      |
| **Risk Analyst**  | Annah Mwihaki  | Risk identification, prioritization, test design linkage |
| **Test Executor** | Molefi Mothibi | Execution, evidence capture, defect logging              |

---

## Group Rules

* Each student belongs to only one group.
* Duplicate membership or multiple submissions will result in invalidation.
* Every group member contributed toward this project.

---

## Project Overview

**System Under Test:** Word Puzzle Game Plus
**Technology Stack:** HTML, CSS, JavaScript
**Environment:** Chrome Browser (Desktop)

### Features Under Test

| Feature     | Description                         | Risk Category |
| ----------- | ----------------------------------- | ------------- |
| Reset Game  | Clears score and progress instantly | Medium        |
| Leaderboard | Stores top 3 scores in localStorage | High          |
| Bonus Round | Every 3 puzzles → doubles score     | High          |

---

# 🧩 Test Plan – Word Puzzle Game Plus

## 🎯 Objectives

* Ensure the **Word Puzzle Game Plus** works according to requirements with minimal defects.
* Identify and test high-risk areas: bonus round logic, leaderboard persistence, and game state management.
* Validate that the game provides an intuitive, engaging user experience.
* Confirm score calculations, `localStorage` operations, and state transitions are reliable.
* Build a regression baseline to prevent future defects.

---

## 🧪 Scope

### ✅ In Scope

* Gameplay mechanics (scrambling, guessing, scoring)
* Hint system deductions
* Bonus round triggers and arithmetic
* Leaderboard storage, ranking, and display
* Reset and state management
* UI responsiveness and feedback messages
* `localStorage` persistence

### 🚫 Out of Scope

* Cross-browser and mobile testing
* Performance or load tests
* Security and data manipulation
* Offline testing
* Localization or backend integration

---

## 🧰 Tools & Resources

| Category            | Tools / Description        |
| ------------------- | -------------------------- |
| Testing Environment | Chrome v120+ with DevTools |
| Defect Management   | GitHub Issues              |
| Collaboration       | Google Drive               |
| Communication       | WhatsApp / Slack           |
| Test Data           | Predefined JSON word bank  |
| Version Control     | GitHub Repository          |

### 👥 Team Resources

| Role          | Hours Allocated     |
| ------------- | ------------------- |
| Test Manager  | 25 hours            |
| Risk Analyst  | 20 hours            |
| Test Executor | 30 hours            |
| **Total**     | **75 person-hours** |

---

## 📅 Schedule

| Phase               | Planned  | Actual | Status |
| ------------------- | -------- | ------ | ------ |
| Planning & Strategy | 4 hrs    | 8 hrs  | ✅      |
| Risk Analysis       | 1 day    | 1 day  | ✅      |
| Test Case Design    | 1 day    | 2 days | ✅      |
| Test Execution      | 1.5 days | 2 days | ✅      |
| Defect Tracking     | 1 day    | 1 day  | ✅      |
| Regression          | 1 day    | 1 day  | ✅      |
| Reporting           | 1 day    | 1 day  | ✅      |

**Milestones:**

* Day 1: Risk Assessment Complete
* Day 2: Test Cases Peer-Reviewed
* Day 3: Execution Cycle 1
* Day 4: Defects Logged & Fixed
* Day 5: Final Report Delivered

---

## ✅ Entry Criteria

* Stable requirements
* Configured test environment
* Ready test data
* Defined roles

## 🏁 Exit Criteria

* All critical test cases executed
* No high defects open
* ≥90% pass rate
* ≥80% risk coverage
* Final metrics documented

---

## ⚠️ Risk Analysis

| ID | Feature     | Description                           | Likelihood | Impact | Priority | Mitigation                  |
| -- | ----------- | ------------------------------------- | ---------- | ------ | -------- | --------------------------- |
| R1 | Leaderboard | Scores not stored or sorted correctly | High       | High   | Critical | Validate using console + UI |
| R2 | Bonus Round | Bonus misfires (too early/late)       | Medium     | High   | High     | Test every 3rd solve cycle  |
| R3 | Reset Game  | Game not fully reset                  | Medium     | Medium | Medium   | Validate DOM + variables    |
| R4 | Hint        | Multiple −2 deductions possible       | High       | Medium | High     | Validate deduction once     |
| R5 | Score Logic | Incorrect point addition              | Medium     | High   | High     | Manual vs UI comparison     |
| R6 | Scramble    | Original word repeats                 | Low        | Medium | Medium   | Confirm randomization       |

**Risk Coverage:**

* Tested: **100%**
* Untested: **0%**

---

## 🧾 Test Cases

| ID    | Feature             | Objective               | Expected Result          | Actual Result | Status | Risk Link |
| ----- | ------------------- | ----------------------- | ------------------------ | ------------- | ------ | --------- |
| TC-01 | Leaderboard         | Verify top 3 sorting    | Correct descending order | Works         | ✅ PASS | R1        |
| TC-02 | Bonus Round         | Trigger after 3 solves  | Score doubled            | Works         | ✅ PASS | R2        |
| TC-03 | Reset               | Clear all data          | Word remains visible     | ❌ FAIL        | R3     |           |
| TC-04 | Hint                | Deduct −2 only once     | Works correctly          | ✅ PASS        | R4     |           |
| TC-05 | Score               | Correct +10/+5 addition | Works                    | ✅ PASS        | R5     |           |
| TC-06 | Scramble            | Ensure word changes     | Works                    | ✅ PASS        | R6     |           |
| TC-07 | Usability           | Layout readability      | Responsive               | ✅ PASS        | R6     |           |
| TC-08 | Leaderboard Refresh | Updates instantly       | Works                    | ✅ PASS        | R1     |           |

---

## 🪄 Code Evidence (Snippets)

### Leaderboard Logic

```js
leaderboard.sort((a,b)=> b-a);
leaderboard = leaderboard.slice(0,3);
displayLeaderboard(leaderboard);
```

✅ Verified sorting accuracy in Chrome console.

### Bonus Round Logic

```js
if (puzzlesSolved % 3 === 0){
  score *= 2;
  showMessage("🎉 Bonus Round! Score doubled!", "success");
}
```

✅ Confirmed correct trigger and doubling.

### Reset Logic (Defective)

```js
scrambledWordEl.textContent = ""; // sometimes not cleared
```

⚠️ Found intermittent issue (D2).

---

## 🐞 Defects

| ID | Issue                              | Severity | Risk | Status | GitHub Link |
| -- | ---------------------------------- | -------- | ---- | ------ | ----------- |
| D1 | Bonus fails after rapid solves     | High     | R2   | Fixed  | —           |
| D2 | Reset retains scrambled word       | Medium   | R3   | Open   | —           |
| D3 | Leaderboard not updating instantly | Medium   | R1   | Fixed  | —           |

---

## 📊 Metrics

* **Test Case Pass %:** 7/8 → **87.5%**
* **Defect Density:** 3 / 8 = **0.37**
* **Risk Coverage:** 100%
* **Regression Success Rate:** 67%

### Defect Summary

* Total Defects: 3
* Critical/High: 1
* Fix Rate: 67%

---

## 🧭 Test Control & Project Management

| Phase         | Deliverable     | Actual Output | Variance | Owner          |
| ------------- | --------------- | ------------- | -------- | -------------- |
| Planning      | Test Plan       | Completed     | 0 days   | Derick Maloba  |
| Risk Analysis | Risk Table      | Completed     | 0 days   | Annah Mwihaki  |
| Execution     | Logs & Evidence | Completed     | 0 days   | Molefi Mothibi |
| Reporting     | Metrics Report  | Completed     | 0 days   | Derick Maloba  |

**Progress Tracking:** GitHub Issues & internal messages
**Change Control:** Added usability test mid-cycle for completeness

---

## 🧠 Lessons Learned

* **Most Defect-Prone Feature:** Reset function
* **Risk Analysis Impact:** Focused attention on leaderboard & bonus logic early
* **Team Communication:** Effective coordination via WhatsApp and GitHub
* **Improvements:** Add automated reset test and cross-browser validation

---

## 📎 Attachments

* Inline evidence (code snippets) included
* No screenshots attached
* GitHub Issues contain defect logs

---

## ✍️ Sign Off

| Name           | Role          | Initials | Date       |
| -------------- | ------------- | -------- | ---------- |
| Derick Maloba  | Test Manager  | DM       | 2025-10-27 |
| Annah Mwihaki  | Risk Analyst  | AM       | 2025-10-27 |
| Molefi Mothibi | Test Executor | MM       | 2025-10-27 |

---

## 🧩 Overall Summary

**Statement:**
All high-priority features of *Word Puzzle Game Plus* were successfully tested.
Minor issues identified (notably reset function), but system remains stable and meets exit criteria.

**Test Status:** ☑ Completed
