# Activity Classification of Elderly Using MATLAB and Wearable Sensor Data

This repository contains the MATLAB code and analysis developed for the project:

📄 **"Activity Classification with MATLAB"**  
👤 *Heiner Castro Gutierrez*  
🎓 Based on motion data from healthy older adults using passive, batteryless wearable sensors

---

## 📦 Repository Structure
├── Codes/                     # MATLAB scripts for classification models
│   ├── Bagged_Trees.m
│   ├── Boosted_trees.m
│   ├── Gaussian_SVM.m
│   ├── Linear_SVM.m
│   ├── LogisticRegression.m
│   ├── NaiveBayes.m
│   ├── Neural_Network.m
│   ├── Quadratic_SVM.m
│   └── Tree_Classifier.m
├── Figures_and_tables/       # All figures and tables referenced in the project report
├── Project.pdf                # Final project report describing methodology and results
└── README.md

---

## 🧪 Project Overview

The project focuses on classifying physical activities of older adults using motion data collected from **battery-less RFID-based wearable sensors** placed on the sternum. Activities include:

- **W**: Walking  
- **GC**: Getting out of a chair  
- **Ly**: Lying on a bed  
- **GB**: Getting back on a bed

The objective is to build a robust **multi-class classifier** that can distinguish these activities using a limited set of features and varying environments.

---

## 🧬 Dataset Summary

- Source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/)
- Subjects: 14 healthy older adults (ages 66–86)
- Input features:  
  - Acceleration in frontal, lateral, and vertical axes  
  - Gender (from filename metadata)  
- Discarded: Time, antenna ID, signal strength, phase, frequency (to reduce room-dependence)
- Final feature count: **4 features + 1 label**

Room setup:
- One environment used for training, the other for testing — mimicking real-world generalization

---

## 🤖 Implemented Models (in `/Codes`)

| Model               | Script               | Notes                                        |
|--------------------|----------------------|----------------------------------------------|
| Decision Tree       | `Tree_Classifier.m`   | Gini-based split, baseline model             |
| Naïve Bayes         | `NaiveBayes.m`        | Leverages independence of acceleration axes  |
| Logistic Regression | `LogisticRegression.m`| Classical linear classifier                   |
| Neural Network      | `Neural_Network.m`    | Simple feedforward network (MATLAB toolbox)  |
| Support Vector Machines | `Linear_SVM.m`, `Quadratic_SVM.m`, `Gaussian_SVM.m` | Kernel variants tested |
| Ensemble Methods    | `Bagged_Trees.m`, `Boosted_trees.m` | AdaBoost used with Decision Trees           |

All scripts implement **5-fold cross-validation** for validation and **cross-room evaluation** for real-world generalization.

---

## 📊 Performance Summary

| Method         | Validation Accuracy | Test Accuracy |
|----------------|---------------------|---------------|
| Decision Tree (3 splits) | 96.8%             | 90.0%         |
| AdaBoost (12 splits, 5 learners) | 97.2% | 90.2%         |
| **Naïve Bayes**        | 97.1%             | **92.5%**     |

> ✅ Naïve Bayes yielded the **highest accuracy** and best classification of difficult classes (GC and W)

---

## 📉 Limitations

- **GC** and **W** are often confused, even in the best classifiers  
- Only four features were used — future improvements may include signal strength or phase  
- Neural networks and SVMs were tested but not reported in detail in the PDF

---

## 📎 Figures and Tables

The folder `Figures_and_tables/` contains:
- All histograms, confusion matrices, and performance tables
- Referenced in the final report (`Project.pdf`)

---

## 🧠 Citation

If you use this dataset, please cite the original source: 
Shinmoto Torres, R. et al. (2016). Effectiveness of a Batteryless and Wireless Wearable Sensor System for Identifying Bed and Chair Exits in Healthy Older People. Sensors, 16(4), 546.

And/or cite this project repository as appropriate.

---

## 📝 License

MIT License. See `LICENSE` file.
