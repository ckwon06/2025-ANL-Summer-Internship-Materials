## ✅ 1. Clone the GitHub repo

**Repo URL:**
`https://github.com/ckwon06/C.Lee--2025-Summer-Internship-Materials.git`

**Steps:**

1. **Open a terminal.**

2. **Go to a folder for projects (if not already):**

   ```bash
   cd ~
   mkdir -p projects
   cd projects
   ```

3. **Clone the repository:**

   ```bash
   git clone https://github.com/ckwon06/C.Lee--2025-Summer-Internship-Materials.git
   cd C.Lee--2025-Summer-Internship-Materials
   ```

---

## ✅ 2. Create a notebook with a simple `pandapower` example

**Assumptions:**

* The conda environment is already activated.
* You just need to install packages and create a notebook.

1. **Install `pandapower` and `jupyter` (only once per environment):**

   ```bash
   pip install pandapower jupyter
   ```

2. **Start Jupyter Notebook:**

   ```bash
   jupyter notebook
   ```

3. **In your browser**, go to the `C.Lee--2025-Summer-Internship-Materials` folder.

4. **Create a new notebook** and name it `simple_pandapower.ipynb`.

5. **Paste and run this code:**

   ```python
   import pandapower as pp

   net = pp.create_empty_network()
   bus1 = pp.create_bus(net, vn_kv=20.)
   bus2 = pp.create_bus(net, vn_kv=0.4)
   pp.create_transformer(net, bus1, bus2, std_type="0.4 MVA 20/0.4 kV")
   pp.create_load(net, bus2, p_mw=0.1, q_mvar=0.05)
   pp.create_ext_grid(net, bus1)

   pp.runpp(net)

   print(net.res_bus)
   print(net.res_line)
   ```

6. **Save the notebook**.

---

## ✅ 3. Push the notebook to GitHub

1. **Make sure you are still in the repo folder**:

   ```bash
   cd ~/projects/C.Lee--2025-Summer-Internship-Materials
   ```

2. **Track the new notebook file:**

   ```bash
   git add simple_pandapower.ipynb
   ```

3. **Commit the change:**

   ```bash
   git commit -m "Add simple pandapower notebook"
   ```

4. **Push to GitHub:**

   ```bash
   git push origin main
   ```
