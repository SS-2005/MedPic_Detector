# MedPic_Detector :


---
## Overview

This project provides a comprehensive solution for classifying images as medical or non-medical. The system can extract images from URLs or PDFs and classify them using a deep learning model trained on a dataset of approximately 10,000 images (sample). The classifier achieves 90% accuracy with 86% precision for non-medical images and 95% precision for medical images.

Note:` I have added video demonstration for the same in the GitHub`

---
## Steps:
1) Open  "Main.ipynb"
2) Upload model "/model/best_model.h5" into colab
3) Run each cell sequentially
4) Choose mode (1-URL,2-PDF)
5) Enter and a personalized result csv will be generated with a confidence score

---
## Evaluation 

* For detailed model evalution view "MedicallimagePredictor.ipynb" : It contains classfication reports,Confusion metrics and ROC as well 
* For detailed feature of extration view "ImageExtractor.ipynb"
* Most of the fuctions are self explanatory yet i have added comments for your refrence
* Performance Metrics is as follows

|Metric |	Non-Medical	| Medical	| Overall |
|----------|-------------|----------|----------|
|Precision	|0.86|	0.95|	0.91|
|Recall	|0.96	|0.83	|0.90|
|F1-Score	|0.91	|0.89	|0.90|
|Support	|5652	|5155	|10807|

---
## Key Features

* Image Extraction: Extract images from websites and PDF documents

* Medical Classification: Classify images as medical or non-medical

* Confidence Scoring: Provides confidence levels for predictions

* Result Export: Save classification results as CSV files

* Medical Image Export: Download high-confidence medical images from PDFs

* Robust Error Handling: Graceful degradation for corrupted images and model loading issues

---
## System Architecture
```
Input (URL/PDF) → Image Extraction → Preprocessing → Classification → Results
                     │                         │
                     └─> Error Handling        └─> Fallback Mechanisms
```

---
## Model Details

* Architecture
  
  * Base Model: EfficientNetB3
  
  * Custom Layers:
  
    * Global Average Pooling
  
    * Dropout (0.4)
    
    * Dense layer with sigmoid activation
      
  * Input Size: 224x224 pixels
  
  * Output: Binary classification (medical/non-medical)

* Training
  
  * Dataset: ~6k non-medical images + ~6k medical images
  
  * Augmentation: Rotation, shifting, shearing, zooming, flipping
  
  * Class Balancing: SMOTE oversampling
  
  * Optimizer: Adam (learning rate 1e-3)
  
  * Callbacks: Early stopping, learning rate reduction, model checkpointing


* Performance Considerations

  * Classification Speed: 0.5-1 second per image on CPU
  
  * Memory Usage: Optimized for Colab's memory constraints
  
  * Error Handling: Skips corrupted images and provides fallback models
  
  * Scalability: Processes large PDFs and websites with multiple images


---
## File Structure:

```
project-root/
├── best_model.h5                  # Trained classification model
├── extracted_images/              # Temporary storage for extracted images
├── medical_images/                # Storage for high-confidence medical images
├── url_classification_results.csv # Classification results from URL processing
└── pdf_classification_results.csv # Classification results from PDF processing
```

---
## Dataset:

I have manually created the dataset

Link to dataset: https://drive.google.com/drive/folders/1fPf2rrXj1qtcPeXwjCJzy1MMykB1-E-f?usp=sharing

its structure is as follows:

```
dataset/
  |__medical/- Contains all medical images
  |__non-medical/- Contains all non-medical images
```

---
## Troubleshooting
* Model Loading Issues:

Ensure best_model.h5 is uploaded before running

The system will use a fallback model if loading fails

* Image Extraction Problems:

Try different URLs if extraction fails

Some websites block scraping - try medical sites like radiopaedia.org

* Memory Errors:

Use Colab's "Restart and run all" option

Reduce batch size in the code (change BATCH_SIZE variable)

Use smaller images (modify IMG_SIZE)
