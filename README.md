# 🛠️  Anomaly Detection for Quality Assurance  
*An OpenCV-based pipeline for detecting manufacturing defects in printed circuit boards*

## 📋 Introduction  
Anomaly detection in manufacturing processes is critical for ensuring product quality, especially in industries like electronics where defects can lead to significant failures. 

This project focuses on identifying anomalies in PCB images using a limited dataset of reference and defective images.  By comparing test images against known defect-free "golden" references, discrepancies can be highlighted and analyzed. This approach is particularly effective when deep learning models are not feasible due to data constraints or computational limitations.  

---

## 📂 Understanding the Data  
The dataset consists of:  
- **10 golden images** as reference  
- **3 folders (PCB1, PCB2, PCB3)** with 6 images each  

To analyze the data:  
- **Duplicate Detection**: Visualized whether images were duplicates by overlaying them (assigning one image to the green channel and the other to the blue channel). The yellow overlap confirmed significant similarity between images.  

---

## 🛠️ Data Preprocessing  
The images are high-quality PCBs in black and white. The preprocessing steps include:  
- Reading images in **grayscale**  
- **Binarization** for further analysis  

Special care was taken during binarization to preserve critical details, as improper binarization can lead to information loss and affect results.  

---

## 🚀 Modeling the Approach  
The approach leverages basic image processing techniques:  
1. **Image Matching**:  
   - Employed two algorithms: **SIFT** and **ORB** 
2. **Feature Extraction**:  
3. **Image Subtraction and Contour Detection** 

---

## 🔍 Anomaly Detection Pipeline  
The pipeline works with grayscale images to retain maximum information:  
1. **Alignment**:  
   - Align the defective image to the original using ORB for feature detection and matching.  
2. **Homography Matrix**:  
   - Compute a homography matrix to warp the defective image, ensuring perfect alignment with the original.  
3. **Difference Calculation**:  
   - Compute the absolute difference between the aligned defective image and the original to highlight regions of discrepancy.  
4. **Contour Detection**:  
   - Detect contours on the thresholded difference image to identify the boundaries of anomalous regions.  

---

## 📊 Results  
Results and code provided in the attached Jupyter notebook.  

---

## ⚠️ Limitations  
1. **Dependency on Reference Images**:  
   - The algorithm requires a reference image and fails in its absence.  
2. **Sensitivity to Noise**:  
   - Threshold-based approaches are sensitive to noisy data. Deep learning-based feature extractors could provide more robust solutions.  
3. **Binarization Challenges**:  
   - Incorrect binarization can lead to information loss, causing false positives and negatives.  

---

## 🔄 Alternative Approaches  
Due to time constraints, the following alternatives were not explored:  
1. **Deep Learning-Based Feature Extraction**:  
   - Transfer learning approaches could enhance feature extraction.  
2. **Synthetic Data Generation**:  
   - Using online simulators [1] to generate synthetic PCB data could expand the dataset. Multi-cropping strategies and augmentations could be applied to high-resolution (1000×1000) images for synthetic board generation using diffusion models.   
