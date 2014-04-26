CodeBook.md
========================================================

This document describes the data and analysis for run_analysis.R.

**Variables**  
A full description of the data, including variables, is available in the README.txt and features_info.txt files available with the data [here.](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip) Few new variables were created in this analysis. The final outputs are saved in tidyData and tidyData2. Descriptions can be found in-line with the code.  

**Data**  
The data comes from [this site.](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)
It represents data collected from the accelerometers from the Samsung Galaxy S smartphone. The data sets are as follows:

* **The "Inertial Signals" folder in test and train is not used for this analysis, as the request can be completed using the data in X_test.txt and Y_test.txt alone.** 
* The main sources of data are the X_test.txt and X_train.txt files, which contain a wide variety of accelerometer data for test subjects performing different activities
* Files y_test and y_train contain activity codes for each observation in their respective x files 
* Subject_test.txt contains which subjects each line pertains to
* Activity_labels.txt contains a map of the numeric codes for each activity
* Features.txt contains a map of the feature names for each accelerometer variable

**Transformations in run_analysis.R**  
1. The data is downloaded to a "data" directory, unzipped, and read.  
2. The components of the dataset are then combined together, with the subject number becoming the first column, followed by the activity number, and then the rest of the accelerometer data.  
3. The test and train data sets are unioned.  
4. The columns of the resulting table are named with Features.txt names, and the activity variable is cast as a factor with labels from Activity_labels.  
5. Only those variables whose names end in "mean" or "std" are selected from the resulting dataset. **Variables such as "FreqMean" were not included as they were not considered pure measurements on the mean.**  
6. The dataset is melted and recast to compute the means of all of the accelerometer variables for each unique subject-activity pair.  
7. The final tidy table is output to a .txt file. **This is considered the tidy dataset that must be uploaded for the project description.**

**Citation**  
[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012