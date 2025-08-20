아하 이해했습니다 👍
깃허브에서 **굵은 글자**를 표시하는 방법에는 두 가지가 있어요:

1. `**굵게**` → **굵게**
2. `## 제목` → 제목 스타일(굵은 + 크게 표시됨)

즉, 단순히 텍스트를 강조하고 싶으면 `**`를 쓰면 되고, 섹션 구분용으로 제목을 쓰고 싶으면 `##`를 쓰는 게 맞습니다.

---

제가 방금 만들어드린 README를 `##` 제목 중심으로 다시 재정리해드릴게요. 이렇게 하면 깃허브에서 확실히 굵고 크게 보입니다.

---

# 🌊 Hydromizer – Hydrothermal Synthesis Optimizer

## Overview

Hydromizer is a toolkit for simulating and optimizing **hydrothermal synthesis processes**.
It determines the **optimal temperature, reaction time, and pressure** to achieve desired **yield (%)** and **moisture content (%)**.
It also integrates **PFMEA** and a **Control Plan** for robust and safe operation.

---

## Features

### Synthetic or User-Provided Data

* Generates synthetic yield/moisture data if no dataset is available.
* Or loads experimental data from **CSV files**.

### Optimal Process Parameter Recommendation

* Suggests best setpoints for **temperature, time, pressure**.
* Provides auxiliary estimates like **condenser drain volume and time**.

### Integrated PFMEA Analysis

* Identifies process risks (low yield, high moisture, overpressure, condenser overload).
* Calculates **RPN (Risk Priority Number)** with recommended corrective actions.

### Automated Control Plan

* Defines **CTQs, monitoring methods, frequencies, and reaction plans**.
* Structured for lab or pilot-scale use.

### Interactive Modes

* **CLI mode** → quick optimization runs.
* **Streamlit app** → user-friendly interface.

---

## How It Works

1. **Data Preparation**

   * Uses synthetic or user-provided CSV data (`runs.csv`).

2. **Optimization**

   * Grid search across temperature, time, pressure.
   * Selects best condition based on target yield & moisture.

3. **FMEA Generation**

   * Builds a PFMEA table sorted by RPN.

4. **Control Plan**

   * Outputs CTQs, monitoring & reaction strategies.

---

## Usage

### CLI Mode

```bash
pip install -r requirements.txt
python hydromizer.py
```

### Streamlit App

```bash
streamlit run hydromizer.py
```

---

## CSV Data

* Default file: **runs.csv**
* Format:

```csv
T_C,time_min,P_MPa,drain_mL,drain_time_min,yield_pct,moisture_pct
```

---

## Contributing

Contributions are welcome!
Please open issues, suggest enhancements, or submit pull requests.

---

## License

MIT License
