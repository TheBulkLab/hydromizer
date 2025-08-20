# 🌊 Hydromizer

## Overview

Hydromizer is a **console-based toolkit** for simulating and optimizing **hydrothermal synthesis processes**.
It determines the optimal **Temperature (°C), Time (min), and Pressure (MPa)** to achieve a user-specified **yield (%)** and **moisture content (%)**.
The system integrates **PFMEA (Process Failure Mode & Effects Analysis)** and a **Control Plan** for robust and safe operation.

---

## ✨ Features

* **Data Handling**

  * Load experimental data from CSV (`T_C, time_min, P_MPa[, yield_pct, moisture_pct]`).
  * If yield/moisture are missing, the tool auto-generates realistic values.
  * If no data is provided, it creates a synthetic dataset.

* **Optimization**

  * Given target yield and moisture, finds optimal **temperature, time, pressure**.
  * Includes auxiliary predictions like **condenser drain volume and drain time**.

* **FMEA Integration**

  * Evaluates risks: low yield, high moisture, overpressure, condenser overload.
  * Calculates **RPN (Risk Priority Number)** and suggests corrective actions.

* **Control Plan Generation**

  * Outputs CTQs with specs, monitoring methods, frequency, and reaction plans.

* **Console-Friendly Output**

  * Supports `--ascii-out` for Windows-safe console display (no Unicode issues).

---

## ⚙️ How It Works

1. **Dataset Preparation**

   * Load CSV if provided; otherwise generate synthetic process data.

2. **Model Training**

   * Fits a **quadratic ridge regression model** (X → Y mapping).

3. **Optimization Process**

   * Coarse **grid search** across T, t, P ranges.
   * Refines best candidate using **Nelder–Mead simplex**.

4. **Outputs**

   * Recommended setpoints (T, t, P).
   * Predicted yield & moisture.
   * Auxiliary condenser drain estimates.
   * Full PFMEA table sorted by RPN.
   * Detailed Control Plan.

---

## 🚀 Usage

### Installation

```bash
pip install numpy pandas
```

### Run (Interactive)

```bash
python hydro_hfmea_inverse.py
```

### Run with Command-Line Options

```bash
python hydro_hfmea_inverse.py --target-y 90 --target-m 1.0 \
    --data your_data.csv --grid 16x16x12 --pressure-mode autogenous \
    --cond-duty-w 500 --ascii-out
```

### Options

* `--data your.csv` → Load dataset
* `--target-y 85`   → Target yield (%)
* `--target-m 1.5`  → Target moisture (%)
* `--grid 16x16x12` → Grid resolution for coarse search
* `--pressure-mode` → `autogenous` (default) or `decoupled`
* `--ascii-out`     → ASCII-safe console output

---

## 📂 Example CSV Format

```csv
T_C,time_min,P_MPa,yield_pct,moisture_pct
180,240,10,87.5,1.2
200,300,12,91.0,0.9
```

If `yield_pct` or `moisture_pct` are missing, the tool auto-generates them.

---

## 🤝 Contributing

Contributions are welcome! Please open an issue or submit a pull request for improvements.

---

## 📄 License

MIT License

---
