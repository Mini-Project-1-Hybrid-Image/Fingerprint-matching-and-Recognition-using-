# Methodology
The fingerprint recognition algorithm employed in this project consists of two main parts:
![image](https://github.com/Mini-Project-1-Hybrid-Image/Fingerprint-matching-and-Recognition-using-/assets/49596777/a2c4cee9-1d95-416d-b060-eb5789d28ea0)



# Preprocessing Step
Feature Extraction, Matching, and Recognition

# Preprocessing Step
The preprocessing step is essential for enhancing image quality and ensuring the effectiveness of subsequent fingerprint recognition steps. Several preprocessing techniques are applied:

Image Normalization:

Normalize the image by subtracting the mean and dividing by the standard deviation to reduce gray level variance and minimize unwanted effects such as illumination.

Image Segmentation (Ridge Segment):

Divide the image into blocks and calculate the standard deviation (STD) for each block. Based on a predefined threshold, determine whether each block contains useful parts of the fingerprint or background information. This segmentation helps reduce the image size and optimize the algorithm.

Directional Map: 

Generate a directional map to define the orientation of the fingerprint ridges. This map is crucial for generating frequency maps and performing Gabor filtering. The orientation estimation involves computing gradients, estimating local direction, and obtaining sines and cosines of doubled angles. Smoothing the directional map is achieved using a low-pass filter.

Frequency Map: 

Estimate the local frequency of the fingerprint ridges in each pixel. Calculate the frequency by analyzing the period between two 

successive extrema. This step involves block frequency calculation, mean orientation estimation, ridge frequency calculation, and frequency masking.

Gabor Filter: 

Use a Gabor filter with even symmetry oriented at 0 degrees to select the set of frequencies that represent the fingerprint region.

Filters corresponding to distinct frequencies and orientations are generated. Rotation and filtering operations are performed to find ridges in the image.

![image](https://github.com/Mini-Project-1-Hybrid-Image/Fingerprint-matching-and-Recognition-using-/assets/49596777/252aac34-5898-40f0-b4a2-dd7958307cd5)


# Feature Extraction, Matching, and Recognition

![image](https://github.com/Mini-Project-1-Hybrid-Image/Fingerprint-matching-and-Recognition-using-/assets/49596777/e14de6cd-e847-4e26-90b9-31052a3459cd)

After the preprocessing and enhancement steps, the fingerprint features are extracted and matched for recognition.

SIFT Feature Extraction:

Utilize the Scale Invariant Feature Transformation (SIFT) algorithm to extract key points from each image. Unique descriptors are 

obtained for each image, and they are appended to a list for subsequent steps.

![image](https://github.com/Mini-Project-1-Hybrid-Image/Fingerprint-matching-and-Recognition-using-/assets/49596777/0f76bfd2-78cc-4c42-af03-25bd1ea98fcd)


Build Vocabulary: 

Create a vocabulary of visual words using the extracted SIFT descriptors. Apply k-means clustering to obtain cluster centers as the vocabulary.

Bag of Words:

Count the number of descriptors falling within each cluster to create histograms for each image. The closest vocabulary word (cluster) is 

determined using Euclidean distance.

# SVM Model Classification: 

Train an SVM model using the LinearSVC algorithm from sklearn.svm. The model is used to predict categories for test images based on their feature histograms.

# Results
The implemented fingerprint recognition system achieved an accuracy of 81.25%. However, further improvements could be made by removing false key points from
