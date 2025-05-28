

# **Next-Generation Audio Deepfake Detection Pipeline Using AI**

## **Project Overview**
This repository contains my implementation of the **Next-Generation Audio Deepfake Detection Pipeline Using AI**. The goal of this project is to research, implement, and analyze robust systems for detecting tampered audio. I leveraged state-of-the-art models and preprocessing techniques to build a practical and efficient solution based on the **ResNet-Based Spectrogram Analysis** approach.

---

## **Contents**
- [Overview](#project-overview)
- [Approach](#approach)
- [Implementation](#implementation)
- [Evaluation Metrics](#evaluation-metrics)
- [Setup Instructions](#setup-instructions)
- [Future Work Roadmap](#future-work-roadmap)

---

## **Approach**

### **Selected Models**
After reviewing existing research and the [Audio Deepfake Detection Repository](https://github.com/media-sec-lab/Audio-Deepfake-Detection), the following approaches were identified:
1. **ResNet-Based Spectrogram Analysis**
    - **Key Innovation**: Adapts computer vision CNNs for spectrogram analysis.
    - **Performance**: 98.2% accuracy on ASVspoof 2019.
    - **Strengths**:
        - Captures local artifacts in generated audio.
        - Computationally efficient for near real-time.
    - **Limitations**:
        - May struggle with unseen synthesis methods.
        - Requires careful spectrogram parameter tuning.
2. **Wav2Vec 2.0 Fine-Tuning**
    - **Key Innovation**: Self-supervised speech representations for linguistic artifact detection.
    - **Performance**: 96.8% accuracy on In-the-Wild dataset.
    - **Strengths**:
        - Captures subtle linguistic patterns.
        - Reduces data requirements via transfer learning.
    - **Limitations**:
        - Computationally intensive.
        - Larger model size affects deployment.
3. **LSTM-Based Temporal Analysis**
    - **Key Innovation**: Models long-range temporal dependencies.
    - **Performance**: 94.5% accuracy on WaveFake dataset.
    - **Strengths**:
        - Effective for conversational contexts.
        - Lightweight compared to transformer-based methods.
    - **Limitations**:
        - Struggles with very short audio clips.
        - Sequential processing limits parallelism.

---

## **Implementation**

### **Selected Approach**
**ResNet-Based Spectrogram Analysis** was chosen due to its balance of performance and computational efficiency. Key aspects include:
- **Dataset**: CMFD (Chinese-English Fake Detection), containing 1,800 real and 1,000 fake samples.
- **Feature Extraction**:
    - Mel spectrograms with 128 bands.
    - Fixed window length of 2 seconds.
    - Resampling to 16kHz.
- **Architecture**:
    - Adaptation of ResNet-18 for binary classification (tampered vs. untampered).
    - Fine-tuning with early stopping.
    - 

---

### **Performance**
| Metric            | Value       |
|--------------------|-------------|
| **Accuracy**       | 92.3%       |
| **Precision**      | 91.8%       |
| **Recall**         | 93.1%       |
| **F1 Score**       | 92.4%       |
| **Inference Speed**| 43 FPS      |

---

## **Evaluation Metrics**

### **Strengths**
- Fast inference suitable for real-time applications.
- Robust against small variations in input.
- Easy to debug and interpret.

### **Weaknesses**
- Performance drops on very short clips (<1 second).
- False positives on low-quality real audio.

---

## **Setup Instructions**

### **Prerequisites**
1. **Clone the Repository**
    ```bash
    git clone https://github.com/DANUSHMATHI2002/Momenta_Task.git
    cd Momenta_Task

    ```
2. **Install Dependencies**
    ```bash
    pip install -r requirements.txt
    ```

## **Dataset**
- The dataset used for this project is the **CMFD (Chinese-English Fake Detection)** dataset.
- It contains `.flac` audio files of real and tampered human speech in both English and Chinese.
- You can download the dataset directly from the following GitHub repository:  
  [CMFD Dataset Repository](https://github.com/WuQinfang/CMFD)

### **Steps to Use the Dataset**
1. Visit the dataset repository and download the ZIP file containing the audio files.
2. Place the ZIP file in the root directory of this project.
3. Run the provided preprocessing script to extract and organize the data for training and testing:
    ```bash
    python preprocess_data.py
    ```

---

### **Run Training**
1. Open the `Implementation.ipynb` file.
2. Execute cells to train the model on the CMFD dataset.

### **Run Testing**
1. Ensure the `test_files` are organized.
2. Evaluate the model using the provided `test_model()` function.

---

## **Future Work Roadmap**
1. Incorporate temporal modeling for sequential data.
2. Evaluate model performance on multilingual datasets.
3. Build a browser-based demo for visualization.
4. Optimize for edge deployment with low-latency inference.
5. Conduct adversarial robustness testing against advanced tampered audio methods.

---

## **Reflection**

### **Challenges & Solutions**
1. **Data Imbalance**: Implemented class weighting during training.
2. **Variable Length Audio**: Used fixed-length cropping for spectrogram consistency.
3. **Overfitting**: Added dropout layers and applied data augmentation.

### **Future Improvements**
1. Ensemble models combining ResNet with temporal analysis methods.
2. Add attention mechanisms for better context representation.
3. Experiment with phase information in spectrogram features.

---

## **Contact**
For questions or feedback, feel free to reach out: **DANUSHMATHI P**

---
