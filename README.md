# mmWave Radar AI – Hidden Object Detection (AIR G Research Assignment)

This repository contains a complete end-to-end implementation of the **mmWave Radar AI Project** assigned by **AIR G International**.  
The goal is to simulate radar signals, generate Range–Doppler (RD) heatmaps, train ML models, and detect **hidden metal objects** under clutter using synthetic 60 GHz FMCW radar data.

---

## 📌 Project Overview

This project covers:

### **Part 1 — Radar Signal Simulation**
- Synthetic 1D/2D FMCW radar data generation  
- Range FFT & Doppler FFT  
- RD heatmap visualization  
- Empty room, metal, and clutter scenarios  

### **Part 2 — Metal vs Non-Metal Classification**
- Dataset creation using synthetic RD heatmaps  
- CNN-based classifier  
- Baseline SVM model  
- Evaluation metrics & predictions  

### **Part 3 — Hidden Object Detection**
- Cluttered heatmap creation  
- Background subtraction & noise filtering  
- CFAR-like region proposal  
- Patch extraction from RD map  
- Classification of each detection  
- Bounding box visualization  
- Output JSON (range, doppler, label, confidence)

### **Part 4 — Deployment Design (PDF included)**
- Real-time radar pipeline  
- Preprocessing & noise filtering  
- Detection → Classification flow  
- Limitations & improvements  
---

## 📁 Repository Structure

MMWave-Radar-AI-Project/
│
├── Part1_Radar_Simulation/
│   └── radar_simulation.ipynb
│
├── Part2_Classification/
│   └── classification_model.ipynb
│
├── Part3_Hidden_Object/
│   └── hidden_object_detection.ipynb
│
├── models/
│   └── cnn_model.h5        # small model (safe)
│
├── data/
│   └── (synthetic radar data / generated)—if any
│
├── deployment_design.pdf   # 1-page system design
├── output.png              # RD heatmap with detections
├── results.json            # detector output
├── README.md
└── .gitignore

> ⚠️ Note:  
> The large SVM model & `.venv` environment are intentionally excluded because they exceed GitHub’s 100 MB file limit.

---

## 🚀 How to Run

### **1. Create virtual environment**
```bash
python3 -m venv venv
source venv/bin/activate    # macOS / Linux
venv\Scripts\activate       # Windows

 Install dependencies
 pip install -r requirements.txt

 Open notebooks in VS Code or Jupyter

Run these in order:
	1.	Part1_Radar_Simulation/radar_simulation.ipynb
	2.	Part2_Classification/classification_model.ipynb
	3.	Part3_Hidden_Object/hidden_object_detection.ipynb

Each notebook is self-contained and generates its own outputs.

🧠 Key Features

✔ Synthetic Radar Simulation

A radar-like signal generator to create range–Doppler frames and clutter.

✔ Heatmap Processing

FFT → magnitude → log power → heatmap visualization.

✔ Hidden Object Detection
	•	Background subtraction
	•	Noise filtering
	•	CFAR-style region detection
	•	Bounding box extraction
	•	CNN-based classification

✔ Output JSON (Sample)
[
  {
    "label": "metal",
    "prob": 0.50,
    "range_start": 112,
    "range_stop": 119,
    "doppler_start": 10,
    "doppler_stop": 25
  }
]
✔ Deployment-Ready Design

Includes real-time pipeline & optimization suggestions.

⸻

📌 Limitations
	•	Fully synthetic radar data (no real mmWave sensor used)
	•	SVM baseline model removed due to size (>450 MB)
	•	Real-time deployment requires model quantization & stream optimization
	•	CNN trained on synthetic samples may need domain adaptation for real radar

⸻

🔮 Future Improvements
	•	Integrate real sensor captures (Infineon / TI radar)
	•	Use Kalman/track filters for multi-frame tracking
	•	Train smaller models (MobileNet / TinyCNN)
	•	Replace CFAR with YOLO-style detection on RD frames
	•	Add noise-robust data augmentation

⸻

📞 Contact

Ojas Bodke
Final Year — B.Tech AI & ML
Symbiosis Institute of Technology
