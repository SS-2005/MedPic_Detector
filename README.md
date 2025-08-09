# MedPic_Detector :

A advanced built in web-scraper that will extract iamges from a pdf or URL and predict the extracted image is a "Medical" Image or not

# Steps:
1) Open  "Main.ipynb"
2) Upload model "/model/best_model.h5" into colab
3) Run each cell sequentially
4) Choose mode (1-URL,2-PDF)
5) Enter and a personalized result csv will be generated with a confidence score

# Evaluation 

* For detailed model evalution view "MedicallimagePredictor.ipynb" : It contains classfication reports,Confusion metrics and ROC as well 
* For detailed feature of extration view "ImageExtractor.ipynb"
* Most of the fuctions are self explanatory yet i have added comments for your refrence

# Dataset:

I have manually created the dataset "dataset.zip"

its structure is as follows:

```
dataset/
  |__medical/- Contains all medical images
  |__non-medical/- Contains all non-medical images
```

