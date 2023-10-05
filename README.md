# 3D-MRI-Brain-tumor-segmentation
Brain tumor segmentation using U-Net
Dataset

1.1 What is an MRI?
Magnetic resonance imaging (MRI) is an advanced imaging technique that is used to observe a variety of diseases and parts of the body.

As we will see later, neural networks can analyze these images individually (as a radiologist would) or combine them into a single 3D volume to make predictions.

At a high level, MRI works by measuring the radio waves emitted by atoms subjected to a magnetic field.

1.2 MRI Data Processing
We often encounter MR images in the DICOM format.

The DICOM format is the output format for most commercial MRI scanners. This type of data can be processed using the pydicom Python library.
we will be using the data from the Decathlon 10 Challenge. This data has been mostly pre-processed for the competition participants, however in real practice, MRI data needs to be significantly pre-preprocessed before we can use it to train our models.


1.3 Exploring the Dataset
Our dataset is stored in the NifTI-1 format and we will be using the NiBabel library to interact with the files. Each training sample is composed of two separate files:

The first file is an image file containing a 4D array of MR image in the shape of (240, 240, 155, 4).

The first 3 dimensions are the X, Y, and Z values for each point in the 3D volume, which is commonly called a voxel.
The 4th dimension is the values for 4 different sequences
0: FLAIR: "Fluid Attenuated Inversion Recovery" (FLAIR)
1: T1w: "T1-weighted"
2: t1gd: "T1-weighted with gadolinium contrast enhancement" (T1-Gd)
3: T2w: "T2-weighted"
The second file in each training example is a label file containing a 3D array with the shape of (240, 240, 155).

The integer values in this array indicate the "label" for each voxel in the corresponding image files:
0: background
1: edema
2: non-enhancing tumor
3: enhancing tumor
We have access to a total of 484 training images which we will be splitting into a training (80%) and validation (20%) dataset.

Let's begin by looking at one single case and visualizing the data! You have access to 10 different cases via this notebook and we strongly encourage you to explore the data further on your own.

We'll use the NiBabel library to load the image and label for a case. The function is shown below to give you a sense of how it works.




# Image data descriptions

All BraTS multimodal scans are available as  NIfTI files (.nii.gz) -> commonly used medical imaging format to store brain imagin data obtained using MRI and describe different MRI settings 
1. **T1**: T1-weighted, native image, sagittal or axial 2D acquisitions, with 1–6 mm slice thickness.
2. **T1c**: T1-weighted, contrast-enhanced (Gadolinium) image, with 3D acquisition and 1 mm isotropic voxel size for most patients.
3. **T2**: T2-weighted image, axial 2D acquisition, with 2–6 mm slice thickness.
4. **FLAIR**: T2-weighted FLAIR image, axial, coronal, or sagittal 2D acquisitions, 2–6 mm slice thickness.

Data were acquired with different clinical protocols and various scanners from multiple (n=19) institutions.

All the imaging datasets have been segmented manually, by one to four raters, following the same annotation protocol, and their annotations were approved by experienced neuro-radiologists. Annotations comprise the GD-enhancing tumor (ET — label 4), the peritumoral edema (ED — label 2), and the necrotic and non-enhancing tumor core (NCR/NET — label 1), as described both in the BraTS 2012-2013 TMI paper and in the latest BraTS summarizing paper. The provided data are distributed after their pre-processing, i.e., co-registered to the same anatomical template, interpolated to the same resolution (1 mm^3) and skull-stripped.


### REFERENCES
[wiqaas/Deep_Learning_Using_Tensorflow/Image_Segmentation_using_U-Net](https://github.com/wiqaaas/youtube/blob/master/Deep_Learning_Using_Tensorflow/Image_Segmentation_using_U-Net/Image%20Segmentation%20using%20U-Net%20for%20MRI%20(3D%20Images).ipynb)

[kaggle](https://www.kaggle.com/code/rastislav/3d-mri-brain-tumor-segmentation-u-net#Load-data)
