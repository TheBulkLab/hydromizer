Hydromizer – Hydrothermal Synthesis Optimizer

Hydromizer is a simulation and optimization toolkit for hydrothermal synthesis processes. It helps researchers and engineers determine the optimal temperature, reaction time, and pressure to achieve desired yield (%) and moisture content (%). The system also integrates PFMEA (Process Failure Mode & Effects Analysis) and Control Plan generation for process safety and robustness.

✨ Features

Synthetic or User-Provided Data:

Automatically generates synthetic yield/moisture data for simulations, or

Loads experimental data from CSV files for model fitting.

Optimal Process Parameter Recommendation:

Recommends best setpoints for temperature, time, and pressure to achieve user-specified targets.

Provides auxiliary estimates such as condenser drain volume and time.

Integrated PFMEA Analysis:

Identifies key process risks (low yield, high moisture, overpressure, condenser overload, runaway risk).

Calculates Risk Priority Number (RPN) and recommends corrective actions.

Automated Control Plan:

Generates a clear monitoring and reaction plan for critical process parameters (CTQs).

Structured for practical operator use.

Interactive Mode (CLI or Streamlit):

CLI prompts allow quick optimization runs.

Streamlit app (optional) offers a user-friendly interface.

⚙️ How It Works

Data Preparation

If no CSV file is provided, the system generates synthetic hydrothermal data (random yield/moisture responses).

If a CSV (runs.csv) exists, the system fits a linear correction model to align surrogate predictions with experimental data.

Optimization

A grid search explores feasible ranges for T (°C), time (min), and P (MPa).

Each condition is scored based on how well it matches the target yield and moisture.

The top-ranked setpoint is selected as the recommendation.

FMEA Generation

Builds a lightweight PFMEA table sorted by RPN.

Suggests preventive/corrective actions for high-risk failure modes.

Control Plan

Defines CTQs, monitoring methods, frequencies, and reaction plans.

Designed for immediate integration into lab or pilot-scale operations.

🚀 Usage
CLI Mode
pip install -r requirements.txt
python hydromizer.py


You’ll be prompted to enter target yield (%) and target moisture (%).
The system outputs:

Recommended temperature, time, and pressure

Predicted yield/moisture

Auxiliary drain estimates

PFMEA table

Control Plan

Streamlit App (Optional)
streamlit run hydromizer.py


Opens a web app for interactive use.

📂 CSV Data

Default filename: runs.csv

Format:

T_C,time_min,P_MPa,drain_mL,drain_time_min,yield_pct,moisture_pct


If present, the system uses it to improve accuracy.

🤝 Contributing

Contributions are welcome! Feel free to open issues, suggest enhancements, or submit pull requests.

📄 License

This project is open-source and available under the MIT License
.
