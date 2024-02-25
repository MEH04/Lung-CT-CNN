# Lung-CT-CNN
## Background: 
Lung cancer occurs in four main types: Adenocarcinoma (A), Small Cell Carcinoma (B), Large Cell Carcinoma (E), Squamous Cell Carcinoma (G). We have found a dataset of size N = 355 of patients diagnosed with one of these four types of cancer. The dataset has a non-uniform distribution of cancer types, primarily type A. An CT scan builds a 3D lung re-construction for each patient (DICOM file type), which is labelled by cancer type. We aim to build a convolutional neural network to predict the type of cancer in the image; initially using 2D plane slices of the image, but potentially extending to 3D images.  
## Plan 
1. Understand the DICOM file format of the images. Write a programme to automate extraction of 2D images from the 3D CT scan of each patient using the pyDICOM library.  
2. Make resolution and dimension uniform for analysis and synthesise new data through SMOTE (data processing) so that each type of cancer has equal data number (preventing bias towards one type).  
3. Analyse and process data to understand the types of cancer present in dataset. Decide which 2D plane-cut provides the most distinction. Dunn and Liu use the central-most transverse plane of the lung. The same plane will be used for each patient to maintain consistency. 
4. Research different CNN models that have been used for lung cancer prediction and figure out an approach of how we can tailor existing models to fit our own dataset. Most models simply predict whether a patient is cancer-positive, so significant adaption / writing from scratch may be required to instead distinguish between the four types of cancer.   
5. After writing the code, train the neural network on a small subset of our data – observe success rate and tweak parameters. Can then extend this to the entire dataset – hiring use of the Imperial HPC.  
6. Visualise and assess performance of neural network on 2D images. Compare performance of neural network to other models including the primary clinical study. 
7. If the 2D neural network is successful, we will write a new model to analyse 3D CT images. The strategy will be to use many 2D slices to produce a 3D rendering of the image. We would need to process the data to be able to generate a certain resolution of the 3D image. Then we would need to preprocess the data and train a CNN created in Pytorch as usual.  
## References: 
[Dataset: Large-Scale CT and PET/CT Dataset for Lung Cancer Diagnosis (Lung-PET-CT-Dx)](https://wiki.cancerimagingarchive.net/pages/viewpage.action?pageId=70224216#7022421689b3111c3e594e78910f8c8317813f35)
[A paper analysing the same dataset with CNNs](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10295141/)
[A step-by-step guide to writing a CNN to diagnose lung cancer](https://www.geeksforgeeks.org/lung-cancer-detection-using-convolutional-neural-network-cnn/)
[Data Augmentation to balance the dataset](https://machinelearningmastery.com/smote-oversampling-for-imbalanced-classification/)
[Writing a 3D neural network for medical image classification](https://pythonprogramming.net/3d-convolutional-neural-network-machine-learning-tutorial/)
