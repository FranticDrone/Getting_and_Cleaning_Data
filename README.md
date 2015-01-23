The source code is already commented
<pre>
# You should create one R script called run_analysis.R that does the following. 
# 1. Merges the training and the test sets to create one data set.
# 2. Extracts only the measurements on the mean and standard deviation for each measurement. 
# 3. Uses descriptive activity names to name the activities in the data set
# 4. Appropriately labels the data set with descriptive variable names. 
# 5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.



run_analysis <- function(){
    #It is mandatory to use the library
    if(!require(dplyr)){
        install.packages("dplyr")
    }
    library(dplyr)
    
    # Loading: All Files
    feat_lbl <- read.table("./UCI HAR Dataset/features.txt")
    actv_lbl <- read.table("./UCI HAR Dataset/activity_labels.txt")
    x_train <- read.table("./UCI HAR Dataset/train/X_train.txt")
    y_train <- read.table("./UCI HAR Dataset/train/y_train.txt")
    s_train <- read.table("./UCI HAR Dataset/train/subject_train.txt")
    x_test <- read.table("./UCI HAR Dataset/test/X_test.txt")
    y_test <- read.table("./UCI HAR Dataset/test/y_test.txt")
    s_test <- read.table("./UCI HAR Dataset/test/subject_test.txt")
    
    # Creating columns for Features and Activity_labes 
    new_cols <- data.frame(V1 = c(0, 0), V2 = c("Activity_Labels", "Features"))
    cols <- rbind(new_cols, feat_lbl)
    
    # 1. Merges the training and the test sets to create one data set.
    r_train <- cbind(y_train, s_train, x_train)
    r_test <- cbind(y_test, s_test, x_test)
    result_merged <- rbind(r_train, r_test)
    colnames(result_merged) <- cols[,2]
    
    # 2. Extracts only the measurements on the mean and standard deviation for each measurement.
    # Observation: Inside the file features_info.txt the measurements have parentheses
    # mean(): Mean value
    # std(): Standard deviation
    # 1 and 2 to keep the columns "Activity_labes" and "Features"
    result_filtered <- result_merged[c(1, 2, grep('mean\\(\\)|std\\(\\)',colnames(result_merged)))]
    
    # 3. Uses descriptive activity names to name the activities in the data set
    for(aux in 1:nrow(result_filtered)) {
        desc_actv <- as.character(actv_lbl[actv_lbl$V1 == result_filtered[aux, 1], 2])
        result_filtered[aux, 1] <- desc_actv
    }
    
    # 4. Appropriately labels the data set with descriptive variable names.
    # The letter "t" at the beginning of the string was changed to Time
    # The letter "f" at the beginning of the string was changed to Frequency
    # The parentheses were removed
    colnames(result_filtered) <- c("Activity_Labels", 
                                   "Features", 
                                   "Time_BodyAcc_Mean_X", 
                                   "Time_BodyAcc_Mean_Y", 
                                   "Time_BodyAcc_Mean_Z", 
                                   "Time_BodyAcc_STD_X", 
                                   "Time_BodyAcc_STD_Y", 
                                   "Time_BodyAcc_STD_Z", 
                                   "Time_GravityAcc_Mean_X", 
                                   "Time_GravityAcc_Mean_Y", 
                                   "Time_GravityAcc_Mean_Z", 
                                   "Time_GravityAcc_STD_X", 
                                   "Time_GravityAcc_STD_Y", 
                                   "Time_GravityAcc_STD_Z", 
                                   "Time_BodyAccJerk_Mean_X", 
                                   "Time_BodyAccJerk_Mean_Y", 
                                   "Time_BodyAccJerk_Mean_Z", 
                                   "Time_BodyAccJerk_STD_X", 
                                   "Time_BodyAccJerk_STD_Y", 
                                   "Time_BodyAccJerk_STD_Z", 
                                   "Time_BodyGyro_Mean_X", 
                                   "Time_BodyGyro_Mean_Y", 
                                   "Time_BodyGyro_Mean_Z", 
                                   "Time_BodyGyro_STD_X", 
                                   "Time_BodyGyro_STD_Y", 
                                   "Time_BodyGyro_STD_Z", 
                                   "Time_BodyGyroJerk_Mean_X", 
                                   "Time_BodyGyroJerk_Mean_Y", 
                                   "Time_BodyGyroJerk_Mean_Z", 
                                   "Time_BodyGyroJerk_STD_X", 
                                   "Time_BodyGyroJerk_STD_Y", 
                                   "Time_BodyGyroJerk_STD_Z", 
                                   "Time_BodyAccMag_Mean", 
                                   "Time_BodyAccMag_STD", 
                                   "Time_GravityAccMag_Mean", 
                                   "Time_GravityAccMag_STD", 
                                   "Time_BodyAccJerkMag_Mean", 
                                   "Time_BodyAccJerkMag_STD", 
                                   "Time_BodyGyroMag_Mean", 
                                   "Time_BodyGyroMag_STD", 
                                   "Time_BodyGyroJerkMag_Mean", 
                                   "Time_BodyGyroJerkMag_STD", 
                                   "Frequency_BodyAcc_Mean_X", 
                                   "Frequency_BodyAcc_Mean_Y", 
                                   "Frequency_BodyAcc_Mean_Z", 
                                   "Frequency_BodyAcc_STD_X", 
                                   "Frequency_BodyAcc_STD_Y", 
                                   "Frequency_BodyAcc_STD_Z", 
                                   "Frequency_BodyAccJerk_Mean_X", 
                                   "Frequency_BodyAccJerk_Mean_Y", 
                                   "Frequency_BodyAccJerk_Mean_Z", 
                                   "Frequency_BodyAccJerk_STD_X", 
                                   "Frequency_BodyAccJerk_STD_Y", 
                                   "Frequency_BodyAccJerk_STD_Z", 
                                   "Frequency_BodyGyro_Mean_X", 
                                   "Frequency_BodyGyro_Mean_Y", 
                                   "Frequency_BodyGyro_Mean_Z", 
                                   "Frequency_BodyGyro_STD_X", 
                                   "Frequency_BodyGyro_STD_Y", 
                                   "Frequency_BodyGyro_STD_Z", 
                                   "Frequency_BodyAccMag_Mean", 
                                   "Frequency_BodyAccMag_STD", 
                                   "Frequency_BodyBodyAccJerkMag_Mean", 
                                   "Frequency_BodyBodyAccJerkMag_STD", 
                                   "Frequency_BodyBodyGyroMag_Mean", 
                                   "Frequency_BodyBodyGyroMag_STD", 
                                   "Frequency_BodyBodyGyroJerkMag_Mean",
                                   "Frequency_BodyBodyGyroJerkMag_STD")
    
    # 5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
    # Take the result of #4 and group the Activity and the Features then obtain the average of each variable
    result_group <- group_by(result_filtered, Activity_Labels, Features)
    result_average <- summarise_each(result_group, funs(mean))
}
</pre>
