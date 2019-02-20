Dataset is downloaded under UCI HAR Dataset folder

The run_analysis.R script then reads and converts data followed by the 5 steps required by the course project.

0. Data is read file by file and converted into a single data frame (data.train & data test).Set their names to subject, activity, and features.

features <- features.txt read and set as character 

Read and create data.train data frame using the following:
data.train.x <- X_train.txt : 7,352 rows 561 columns
data.train.acitivity <- y_train.txt : 7,352 rows 1 column
data.train.subject <- subject_train.txt : 7,352 rows 1 column

Read and create data.test data frame using the following:
data.test.x <-X_test.txt : 2,947 rows 561 columns
data.test.acitivity <- y_test.txt : 2,947 rows 1 column
data.test.subject <- subject_test.txt : 2,947 rows 1 column


1. Merge the training and the test sets to create one data set
data.all (10299 rows, 563 columns) is created by merging data.train and data.test using rbind() function

2. Extracts only the measurements on the mean and standard deviation for each measurement
data.sub (10299 rows, 81 columns) is created by searching for mean or std strings in features dataset and selecting only subject, code and the measurements on the mean and standard deviation for each measurement

3. Uses descriptive activity names to name the activities in the data set
activity.labels <- activity_labels.txt read and set as character 
Replace the activity column in data.sub with the second column taken from the activity variable.

4.Appropriately labels the data set with descriptive variable names
code column in data.sub renamed to:
All Acc in data.sub replaced by Accelerometer
All Gyro in data.sub replaced by Gyroscope
All BodyBody in data.sub replaced by Body
All Mag in data.sub replaced by Magnitude
All -mean- in data.sub replaced by _Mean_
All -std- in data.sub replaced by _StandardDevation_
All start with character t in column’s name replaced by Time
All start with character f in column’s name replaced by Frequency
All - in data.sub replaced by _
All ( ) in data.sub replaced by ""

5.From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
tidy.data (180 rows, 81 columns) is created by sumarizing data.tidy taking the means of each variable for each activity and each subject, grouped by subject and activity.
Export tidy.data into tidy_data.txt file.