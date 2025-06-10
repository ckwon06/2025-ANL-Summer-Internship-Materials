## 🧠 Part 1: Learn Power System Basics

### ✅ Goal:

Understand enough to read, simulate, and modify simple power flow and optimal power flow models.

### 📘 Background Reading (Simple and Visual):

1. **What is a Power System?**
   Read: [Chapter 1 of Power Systems Analysis](https://doi.org/10.1016/B978-0-08-101111-9.00001-X)

2. **What is Power Flow (Load Flow)?**

   * Read: [Pandapower Docs](https://pandapower.readthedocs.io/en/latest/powerflow.html)

3. **What is Optimal Power Flow (OPF)?**

   * Short intro: [ACOPF on Pandapower Docs](https://pandapower.readthedocs.io/en/latest/opf.html)
   * Concept:

     * ACOPF = Minimize cost (e.g., fuel) subject to power system physical laws (AC power flow equations) and operational limits (e.g., generation, voltage, line flow).

4. **Key Concepts to Learn:**

   * Bus (node)
   * Line (edge)
   * Load (demand)
   * Generator (supply)
   * Voltage, real/reactive power
   * Constraints (limits on voltages, flows, etc.)

---

## 💻 Part 2: Setup Pandapower and Python Environment

Follow this if not already set up:

```bash
module load anaconda3
conda create -n pandapower-env python=3.9
conda activate pandapower-env
pip install pandapower
```

---

## 🛠️ Part 3: Run a Simple Power Flow (PF) Example

Create a file `run_pf.py`:

```python
import pandapower as pp
import pandapower.networks as pn
import pandapower.plotting as plot

# Create IEEE 9-bus example system
net = pn.case9()

# Run power flow
pp.runpp(net)

# Print results
print(net.res_bus[["vm_pu", "va_degree"]])  # Voltage magnitude and angle
print(net.res_line[["p_from_mw", "loading_percent"]])  # Line flows

# (Optional) Show network plot
# plot.simple_plot(net)
```

To run:

```bash
python run_pf.py
```

🧠 **What’s happening?**

* It loads a standard test system (IEEE 9-bus).
* Runs AC power flow (calculates voltages, flows, losses).
* Prints the results.

---

## ⚡ Part 4: Run a Simple AC Optimal Power Flow (ACOPF)

Create a file `run_opf.py`:

```python
import pandapower as pp
import pandapower.networks as pn

net = pn.case9()

# Define cost function for each generator (quadratic cost: c2 * p^2 + c1 * p + c0)
pp.create_polynomial_cost(net, element=0, et="gen", cp1_eur_per_mw=10, cp2_eur_per_mw2=0.02)
pp.create_polynomial_cost(net, element=1, et="gen", cp1_eur_per_mw=12, cp2_eur_per_mw2=0.01)
pp.create_polynomial_cost(net, element=2, et="gen", cp1_eur_per_mw=20, cp2_eur_per_mw2=0.015)

# Run AC OPF
pp.runopp(net)

# Print generator outputs and objective
print(net.res_gen[["p_mw", "q_mvar"]])
print("Total cost: €", net.res_cost)
```

To run:

```bash
python run_opf.py
```

🧠 **What’s happening?**

* Pandapower solves an optimization problem:
  **Minimize generation cost** while **satisfying power flow equations and limits**.
* Output shows how much each generator is producing.

---

## 🧠 Summary

| Task                 | Command or File                      |
| -------------------- | ------------------------------------ |
| Create environment   | `conda create -n pandapower-env ...` |
| Activate environment | `conda activate pandapower-env`      |
| Install pandapower   | `pip install pandapower`             |
| Run PF example       | `python run_pf.py`                   |
| Run OPF example      | `python run_opf.py`                  |
| Explore results      | Look at `net.res_*` tables           |
