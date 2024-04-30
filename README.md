# Getting-and-Cleaning-Data-Course-Project

# get_project_data.R
It is the script that was used to download and unzip the files, needed to perform the analysis in the first place. It is recommended to use it but not necessary, as long as the files for the 'Human Activity Recognition Using Smartphones Dataset Version 1.0' are present in a folder with name 'UCI HAR Dataset' in the working directory. A lot of comments explain the code and informative messages are printed in console while it is executed, describing what it tries to do. Also, it creates a file with name 'log.txt' in the current working directory (only if it downloads the zipped data) to store the url and the date of the download. If the a folder with name 'UCI HAR Dataset' already exists in the working directory it just informs the user about it's existence and doesn't download the files.
# run_analysis.R
It is the main script of the repository.
In order to produce the 'tidy_data_summary' table, the script 'run_analysis.R' was created and used. It performs the following tasks:

Merges the training and the test sets to create one data set with target variables.
Binds these files,

UCI HAR Dataset/train/subject_train.txt
UCI HAR Dataset/train/X_train.txt
UCI HAR Dataset/train/y_train.txt
from the train set by columns to a table that contains, the human subject, the activity performed and the values of the features.

Binds these files,

UCI HAR Dataset/test/subject_test.txt
UCI HAR Dataset/test/X_test.txt
UCI HAR Dataset/test/y_test.txt
from the test set by columns to a table that contains, the human subject, the activity performed and the values of the features.

Binds the data frames created for test and train set into one large dataset by rows.

Extracts only the measurements on the mean and standard deviation for each measurement.
Finds the target features, which are the features with measurements about mean and standard deviation, and extracts them as well as those that indicate the 'subject' and 'activity' and creates a new data table only with the target variables.
Uses descriptive activity names to name the activities in the data set.
Replace the variable about activity, that contains integers from 1 to 6, with a factor based on levels and labels contained in the 'activity_labels' data file.
Appropriately labels the data set with target variables with descriptive names.
Extracts the target variable names from 'features.txt'.
Corrects a typo that exists in some feature names, that is to replace 'BodyBody' that appears in the names of some features with just 'Body'.
Creates a new tidy dataset with the appropriate labels for the variable names.
From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
Group the tidy data table created in step 4, by 'subject' and 'activity'.

Summarize each variable to find the average for the grouped values.

Ungroup the data table.

Add descriptive names to the variables of the new tidy data table, by adding the prefix 'Avrg-' in the names of the target feature averages.

Write the data in a text file in the present working directory, by the command:

write.table(tidy_data_summary, "tidy_data_summary.txt", row.names = FALSE) 

# tidy_data_summary.txt
The tidy dataset that was produced by the script 'run_analysis.txt', which contains the averages of selected features from the original 'Human Activity Recognition Using Smartphones Dataset Version 1.0'

To read the table back on R correctly, you can use the following command:

tidy_data_summary <- read.table(file = "tidy_data_summary.txt",
                                header = TRUE, check.names = FALSE, dec = ".") 
Or for faster loading some additional arguments can be specified:

tidy_data_summary <- read.table(file  = "tidy_data_summary.txt", 
                                header = TRUE, check.names = FALSE, dec = ".", 
                                colClasses = c("numeric", "factor", rep("numeric", 66)), 
                                nrows = 180, comment.char = "", quote = "") 
