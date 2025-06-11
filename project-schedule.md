# LLM-Guided Risk Assessment for Grid Agent Systems

## 🌟 Goal

Use **ChatGPT**, **Pandapower**, and **Python** to simulate and assess risk scenarios in power systems based on the IEEE 14-bus test case. You'll use AI to generate what-if situations, simulate them, and analyze their impact on system reliability and safety.

---

## ✅ 8-Week Project Schedule

### **Week 1: Onboarding & Foundations**

* Learn basic concepts: What is a power grid? What is ACOPF?
* Review provided materials and documentation.
* Install necessary tools (Pandapower, Python, GitHub setup).
* Run a base simulation using IEEE 14-bus with Pandapower.
* Record and explain what the simulation results show.

**Deliverable**: A working notebook running ACOPF and explaining the base case.

---

### **Week 2: LLM-Prompted Scenario Simulation**

* Use ChatGPT to generate 5 risk scenarios (e.g., line outage, load spike).
* Learn how to modify Pandapower models using Python.
* Simulate each scenario and observe changes in voltages, line flows, and feasibility.
* Record all results in a structured table.

**Deliverable**: Notebook with 5 simulations and a results table.

---

### **Week 3: Risk Scoring and Scenario Library**

* Define a "risk score" based on voltage violations, line overloads, and feasibility.
* Write a Python function to compute this score.
* Create a structured dataset (JSON/CSV) storing each scenario and its risk.
* Visualize and rank scenarios by severity.

**Deliverable**: Risk scoring function, dataset file, and a ranked list of scenarios.

---

### **Week 4: Interactive CLI Tool**

* Create a Python command-line interface (CLI) to type natural-language scenarios.
* Use pattern-matching or prompts to translate inputs into Pandapower modifications.
* Run simulations and print results and risk score in real time.

**Deliverable**: A CLI script to simulate and score user-defined scenarios.

---

### **Week 5: Red-Teaming LLM Predictions**

* Ask ChatGPT to predict whether a scenario will be feasible or not.
* Compare prediction with actual simulation results.
* Record ChatGPT accuracy in a log or table.

**Deliverable**: Table comparing LLM prediction vs simulation results, with notes.

---

### **Week 6: Visualization and Reporting**

* Visualize bus voltages (bar chart or network layout).
* Highlight overloaded lines.
* Create plots to compare risk scores across scenarios.

**Deliverable**: Notebook or Python script with all plots and brief descriptions.

---

### **Week 7: Larger Grids and Literature Context**

* Extend simulations to IEEE 57-bus system.
* Read 1-2 articles or blog posts about power grid vulnerability.
* Relate your work to real-world grid planning and risk assessment.

**Deliverable**: 1–2 simulations on a larger grid and a 1-page reflection.

---

### **Week 8: Final Report and Presentation**

* Compile all work into a structured report.

  * Introduction
  * Methods
  * Risk scenarios
  * Results and analysis
  * Visualizations
  * Reflections and next steps
* Prepare a 5–10 minute slide presentation.

**Deliverable**: Final report (PDF or notebook) + presentation slides.

---

## 🚀 Optional Extensions

* Add red-teaming logic to "trick" the agent.
* Simulate N-2 failures.
* Use IEEE 118-bus or synthetic data.
* Implement a simple Streamlit app.

---

Good luck, and remember: the goal is not just to run simulations, but to understand how AI can reason about risk in complex systems!
