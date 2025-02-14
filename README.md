# CV-Projects 🚀  
My collection of projects focused on training and improving machine learning skills in object detection, segmentation, and retrieval tasks.

---

## 📋 Table of Contents  
1. [1st Project: Fine-tuning DETR on Balloon Dataset 🎈](#-1st-project-fine-tuning-detr-on-balloon-dataset-)  
   - [Project Overview 📚](#project-overview-📚)  
   - [Methodology 🛠️](#methodology-🛠️)  
   - [Training Details 💻](#training-details-💻)  
   - [Tools and Frameworks 🛠️](#tools-and-frameworks-🛠️)  
   - [Results 📈](#results-📈)  
   - [Future Improvements 🚀](#future-improvements-🚀)  
   - [Conclusion 🎯](#conclusion-🎯)  
   
2. [2nd Project: Object Retrieval with SAM and CLIP 🔍🎨](#-2nd-project-object-retrieval-with-sam-and-clip-)  
   - [Project Overview 📚](#project-overview-📚-1)  
   - [Methodology 🛠️](#methodology-🛠️-1)  
   - [Prompt Sensitivity Analysis ✏️](#prompt-sensitivity-analysis-✏️)  
   - [Challenging Cases ⚠️](#challenging-cases-⚠️)  
   - [Proposed Improvements 🚀✨](#proposed-improvements-🚀✨)  
   - [Conclusion 🎯](#conclusion-🎯-1)  

---

# 👾 1st Project: Fine-tuning DETR on Balloon Dataset 🎈  

## Project Overview 📚  
This project involves fine-tuning the **DETR (DEtection TRansformer)** model to detect balloon objects in images using the **Balloon dataset**. The main objective was to optimize DETR for balloon detection by leveraging data augmentation and analyzing its impact on performance.  

---

## Methodology 🛠️  

### 1. Dataset Preparation 🗂️  
- **Dataset:** The Balloon dataset with image-annotation pairs.  
- **Splitting:** Training (70%), Validation (15%), and Test (15%).  
- **Annotation Conversion:** Custom annotations converted to COCO format for compatibility.  

### 2. Model: DETR (DEtection TRansformer) 🤖  
- **Backbone:** ResNet for feature extraction.  
- **Transformer:** Processes image features and predicts object locations.  
- **Loss:** Bipartite matching using the Hungarian algorithm.  

### 3. Fine-Tuning Strategy 🏋️‍♂️  
- **Pretrained Weights:** Initialized from the COCO dataset.  
- **Data Augmentation:** Applied techniques such as flipping, scaling, and color adjustments.  
- **Training:** Implemented using PyTorch Lightning.  

---

## Training Details 💻  
- **Hardware:** Google Colab with GPU support.  
- **Batch Size:** 4  
- **Epochs:** 5–15 (optimal at 6–10 epochs).  
- **Optimizer:** AdamW with a learning rate scheduler.  

---

## Tools and Frameworks 🛠️  
- **PyTorch + PyTorch Lightning** – Training and implementation.  
- **Albumentations** – Data augmentation.  
- **PyCOCO Tools** – COCO-style evaluation.  
- **Matplotlib & TensorBoard** – Visualization and logging.  

---

## Results 📈  
- **Average Precision (AP):** 78.9% at IoU=0.50.  
- **Data Augmentation Impact:** Improved performance and stability.  
  - Best results with `A.RandomBrightnessContrast` and `A.Resize(800, 800)`.  
  - Over-augmentation slowed convergence and increased losses.  

---

## Future Improvements 🚀  
1. **Dataset Expansion:** Use synthetic data generation.  
2. **Advanced Augmentation:** Explore techniques like CutMix and Mosaic.  
3. **Efficient Attention Mechanisms:** FlashAttention, Performer, or Linformer.  
4. **Better Localization:** Implement Conditional DETR.  

---

## Conclusion 🎯  
This project highlights the importance of data augmentation in training transformer-based models like DETR on small datasets. Augmentation significantly improved generalization and detection accuracy.  

---

# 👾 2nd Project: Object Retrieval with SAM and CLIP 🔍🎨  

## Project Overview 📚  
In this project, I used **Segment Anything Model (SAM)** and **CLIP** for object retrieval in images based on **textual prompts**. The goal was to segment objects (e.g., chairs) using SAM and match them to text prompts with CLIP.

---

## Methodology 🛠️  

### Main Workflow 🚀  
1. **Image Processing:** Convert images to RGB.  
2. **Mask Generation:** Use SAM to generate masks for objects.  
3. **True Mask Loading:** Load reference masks for evaluation.  
4. **Object Matching:** Match masks with the prompt "chair" using a threshold of 0.3.  
5. **Mask Combination:** Merge relevant masks into a single one.

---

## Prompt Sensitivity Analysis ✏️  
- **"chair" (IoU: 0.7164)** – Good results.  
- **"a photo of a chair" (IoU: 0.7298)** – Best result due to balanced detail.  
- **"a computer small chair" (IoU: 0.6358)** – Complex prompt reduces performance.  

---

## Challenging Cases ⚠️  
1. **Blended Objects:** Chairs blending into the background.  
2. **Low Contrast:** Poor lighting affects object boundaries.  

---

## Proposed Improvements 🚀✨  
1. **Prompt Tuning:** Balance prompts for better performance.  
2. **Image Preprocessing:** Use contrast enhancement and edge detection.  
3. **Hybrid Approaches:** Integrate depth sensing or metadata.  
4. **Advanced Models:** Explore GPT-4 for improved text understanding.  

---

## Conclusion 🎯  
This project demonstrates the power of combining SAM and CLIP for text-based object retrieval. Prompt engineering is crucial, and future improvements can enhance accuracy and robustness. 
