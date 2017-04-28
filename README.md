# Data-Science-Bowl-2017

1.	Problem
We have to classify whether someone will be diagnosed with lung cancer at some point during the next year. We are given DICOM files, which is a format that is often used for medical scans. Using CT scans from 1400 patients in the training set, we have to build a model which can predict on the patients in the test set.
2.	Significance
A diagnostic for early detection of lung cancer could be important in the effective therapy of the disease. So this study aims to build a smart and intelligent system for lung diseases, especially lung cancer diagnosis, using deep learning and GPU's
We will use the large number of CT cases available to train some novel ConvNets to (1) detect the candidate nodules in CT (if possible), (2) reduce the ambiguity in data, and (3) predict the probability of lung cancer according to the various features of detected nodules.
4.	Data Mining / Cleaning

4.1	The data consists of many 2D "slices," which, when combined, produce a 3-dimensional rendering of whatever was scanned. In this case, that's the chest cavity of the patient. We've got CT scans of about 1500 patients, and then we've got another file that contains the labels for this data. So initially I have divided then data into cancerous patient  and non-cancerous patients by merging the Labels with the data available.

 

4.2	Normalization: 
Some scanners have cylindrical scanning bounds, but the output image is square. The pixels that fall outside of these bounds get the fixed value -2000. In my cleaning process I have replaces all the values [-2048 , -2000, -1024, -1000] with [0]. Normalization values currently range from -1024 to around 2000. Anything above 400 are simply bones with different radio density.

For every axial slice in the scan, determine the largest solid connected component (the body+air around the person), and set others to 0. This fills the structures in the lungs in the mask. (Reference: https://en.wikipedia.org/wiki/Hounsfield_scale)


 

4.3	RESIZE: 
Also, I have resized the Dicom img ‘pixel’ value to 32*32 in order to sort the data and run the models. (Reference Dr. Lawrence V Fulton 'code from class'). We're resizing our images from 512*512 to 32*32 below is the code for it;


 


4.4	 RESCALE:  Another thing I tried in my models is with the sliceLocation. Firstly, I have re-scaled (using RESCALE function of R from RPMG library) all the sliceLocation of Dicom image with a scale 0 to 100. In the Dicom images the maximum and minimum sliceLocation value is between [-420, 877.3] which has been converted to [0,100] scale for better uniformity of data for the patient.

       


4.5	I have used different script to serve the below purpose:
	To extract the headers.
	To extract the images 'pixel' data into array (Reference Dr. Lawrence V Fulton 'code from class'
	To resize the images 'pixel' data (Reference Dr. Lawrence V Fulton 'code from class')
	Normalizing the values values [-2048 , -2000, -1024, -1000] with [0].
	To 'rescale' the sliceLocation into scale of 1, 100 for values of original sliceLocation ranging between -420, 877.3. (Script: Model 2 Scipt Data Science Bowl 2017)
	Predicting the missing values of sliceLocation in stage2 Test data. (Script: Model 2 Scipt Data Science Bowl 2017)
	Imputed the missing sliceLocation values with mean ( in few models)
	Modelling using Random Forest and DeepLearning using h2o package.

8.	Model Performance

8.1	I started doing in Python, and has done some preliminary visualization. I have shared the output in html format where I have plotted dicom image of one patient and resized it to 200 *200 scale for one patient. Script: `Visualizing the DICOM Image before KICK start.ipynb`

8.2	Secondly, coming to exploring the data in python was little tedious for me it took nearly a day just to install few packages and I spend virtually a long time on setting the framework for the required packages. So, I have decided to go with old friend R for further analysis.

8.3	To train the data I have tried using 2 and 3 hidden layers NN model with each of 100 , 150 , 200 nodes respectively and an epoch of 10,50,100, 200 resp using the h2o package on a subset l of data which lasted for longer than 40 -120 minutes for different combination of parameters. 

8.4	Apart I also tried xgboost and logit regression models. However, the best accuracy I got is with H2O deepLearning with a score of .69315 on the 'Stage2' Data.

8.5	This folder contains 4 scripts of four different Models.
	Model-1 Neural Networks score 0.83175
	Model-2 DeepLearning with rescaling of slice location (best accuracy model) 0.69315
	Model-3 DeepLearning without rescaling 0.76732
	Model-4 random forest 0.83471
