# Hindalco Synthetic Data Interpolation problem

## 🚀 problem Summary
In this problem, we tackled the challenge of interpolating missing process parameters in Hindalco's specialty alumina manufacturing data. Due to irregular sampling and missing sensor values, key process parameters are often partially logged, making direct downstream analytics unreliable. We designed a pipeline to interpolate these values across time, generating complete multivariate time series.

---

## 🧠 Problem Statement
Given multiple multivariate time series (one per run), where each file contains observations at irregular time intervals and missing values for several parameters, generate a complete matrix of parameter values at fixed time points.

### Why it's hard:
- Time sampling is irregular
- Parameters are missing at different timestamps
- Parameter dynamics are often interdependent

---

## 🏭 Real-World Use Case
This problem was developed in the context of process optimization for a large manufacturing setup (Hindalco). Sensor dropouts, manual logs, and uneven sampling are common issues in industrial environments. Filling these gaps enables consistent data analysis and supports better decision-making.

---

## 💡 Inspiration from Other Domains
We drew inspiration from healthcare time-series datasets like **PhysioNet**, where patient vitals are logged asynchronously. Similar interpolation problems arise when modeling patient states for diagnosis. Despite differing domains, the nature of missingness and temporal complexity is shared.

---

## 🧾 Sample Data Format
Input data:
```json
[
  {"timestamp": "2023-07-01T10:00:00Z", "temperature": 85.2},
  {"timestamp": "2023-07-01T10:10:00Z", "pH": 6.8, "flow_rate": 12.4},
  {"timestamp": "2023-07-01T10:20:00Z", "temperature": 85.9, "pH": 6.9}
]
```

Expected interpolated data:
```json
[
  {"timestamp": "2023-07-01T10:00:00Z", "temperature": 85.2, "pH": 6.7, "flow_rate": 12.0},
  {"timestamp": "2023-07-01T10:05:00Z", "temperature": 85.3, "pH": 6.75, "flow_rate": 12.2},
  ...
]
```

---

## 🧭 Approach Summary
- Parse and structure irregular time series
- Interpolate missing values on a fixed-resolution grid
- Hold out known values and validate interpolation via MSE

---

## 📊 Visual Representation
![Data Structure](Screenshot%202025-04-07%20at%2011.11.28%E2%80%AFAM.png)
Green dots = observed values. All other values are estimated.

---

## ✅ Outcome
- Clean, complete time-aligned parameter logs
- Enables advanced analytics, monitoring, and control strategies
- A flexible solution that generalizes to many time series forecasting and interpolation challenges

---

## Core Methodologies Used:

* A single Model consist of 
  * Transformers with time based attention instead of position based.
  * Variational Autoencoder
  * Bidirectional RNN


## 🧰 Tech Used
*  PyTorch,Python
* Pandas & Numpy for manipulation

---

_This problem bridges industrial process control with time series modeling, showcasing practical utility and real-world impact._
