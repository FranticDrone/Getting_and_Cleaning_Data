<h3>First I check if the library is installed.</h3>
<li>
<ul>If the library isn't installed then the code will install</ul>
</li>

<h3>All the files are loaded to begin the analisys</h3>
<li>
<ul>Var: feat_lbl</ul>
<ul>File: features.txt</ul>
<ul>Description: The file that contain all the column names</ul>


<ul>Var: actv_lbl</ul>
<ul>File: activity_labels.txt</ul>
<ul>Description: The file that contain the activity names</ul>

<ul>Var: x_train</ul>
<ul>File: X_train.txt</ul>
<ul>Description: Table with the main columns of train</ul>

<ul>Var: y_train</ul>
<ul>File: y_train.txt</ul>
<ul>Description: Table with the index activity of train</ul>

<ul>Var: s_train</ul>
<ul>File: subject_train.txt</ul>
<ul>Description: Table with the index features of train</ul>

<ul>Var: x_test</ul>
<ul>File: X_test.txt</ul>
<ul>Description: Table with the main columns of test</ul>

<ul>Var: y_test</ul>
<ul>File: y_test.txt</ul>
<ul>Description: Table with the index activity of test</ul>

<ul>Var: s_test</ul>
<ul>File: subject_test.txt</ul>
<ul>Description: Table with the index features of train</ul>
</li>

<h3>Creating the columns for Activities and Features</h3>
<li>
<ul>new_cols is the variable with the name of the first two columns</ul>
<ul>cols is the variable with all the cols names</ul>
<ul>Merge the training and test</ul>
<ul>The files of train was inserted in the r_train variable The files of test was inserted in the r_test variable When the r_train and r_test are merged we load the result in result_merged and insert the column names</ul>
</li>

<h3>Choosing the columns</h3>
<li>
<ul>After load the result_merged we choose the columns that extracts only the measurements on the mean and standard deviation and load in result_filtered</ul>
</li>

<h3>Updating the Activity_Labels</h3>
<li>
<ul>We get the id values of the Activity_Labels and change for the description values of Activity_Labels</ul>
</li>

<h3>Group and mean</h3>
<li>
<ul>Group the variables Activity_Labels and Features to get the mean of each variable</ul>
</li>
