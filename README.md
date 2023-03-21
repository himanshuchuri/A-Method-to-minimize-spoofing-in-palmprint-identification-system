# A-Method-to-minimize-spoofing-in-palmprint-identification-system


1. Our dataset consists of seven images of each of the 230 participants right and left hand while sampling a dataset consisting of only left hand of each participant.
2. Each of these images are displayed on
3. We printed these 115 of these images at random and then captured those using the same camera to simulate spoofed images captured from printed sheet.
4. The images were cropped manually to only contain the palm and then further to crop finger by considering the bottom 55% of the image and cropping 25% from the side.
 2560-by-1600, 227ppi screen with 500 nits of
 brightness and captured using a phone camera, 48MP quad pixel sensor (fuses 4 pixels
 into 1 to give output of 12MP), 24mm lens at aperture of 1.7 to generate the data of
 spoofed palm images captured from the screen.
5. A mask is generated with thresholds of 200,255 and combining THRESH_BINARY and THRESH_OTSU type. Also, a kernel of size 3x3 is initialized.
6. Gaussian blur is applied on the masks to reduce high frequency components with standard deviation in X and Y direction of 2.29.
7. Then the mask is normalized, and then morphological transformations are applied to remove any of the area that have passed into the mask that are not needed.
8. Using cv2. findContours contours are selected (which are the points with same intensity) and the one with the biggest area among these is selected.
9. An epsilon is calculated which is used in the approxpolyDP function to approximate the shape of the region. The epsilon is the perimeter with precision value of 10^(-31).
10. This approximated shape is passed in the Moments function to calculate the moments of the contour from the moments the center of the area is generated using x co- ordinate = M['m10'] // M['m00'] and y co-ordinate = M['m01'] // M['m00'].
11. A rectangle with these x and y points as center is selected as the region of interest and saved.
12. These saved ROI are loaded and using createCLAHE which normalized the histogram of the image, enhances the quality of image as resizing to size of 150-by-150.
13. Features such as 'mean', 'pixel_intensity_variance', '10th_percentile', '50th_percentile', '90th_percentile', 'skewness', 'kurtosis', 'median', 'mode' are extracted directly from the image.
14. 'contrast', 'correlation', 'energy', 'homogeneity', 'entropy' is extracted after calculating a gray level comatrix of 256 levels.
15. DWT is applied on the images and is split into 4 bands, ll,lh,hl,hh. These bands are then split into several sub-bands of 75-by-75 size and on each of them dct is applied followed by pca to get 2 variance ratio values and 2 singular values.
16. All the above values are inserted into a data frame.
17. So, the total number of features is 350.
18. The dataframes of all the three; original, spoofed-print and spoofed-display are merged
and shuffled. With the class values of original as 1 and spoofed as 0.
19. Only half of the spoofed-print and half of three spoofed-display data is selected at
random to avoid bias issues.
20. SVM is applied on the dataset after splitting data int train and test with ratio of 4:1 and
the test into test and validation with ratio of 7:3.
21. XGBoost is applied on the train data and with the model obtained the important
features were extracted and ROC curve was plotted.
22. Both the models were saved for further use.
