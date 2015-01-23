<h3>First I check if the library is installed.<h3>
If the library isn't installed then the code will install
All the files are loaded to begin the analisys
Var: feat_lbl
File: features.txt
Description: The file that contain all the column names

Var: actv_lbl
File: activity_labels.txt
Description: The file that contain the activity names

Var: x_train
File: X_train.txt
Description: Table with the main columns of train

Var: y_train
File: y_train.txt
Description: Table with the index activity of train

Var: s_train
File: subject_train.txt
Description: Table with the index features of train

Var: x_test
File: X_test.txt
Description: Table with the main columns of test

Var: y_test
File: y_test.txt
Description: Table with the index activity of test

Var: s_test
File: subject_test.txt
Description: Table with the index features of train
Creating the columns for Activities and Features
new_cols is the variable with the name of the first two columns
cols is the variable with all the cols names
Merge the training and test
The files of train was inserted in the r_train variable The files of test was inserted in the r_test variable When the r_train and r_test are merged we load the result in result_merged and insert the column names

Choosing the columns
After load the result_merged we choose the columns that extracts only the measurements on the mean and standard deviation and load in result_filtered

Updating the Activity_Labels
We get the id values of the Activity_Labels and change for the description values of Activity_Labels

Group and mean
Group the variables Activity_Labels and Features to get the mean of each variable
