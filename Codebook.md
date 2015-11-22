#Data Set Description#

"FinalMergeSumm" data set is a summary report of six
activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) performed wearing a smartphone (Samsung Galaxy S II)
on the waist by 30 respondents. There are total six variables in the data set which reflect the mean values for each activity and each subject.

Each mean value suggest the total mean body acceleration in 3 axial raw direction, also it show the mean of standard deviation in total body acceleration during the particular activity. 

##Description Of Variables##

 * tBodyAcc_mean_X - Mean body acceleration in x axial direction
 * tBodyAcc_mean_Y - Mean body acceleration in y axial direction
 * tBodyAcc_mean_Z - Mean body acceleration in z axial direction
 * tBodyAcc_std_X - Mean Standard Dev. body acceleration in x axial direction
 * tBodyAcc_std_Y - Mean Standard Dev. body acceleration in y axial direction 
 * tBodyAcc_std_Z - Mean Standard Dev. body acceleration in z axial direction 
 * Activity - Name of Activity Performed (Rows with NA are belong to Subject Summary Stats)
 * Subject - Subject Identifier (Rows with NA are belong to Subject Summary Stats)

Please note, each row labeled with particular activity reflecting summary report for same, rows with NA values for this variable belongs to subject summaries and to identify particular subject please refer subject variable.

## Raw Data Set
The obtained data set has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating 
the training data and 30% the test data. 

##Task Performed To Create Tidy Data Set
 * Combined Test and Training Data Created With Subject and Activity ID
 * New Data Set Created Keeping only variables needed for Further Analysis
 * Activity Codes are replaced with Descriptive Names for easy reference
 * Variable Names provided to each variable for easy reference
 * Two summary reports based on Subject and activity created and later combined into one data set and finally write into the text data file.