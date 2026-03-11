# IoT-NetGuard
## Anomaly Detection for IoT Cybersecurity

**Research Area:** Machine Learning and Deep Learning Methods for Anomaly Detection  
**Dataset:** IoT-23 — Stratosphere Laboratory  
**Goal:** Find the best anomaly detection model balancing accuracy and time efficiency

---

## Project Structure

```
IoT-NetGuard/
├── notebooks/
│   ├── 01_Data_Preprocessing.ipynb   ← Load & clean all 23 capture files
│   ├── 02_Naive_Bayes.ipynb          ← Gaussian Naïve Bayes classifier
│   ├── 03_SVM.ipynb                  ← Support Vector Machine (RBF kernel)
│   ├── 04_Decision_Trees.ipynb       ← Decision Tree with feature importance
│   ├── 05_CNN.ipynb                  ← Deep Neural Network (TensorFlow/Keras)
│   └── 06_Model_Comparison.ipynb     ← Side-by-side results & charts
├── outputs/                          ← Auto-generated plots & confusion matrices
└── README.md
```

---

## How to Run

### Step 1 — Prerequisites

```bash
pip install pandas numpy scikit-learn tensorflow==2.4 matplotlib seaborn
```

### Step 2 — Data Preprocessing

1. Open `notebooks/01_Data_Preprocessing.ipynb`
2. Update `BASE_PATH` to point to your local IoT-23 dataset folder
3. Run all cells → generates `iot23_combined.csv`

### Step 3 — Run Models (in order)

| Notebook | Model | Rows Used | Est. Time |
|----------|-------|-----------|-----------|
| `02_Naive_Bayes.ipynb` | Gaussian Naïve Bayes | 1.44M | < 1 min |
| `03_SVM.ipynb` | SVM (RBF) | 400K | 10–60 min |
| `04_Decision_Trees.ipynb` | Decision Tree | 1.44M | 1–5 min |
| `05_CNN.ipynb` | Deep Neural Net | 1.44M | 10–30 min |

### Step 4 — Compare Results

1. Open `notebooks/06_Model_Comparison.ipynb`
2. Fill in your accuracy and time results from each model
3. Run all cells → generates comparison charts

---

## Dataset

**IoT-23** — A labeled dataset with malicious and benign IoT network traffic.  
Stratosphere Laboratory. Agustin Parmisano, Sebastian Garcia, Maria Jose Erquiaga.  
January 22, 2020.  
https://www.stratosphereips.org/datasets-iot23

### Capture Scenarios Used

| Captures | Count | Type |
|----------|-------|------|
| CTU-IoT-Malware-Capture-1,3,7,8,9,17,20,21,33–36,39,42–44,48,49,52,60 | 20 | Malicious |
| Benign captures within above | 3 | Benign |

### Attack Labels

- `PartOfAHorizontalPortScan` — Port scanning activity
- `Okiru` — Okiru botnet variant
- `DDoS` — Distributed Denial of Service
- `C&C` — Command and Control traffic
- `Attack` — Generic attack
- `C&C-HeartBeat` — C&C keep-alive
- `C&C-FileDownload` — Malware file download
- `C&C-Torii` — Torii botnet
- `FileDownload` — Suspicious file download
- `C&C-HeartBeat-FileDownload` — Combined C&C
- `C&C-Mirai` — Mirai botnet
- `Benign` — Normal traffic

---

## Features Used (24 total)

| Feature | Description |
|---------|-------------|
| `duration` | Connection duration |
| `orig_bytes` | Originating bytes |
| `resp_bytes` | Response bytes |
| `missed_bytes` | Missed bytes |
| `orig_pkts` | Originating packets |
| `orig_ip_bytes` | Originating IP bytes |
| `resp_pkts` | Response packets |
| `resp_ip_bytes` | Response IP bytes |
| `proto_icmp/tcp/udp` | Protocol (one-hot encoded) |
| `conn_state_*` | Connection state (one-hot encoded, 13 states) |

---

## Environment

| Component | Version |
|-----------|---------|
| Python | 3.8 |
| TensorFlow | 2.4 |
| scikit-learn | Latest |
| Pandas | Latest |
| Anaconda Jupyter Notebook | Latest |

---

## Citation

Stratosphere Laboratory. *A labeled dataset with malicious and benign IoT network traffic.*  
January 22th, 2020. Agustin Parmisano, Sebastian Garcia, Maria Jose Erquiaga.
