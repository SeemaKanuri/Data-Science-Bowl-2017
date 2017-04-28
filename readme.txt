1.	I started doing in Python, and has done some preliminary visulization. I have shared the output in html format where I have ploted dicom image of one patient and resized it to 200 *200 scale for one patient. Script: Visualizing the DICOM Image before KICK start.ipynb


2.	Secondly, comin to exploring the data in python was little tedius for me it took nearly a day just to install few packages and I spend vertually a long time on setting the framework for the required packages. So I have decided to go with old friend R for further analysis.


3.	However R seems to be an easy choice where I was able to do the analysis in a quick time. I have used 3 scripts in different ways:
	1.	I started doing in Python, and has done some preliminary visulization. I have shared the output in html format where I have ploted dicom image of one patient and resized it to 200 *200 scale for one patient. Script: Visualizing the DICOM Image before KICK start.ipynb


2.	Secondly, comin to exploring the data in python was little tedius for me it took nearly a day just to install few packages and I spend vertually a long time on setting the framework for the required packages. So I have decided to go with old friend R for further analysis.


3.	However R seems to be an easy choice where I was able to do the analysis in a quick time. I have used 3 scripts in different ways:
	To extract the headers.
	To extract the images 'pixel' data into array (Reference Dr. Lawrence V Fulton 'code from class'
	To resize the images 'pixel' data (Reference Dr. Lawrence V Fulton 'code from class')
	Normalizing the values values [-2048 , -2000, -1024, -1000] with [0].
	To 'rescale' the sliceLocation into scale of 1, 100 for values of original sliceLocation ranging between -420, 877.3. (Script: Model 2 Scipt Data Science Bowl 2017)
	Predicting the missing values of sliceLocation in stage2 Test data. (Script: Model 2 Scipt Data Science Bowl 2017)
	Imputed the missing sliceLocation values with mean ( in few models)
	Modelling using Random Forest and DeepLearning using h2o package.


4.	To train the data I have tried using 2 and 3 hidden layers NN model with each of 100 , 150 , 200 nodes respectively and an epoch of 10,50,100, 200 resp using the h2o package on a subset l of data which lasted for longer than 40 -120 minutes for different combination of parameters. 


5.	Apart I also tried xgboost and logit regression models. However the best accuracy I got is with H2O deepLearning with a score of .69315 on the 'Stage2' Data.


6 . This folder contains 4 scripts of four different  Models .
	Model-1  Neural Networks score 0.83175
	Model-2 DeepLearning with rescaling of slice location ( best accuracy model) 0.69315 
	Model-3 DeepLearning without rescaling 0.76732
	Model-4 random forest 0.83471

7. Each model has Output predicted value file and Rmarkdown file for preview.

4.	To train the data I have tried using 2 and 3 hidden layers NN model with each of 100 , 150 , 200 nodes respectively and an epoch of 10,50,100, 200 resp using the h2o package on a subset l of data which lasted for longer than 40 -120 minutes for different combination of parameters. 


5.	Apart I also tried xgboost and logit regression models. However the best accuracy I got is with H2O deepLearning with a score of .69315 on the 'Stage2' Data.


6 . This folder contains 4 scripts of four different  Models .
	Model-1  Neural Networks score 0.83175
	Model-2 DeepLearning with rescaling of slice location ( best accuracy model) 0.69315 
	Model-3 DeepLearning without rescaling 0.76732
	Model-4 random forest 0.83471

7. Each model has Output predicted value file and Rmarkdown file for preview.

