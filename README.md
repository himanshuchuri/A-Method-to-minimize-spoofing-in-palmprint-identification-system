# A-Method-to-minimize-spoofing-in-palmprint-identification-system

## Dataset:
The IIT Delhi palmprint image database consists of the hand images collected from the students and staff at IIT Delhi, New Delhi, India. This database was acquired in the IIT Delhi campus from July 2006 - Jun 2007 using a simple and touchless imaging setup. All the images are collected in the indoor environment and employ circular fluorescent illumination around the camera lens. The currently available database is from 230 users, all the images are in bitmap (*.bmp) format. All the subjects in the database are in the age group 12-57 years. Seven images from each subject, from each of the left and right hands, are acquired in varying hand pose variations. Each of the subjects is provided with live feedback to present his/her hand in the imaging region. Touchless imaging results in higher image scale variations. The acquired images have been sequentially numbered for every user with an integer identification/number. The resolution of these images is 800 ´ 600 pixels.


## Abstract:
Region of interest (ROI) derived palmprint images have higher entropy and require less processing and storage, they considerably improve the effectiveness of identification systems. Using image processing methods like dynamic thresholding for binarization, centroid determination, boundary extraction using morphological operations, Euclidean distance calculations from the centroid, valley point determination after smoothing the Euclidean distance plot, and from which the ROI is ultimately extracted, the technique used here calculates distances between points using geometry. Using this technique, ROIs for the datasets of sizes 128 x 128 and 256 x 256 have been extracted.

## Introduction:
Biometric systems are a helpful feature for authenticating and differentiating people from other people. Its primary characteristics or properties, which include universality, distinctiveness, permanence, and collectability, make it a potent biometric for recognition. These make sure that the feature is present in everyone, that it has enough variation, and that it does not change drastically over time. The issue about these traits is acceptability, performance, and risk of circumvention.


## Significance of my work:
This technique of applying Discrete Wavelet Transform (DWT) followed by Discrete Cosine Transform (DCT) on image patches can help in creating features that capture different aspects of the image's spatial and spectral information, useful for various image processing and analysis tasks. Here's a breakdown of what each step contributes to feature extraction:

* Discrete Wavelet Transform (DWT):

  DWT decomposes the image into sub-bands representing different frequency ranges and spatial locations.
  The 'db1' wavelet used here is a good starting point for capturing both horizontal and vertical image structures.
  The resulting sub-bands are:
  1. LL (low-low): This sub-band contains the approximation coefficients, representing the overall image with reduced spatial resolution but preserving low-frequency information.
  2. LH (low-high): This sub-band captures horizontal details at a higher frequency compared to LL.
  3. HL (high-low): This sub-band captures vertical details at a higher frequency.
  4. HH (high-high): This sub-band captures diagonal details and high-frequency information.

* Splitting Sub-bands into Patches (split_img):

Splitting the sub-bands (LL, LH, HL, HH) into smaller non-overlapping patches allows for localized feature extraction.
By applying split_img, you can analyze the image content within smaller regions, potentially capturing local variations in texture, edges, and other spatial patterns.

* Discrete Cosine Transform (DCT) on Patches:

DCT transforms the pixel intensities within each patch into the frequency domain.
The DCT coefficients represent the importance of different spatial frequencies in reconstructing the patch.
Low-frequency coefficients capture the overall intensity variations within the patch, while high-frequency coefficients capture finer details and textures.

* Overall, this technique helps create features that capture:

Spatial information: DWT separates the image into sub-bands with localized frequency information. Splitting these sub-bands further refines the spatial resolution of the features.
Spectral information: DCT applied to each patch captures the distribution of spatial frequencies within that local region.

Principal Component Analysis (PCA), explained covariance ratio and singular values play crucial roles in understanding the dimensionality reduction process and the importance of the retained components.

