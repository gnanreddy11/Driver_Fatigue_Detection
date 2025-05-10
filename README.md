# EEG-Based Driver Fatigue Detection

This project focuses on detecting driver fatigue using brainwave signals (EEG) and reaction times. It uses machine learning techniques to classify the driver's mental state into three categories: **Low**, **Medium**, or **High Fatigue**. The entire system is built on real experimental data and includes signal processing, feature extraction, and a predictive model — making it a complete end-to-end pipeline for fatigue detection.

---

## 🧠 What is EEG and Why Fatigue Detection?

**EEG (Electroencephalography)** records the electrical activity of the brain through sensors placed on the scalp. Fatigue changes how our brain behaves, especially in how active certain regions are. This change is reflected in brain waves (like Alpha, Beta, Theta, and Delta), and we can capture it with EEG.

**Fatigue while driving** is dangerous. It reduces attention, slows down reactions, and increases accident risk. Detecting fatigue *before* it reaches a dangerous level can save lives. This project aims to build a system that does exactly that.

---

## 🚗 Project Summary

- **Dataset**: EEG recordings from 27 drivers in a virtual reality driving simulator.
- **Data Collected**: 32 brainwave channels, reaction times, lane departure events.
- **Goal**: Classify driver fatigue in real-time using brain activity and behavior.
- **Method**: Machine learning (Gradient Boosting) on extracted EEG features.
- **Accuracy**: 95% overall prediction success.
- **Interface**: Real-time dashboard showing current fatigue level.

---

## 🔍 Step-by-Step Breakdown

### 1. Data Collection
- 27 participants drove in a VR-based highway simulator for 90 minutes.
- Sudden lane drifts were introduced to simulate real-life drowsy challenges.
- EEG data was recorded using a 32-electrode cap.
- Events like drift-start, response-start, and response-end were logged.

### 2. Signal Preprocessing
- EEG signals are noisy, so we cleaned them using filters:
  - Removed electrical noise
  - Isolated brainwave frequency bands (0.5–30 Hz)
- Reaction time was calculated from event markers (e.g., time to correct a lane drift).

### 3. Feature Extraction
We extracted **band power** from EEG signals:
- **Alpha waves (8–13 Hz)**: Linked with relaxation → increased during fatigue.
- **Theta waves (4–7 Hz)**: Associated with drowsiness → strong fatigue marker.
- **Beta waves (13–30 Hz)**: Active thinking → decreases with tiredness.
- **Delta waves (0.5–4 Hz)**: Deep sleep signals → may emerge in high fatigue.

Also used:
- Normalized reaction times (left and right hand)
- Statistical features like average power per channel

### 4. Fatigue Classification
- **Three classes**: 
  - 0: Low (Alert)
  - 1: Medium (Getting tired)
  - 2: High (Dangerous fatigue)
- **Model**: Gradient Boosting Classifier
- Used features from all channels + reaction time as input
- Evaluated using cross-validation and confusion matrix

### 5. Real-time Interface
- Fatigue is continuously predicted every few seconds
- Dashboard displays:
  - Current fatigue state
  - History graph
  - Warnings if fatigue crosses threshold

---

## 📂 Folder Structure

```
Driver_Fatigue_Detection/
├── notebook/                 # Main code in Jupyter notebook format
├── reports/                  # Report, slides, and research paper
├── media/                    # Graphs and screenshots
├── requirements.txt          # Required Python libraries
├── LICENSE                   # MIT license for open-source use
└── README.md                 # Project overview
```

---

## 🧪 Results

- **Accuracy**: 95%
- **Precision**: 97%
- **Recall**: 93%
- **Confusion Matrix**:

```
[[ 4 0 0]
 [ 0 4 1]
 [ 0 0 10]]
```

---

## 📊 Visual Insights

| Real-Time UI | Feature Importance |
|--------------|--------------------|
| ![UI](media/fatigue_ui_real_time.png) | ![Importance](media/feature_importance_fatigue.png) |

---

## 💡 Technologies Used

| Category | Tools |
|----------|-------|
| Data Handling | NumPy, Pandas |
| Signal Processing | MNE, SciPy |
| Visualization | Matplotlib, Seaborn |
| Machine Learning | Scikit-learn (Gradient Boosting) |
| Interface | Dashboard using Python-based plotting |
| Deployment (Future) | Streamlit or Flask |

---

## 📘 Reports

- [Final Report (PDF)](Reports/Final_Report.pdf)
- [Project Presentation (PDF)](Reports/Project_Presentation.pdf)
- [Original Research Paper](Reports/Reference_Paper.pdf)

---

## 📝 License

This project is licensed under the [MIT License](LICENSE). Free to use and modify with credit.
