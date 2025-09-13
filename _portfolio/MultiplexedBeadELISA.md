---
title: "Multiplexed ELISA on a Bead Assays Software"
excerpt: "Software to expand the capabilities of fluorescent microscopy in single cell secretion assays using U-Net segmentation <br/><img src='/images/Image16.JPG'>"
collection: portfolio
---

Microscopy based multiplexed assays are an important tool for comparing stem cell
derived beta cells and donor beta cells through their secretion profiles. The limited fluorescent
range used by microscopes limits multiplexed assays to the detection of 3 to 4 four biomolecules.
This is because fluorescent labels emit a range of fluorescent wavelengths and overlapping
ranges lead to false detections. The proposed approach to overcome this limitation is to apply a
machine learning model to segment different bead sizes which contain different bioreceptors.
After biomolecules bind to the bioreceptors, they can be fluorescently labeled. The fluorescence
intensity of each biomolecule can then be calculated using the segmented masks of the different
bead sizes. Finally, the mean fluorescence intensities can be converted into concentrations for
each biomolecule using standard curves.

Pancreatic beta cells are pancreatic cells that secrete insulin – an important biomolecule
for body processes such as managing blood glucose levels through cellular glucose uptake. Type
1 Diabetes (T1D) is an autoimmune disease where pancreatic cells are destroyed by the immune
system, thus resulting in less insulin production. Current treatments include lifelong insulin injections,
and more recently, pancreatic beta cell transplants. Donor beta cells are in short supply and thus there is
a critical need for new beta cells sources. Recent research has focussed on the differentiation 
and genetic engineering of pluripotent stem cells into stem cell derived beta cells (SCβ) to be used as a new source for beta cell transplants. 

![alt text](/images/Image1.JPG)


Recently, nanowell technology and fluorescent microscopy was used to investigate
the heterogeneity of glucose stimulated insulin secretion (GSIS) for single pancreatic beta cells.
This study provided insight into the characteristics required of stem cell derived beta cells before
they can be used as a transplant treatment for Type 1 Diabetes. However, there is still a need for
better characterization of donor and SCβ cells regarding their insulin, glucagon, and somatostatin
hormone secretion levels. This will help in understanding if SCβ cells provide the same secretion
standards of donor cells, or if alternative methods such as secretion-based cell
selection if needed.

![alt text](/images/Image2.JPG)

Multiplexed single cell secretion assays can be used to profile donor and stem cell
derived islet cells through their secretion of insulin, glucagon, and somatostatin. This can be
done at the single cell level using nanowells to separate the cells and microscopy to image the
fluorescence of detection beads in each nanowell. These detection beads increase in fluorescence
intensity when the biomolecule of interest increases (e.g. insulin). However, multiplexed single
cell assays that employ microscopy are usually limited to detecting 3-4 different biomolecules. 
This is due to the limited fluorescence emission range and the fact that fluorophores attached to
the beads emit a range of fluorescent wavelengths. Generally, when conducting single cell
assays, two fluorescence stains are used to check if the cell is dead or alive. As a result, there is
not enough space on the fluorescence emission range for an additional three fluorophores for
insulin, glucagon, and somatostatin.

Previous research in increasing the multiplexing capability of microscopy mainly
focussed on decreasing the fluorescence emission ranges of fluorescent labels to minimize
overlap. Instead, it is proposed that different bead sizes can be used to detect different
biomolecules such as insulin, glucagon, and somatostatin, using the same fluorescent label.
Semantic segmentation can be applied to identify and categorize the beads in order to calculate
the fluorescent intensity for each bead size. 
Semantic segmentation is a well-known challenge in the biomedical field. Recently,
researchers have employed deep learning techniques such as U-Net, an encoder-decoder-style
neural network, to segment single cells. The U-Net has a proven ability to segment biomedical
images with good accuracy and minimal training images using image augmentation techniques.

For example, a U-Net was applied to successfully detect rare sperm in microwell
samples from microsurgical testicular sperm extraction. Thus, a U-Net appears to be the best
approach towards segmenting different bead sizes in nanowells. The segmentation
discussed will focus on two different bead sizes and will require the use of three
categories, one for each bead size, and one for the background (including cells). In addition, each
bead size can be used to detect two different biomolecules through the use of two different
fluorophores - resulting in the detection of up to four biomolecules. Table 1 provides an example
of an assay setup for sensing insulin, glucagon, and somatostatin.


![alt text](/images/Image3.JPG)

Segmentation is only the first part of the solution towards increasing the multiplexing
capacity of microscopy-based assays through different bead sizes.
The second part requires the application of the segmentation mask to calculate the fluorescent
intensities for each bead size in each nanowell. Fluorescent intensities of each bead size
will be used along with standard curves to determine the concentration of the biomolecules
secreted in each nanowell.

![alt text](/images/Image4.JPG)


## Software Overview
The software can be downloaded through the following [Github Repository](https://github.com/JadenSequeira/MDLMultiplexedAssay/tree/main), which also includes video tutorials and a user manual on the software.\
MultiELISAB folder holds the software for multiplexed bead ELISA measurements.\
Tutorials folder holds links (google drive links) to the 3 video tutorials.\
Documentation folder holds the User Manual and Overview Document.\
Model folder holds an example U-Net Model file that was trained for 2.8um and 4.5um bead segmentation.

## Getting Started
The goal of this software is to segment two different bead sizes from brightfield images of
nanowells and apply this segmentation to the respective fluorescent nanowell images to
determine the fluorescent intensity of each bead size. Ultimately, the software will be used to
measure cell secretion of multiple biomolecules through the fluorescence intensity of nearby
beads in the nanowell. For example, two different sized beads, each with two different
fluorescent emission ranges, can be used to determine the concentrations of up to four different
biomolecules. Please note that the bead sizes are not constrained and can be chosen as long as they are visibly
distinguishable in brightfield nanowell images. However, a new U-Net prediction model
(Training section) will need to be trained for new sizes. This manual will primarily focus on
working with 2.8um and 4.5um beads.
The software is broken into 6 sections and three scripts. The U-Net architecture script is named
Model.py. Excluding the Renaming script, the 5 sections below are all integrated into a user-friendly GUI
in the MultiELISAB.py script. It is recommended to download the PyCharm IDE to
run this code as it makes downloading the required packages quick and simple (hovering over
the imports provides immediate options to download the package). The python interpreter
installed should be 3.10. Additionally, the TensorFlow version downloaded should be 2.15.0. To
manually download required packages, open settings -> Python Interpreter -> + sign (install) and
search the package of interest (e.g. numpy). This process should be used to download the
TensorFlow package due to its specific version requirement.


## Software Functions
### 1. Nanowell Cropping

![alt text](/images/Image6.JPG)
![alt text](/images/Image7.JPG)

This cropping functionality is developed to work with the nanowell images which have
individual nanowells that are slightly smaller 160 x 160 pixels in size. The U-Net structure is
also only compatible with nanowells smaller than 160x160 pixels. If larger nanowells are used,
the internal code that sets the cropping size of 160x160 pixels must be changed. This change will
also lead to significantly longer training times

### 2. Quality Inspection of Training Data
![alt text](/images/Image14.JPG)

Once the nanowells are cropped for training and testing, the Inspector and Training Tab should
be chosen. Please ensure there are at least 3,000-15,000 cropped nanowell images to ensure that
after inspection there is enough training data.

### 3. Training Data Generation
![alt text](/images/Image8.JPG)

To train the U-Net model, it is suggested that at least 5,000-10,000 training image pairs
(brightfield and ground truth pairs) are provided to the model. To achieve this, the training
images can be augmented by rotation or reflection across an axis to create new training data
images. For instance, applying two augmentations (90-degree rotation and flip about vertical
axis) will lead to a tripling of the training data set size. This makes it possible to train the model
with only 1,000 – 4,000 images after the quality inspection. However, since these images are not
exactly independent, it is suggested that at least 6,000 images are used when augmentations are
used. Please note that before augmentation, the image dataset needs to be split up into training
and testing datasets. It is suggested that the testing dataset size be about 10%-30% of the dataset
size (before augmentation). The larger the testing dataset (e.g. 500-1000 testing image pairs), the
more representative the testing will be. 

### 4. Image Augmentation (Increasing Training Data) and Training
![alt text](/images/Image9.JPG)

![alt text](/images/Image10.JPG)

To train the U-Net model, it is suggested that at least 5,000-10,000 training image pairs
(brightfield and ground truth pairs) are provided to the model. To achieve this, the training
images can be augmented by rotation or reflection across an axis to create new training data
images. For instance, applying two augmentations (90-degree rotation and flip about vertical
axis) will lead to a tripling of the training data set size. This makes it possible to train the model
with only 1,000 – 4,000 images after the quality inspection. However, since these images are not
exactly independent, it is suggested that at least 6,000 images are used when augmentations are
used. Please note that before augmentation, the image dataset needs to be split up into training
and testing datasets. It is suggested that the testing dataset size be about 10%-30% of the dataset
size (before augmentation). The larger the testing dataset (e.g. 500-1000 testing image pairs), the
more representative the testing will be. 

### 5. Segmentation Testing
![alt text](/images/Image11.JPG)

The testing will provide Dice coefficients for the 2.8um and 4.5um bead segmentation. The
average Dice coefficient is computed and if above 0.7, it is acceptable. In the case the average
Dice coefficients are below 0.7, the boxplots outputted by the software which describe the spread
of the Dice coefficients for each nanowell should be analyzed regarding the general spread.
Generally, if the average is significantly below 0.7, or if there is a large spread or a group of
outliers near 0, then the training data set should be increased by acquiring new training images.

### 6. Segmentation Prediction
![alt text](/images/Image12.JPG)

The main purpose of prediction is to measure the fluorescent intensities of the different bead
sizes in each nanowell and apply the standard curve from calibration to translate the fluorescent
intensities into biomolecule concentrations. When a cell is present in the nanowell, this becomes
a secretion assay and when multiple biomolecules are being detected (different bead sizes or
fluorescence), this becomes a multiplexed secretion assay. The process is the exact same as
calibration except that the same “thresh” setting used to create the standard curve must be used
when predicting. The prediction process is repeated for every 2 biomolecules, so for a prediction
of 4 different biomolecules, the process must be conducted twice.

### 7. Standard Curve Generation
![alt text](/images/Image13.JPG)

The main purpose of calibration is to create a standard curve that relates fluorescent intensity and
biomolecule concentration. This standard curve can then be coupled with predicted fluorescent
intensities of beads in a secretion assay to determine the concentration of the biomolecule
secreted. Microwells are given different biomolecule concentrations which result in different
fluorescence intensities due to these different concentrations. Single biomolecule calibration will
be defined as the calibration of a single biomolecule using different concentrations in different
microwells and no other biomolecule present. Multi Biomolecule calibration is used to calibrate
with two biomolecules present at different concentrations – its main purpose is to determine if
the biomolecules interact. Interaction means that biomolecule concentrations do have
independent effects on fluorescent intensity. If they are not independent, then techniques of
biomolecule detection should be re-examined to ensure that there is no cross binding occurring
with the different detection beads.

### 8. Re-stitching Segmented Nanowells (Plotting)
![alt text](/images/Image15.JPG)

Plotting combines data regarding nanowell locations in microscopy images and their respective
fluorescent intensities. It also stitches the individual nanowells with normalized intensities to
display the intensity distribution in the large microscopy image. To use this function, either
calibration or prediction must be conducted. This function will combine FluoroAvgResults.csv
and NanowellLocations.csv into CombinedResults.csv. This organizes all the fluorescent
measurements and XY coordinates of the cropped nanowell images into a single spreadsheet.
Finally, the function uses the coupled data to stitch the individual nanowells with normalized
intensities together and overlay with the TIFF images to show the intensity distributions in the
microwells.

### 9. Update - Nikon Instrument Software (NIS) Compatability
The software can now store 16bit Tiff images of the separated fluorescences of 2.8um and 4.5um beads in folders NIS28 and NIS45 respectively, after calibration or prediction.
This way users can seperate the beads with the same fluorescence into separate fluorecence images for each bead size and input each image to measure fluorescence using NIS. 

![alt text](/images/Image5.JPG)


(Left) Image of the fluorescent nanowell with 2.8um and 4.5um beads – background
fluorescence is apparent in this image. (Middle) Image of the same nanowell with only the 2.8um
bead fluorescence; this image is in the NIS28 folder. (Right) Image of the same nanowell with
only the 4.5um bead fluorescence; this image is in the NIS45 folder
For more information, please see the NIS Fluorescence Measurement Section in the User Manual.

For more information on using each function in the software, please see the user manual located in the Documentation Folder.

## Acknowledgements

I would like to acknowledge and thank the following contributors to the project: Pan Deng for
the design of the Nanowell Cropping algorithm using OpenCV, Deasung Jang for acquiring and
providing experimental data needed to test and develop the software, and Erik Lamoureux for his
help with computing resource setup. I acknowledge and thank Kerryn Matthews, Professor
Hongshen Ma, and the Multi-scale Design Laboratory at UBC for all their supervision, guidance,
and support.