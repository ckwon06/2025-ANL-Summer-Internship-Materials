## 📘 Learning the MATPOWER Case Format (for Beginners)

### ✅ What is MATPOWER?

**MATPOWER** is a widely used MATLAB-based power system simulation package.
Its input format (called a *MATPOWER case file*) is used by many power system tools to define the structure and data of power networks for power flow or OPF analysis.

---

## 🧠 What to Learn

MATPOWER defines a power system using structured arrays (usually in a `.m` or `.mat` file) with these main components:

| Component | Description                        |
| --------- | ---------------------------------- |
| `bus`     | Buses (nodes) in the system        |
| `gen`     | Generators attached to buses       |
| `branch`  | Transmission lines or transformers |
| `gencost` | Cost function of each generator    |
| `baseMVA` | Power base for normalization       |

---

## 🧪 Step-by-Step: Explore a MATPOWER Case

### Step 1: View a Sample Case File (Text-Based)

Let’s look at the IEEE 9-bus system from [MATPOWER’s GitHub](https://github.com/MATPOWER/matpower/blob/master/data/case9.m):

Click to view:
👉 [https://github.com/MATPOWER/matpower/blob/master/data/case9.m](https://github.com/MATPOWER/matpower/blob/master/data/case9.m)

Or download the file:

```bash
wget https://raw.githubusercontent.com/MATPOWER/matpower/master/data/case9.m
```

Open it in a text editor:

```bash
nano case9.m
```

You’ll see something like:

```matlab
function mpc = case9
mpc.baseMVA = 100;

mpc.bus = [
    1	1	0	0	0	0	1	1	0	230	1	1.06	0.94;
    ...
];

mpc.gen = [
    1	0	0	300	-300	1	100	1	250	90;
    ...
];

mpc.branch = [
    1	4	0	0.0576	0	250	250	250	0	0	1	-360	360;
    ...
];
```

---

## 🔍 What Each Section Means

### `mpc.bus`

Each row = one bus (node).

| Column | Meaning                           |
| ------ | --------------------------------- |
| 1      | Bus ID                            |
| 2      | Bus type (1=load, 2=gen, 3=slack) |
| 3–6    | Power demands (Pd, Qd)            |
| 9–12   | Voltage (Vmag, Vangle, etc)       |

---

### `mpc.gen`

Each row = one generator.

| Column | Meaning                       |
| ------ | ----------------------------- |
| 1      | Bus ID where gen is connected |
| 2–3    | Pg, Qg (power output)         |
| 9–10   | Pmin, Pmax (bounds)           |

---

### `mpc.branch`

Each row = one transmission line or transformer.

| Column | Meaning                                      |
| ------ | -------------------------------------------- |
| 1–2    | From bus, to bus                             |
| 3–5    | Resistance (r), reactance (x), line charging |
| 6–8    | Thermal limits                               |

---

### `mpc.gencost`

Cost function per generator.

* Defines how cost depends on output power.
* Usually a **polynomial**:
  `cost = c2 * Pg² + c1 * Pg + c0`

---

## 🛠️ Run MATPOWER Data in Pandapower

Pandapower can load MATPOWER files directly (if you convert to `.mat` format using MATLAB or Octave), or you can **manually translate** a MATPOWER case to Pandapower format using the same structure.

Alternatively, you can inspect pre-built versions:

```python
import pandapower.networks as pn
net = pn.case9()  # A translation of MATPOWER's case9.m
```

Explore:

```python
print(net.bus)
print(net.gen)
print(net.line)
```

---

## 🧑‍🎓 Suggested Learning Tasks for the Student

| Task                                                                    | Description                                |
| ----------------------------------------------------------------------- | ------------------------------------------ |
| ✅ Read and explain `case9.m`                                            | Identify 3 buses, 3 generators, 9 branches |
| ✅ Match `bus`, `gen`, `branch` structure with Pandapower `net` object   |                                            |
| ✅ Modify a MATPOWER case (e.g., add load or change generator limit)     |                                            |
| ✅ Convert to Pandapower using `create_bus`, `create_gen`, `create_line` |                                            |

---

## 📚 Resources for Deeper Learning

* [MATPOWER Manual](https://matpower.org/docs/manual.pdf) – skip to section 4 (Data Format)
* Pandapower Docs:
  [https://pandapower.readthedocs.io](https://pandapower.readthedocs.io/en/latest/)
* IEEE Test Cases in MATPOWER Format:
  [https://github.com/power-grid-lib/pglib-opf](https://github.com/power-grid-lib/pglib-opf)
