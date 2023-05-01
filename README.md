Download Link: https://assignmentchef.com/product/solved-cecs-551-programming-assignment-3
<br>



<strong>Presenting Your Work.</strong>

Submit via email a <em>single </em>R script named assign3-StudentFirstName.R. For example, if your first name is George, then you would submit the file assign3-George.R. Line 1 of the file should include your full name as a comment. Also, for each block of code that pertains to some exercise, say Exercise 1, preface the code with the comment (all in caps)

#EXERCISE 1

Each function should be named <em>exactly </em>as it appears in the exercise, and have an input signature that follows the order specified in the exercise.

<strong>Important: </strong>make sure your file produces no errors when sourced by the R interpreter. Otherwise your work will not be graded. Therefore, all answers, tables, explanations, etc. should be placed in comments, so as not to be confused with the actual R code.

Your email submission should be postmarked no later than the time shown on the due date. Submissions received after that time, but on the same day will lose one letter grade. Submissions emailed on a later day will either not be accepted, or will lose two letter grades.

<strong>Exercises</strong>

<ol>

 <li>Write an R function called <strong>partition </strong>that takes as input a data frame df, and a real number <em>α </em>∈ (0<em>,</em>1) and returns a list consisting of two data frames df1 and df2, where df1 consists of b<em>αr</em>c randomly selected rows (without replacement) of df, and df2 consists of the remaining unselected rows of df, where <em>r </em>denotes the number of rows of df. For example, if <em>r </em>= 100, and <em>α </em>= 0<em>.</em>4, then df1 will consist of 40 randomly selected rows of df, and df2 will consist of the other 60 rows.</li>

 <li>Implement the R functionbest_svm(df, alpha, degree, cost)</li>

</ol>

which works as follows. First, partition(df,alpha) is called to obtain two data frames df1 and df2 from df, where df1 will serve as the training set, and df2 will serve as the test set. Now, for each (<em>d,c</em>) combination, where <em>d </em>is a member of vector degree, and <em>c </em>is a member of vector cost, function

svm(Class~., data = df1, kernel=”polynomial”, degree = d, type = “C-classification”,cost=c)

is called to create a support-vector machine model, where we assume that “Class” is the name of the data-frame attribute that represents the class label of each vector in the frame. The model is then tested against data set df2. Finally best svm returns a list having the three attributes <em>d</em>, <em>c</em>, and accuracy, that give the <em>d </em>and <em>c </em>value of the model demonstrating highest accuracy against the test set. Note: make sure that each df1 and df2 remain fixed for each learning model.

<ol start="3">

 <li>Review and download the Car data set athttps://archive.ics.uci.edu/ml/datasets/Car+Evaluation</li>

</ol>

Place attribute names in line one of the file, making sure that Class is the name of the final attribute. Load the data set into a data frame df, and call best svm on inputs df, <em>α </em>= 0<em>.</em>8, degree = (1<em>,</em>2<em>,</em>3<em>,</em>4), and cost = (0<em>.</em>1<em>,</em>1<em>.</em>0<em>,</em>10<em>.</em>0<em>,</em>100<em>.</em>0<em>,</em>1000<em>.</em>0<em>,</em>10000<em>.</em>0). Call best svm 10 different times on these inputs, and provide a table (as an R-comment) showing the <em>d</em>, <em>c</em>, and accuracy values of each call.

<ol start="4">

 <li>By setting the C-classification cost to 10<sup>5 </sup>(meaning very little to no slack allowance), determine the least degree value <em>d </em>that can produce a (nonlinear) model that can attain 100% accuracy for the entire data set.</li>

 <li>Repeat Exercise 2, but instead implement the functionsvm.cross(df, degree, cost, n)</li>

</ol>

This function works similar to the previous one, but now, instead of the partitioning df, cross validation is performed on the entire data set using <em>n &gt; </em>0 as the fold. Thus, the call to svm is now

svm(Class~., data = df, kernel=”polynomial”, degree = d, type = “C-classification”,cost=c, cross = n)

Finally best.svm.cross returns a list having the three attributes <em>d</em>, <em>c</em>, and accuracy, that give the <em>d </em>and <em>c </em>value of the model demonstrating highest average cross-validation accuracy, along with the value of the average accuracy (obtained from the model via model$tot.accuracy).

<ol start="6">

 <li>Apply your function svm.cross to the Wisconsin Breast Cancer data set found at</li>

</ol>

https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Original%29

Place attribute names in line one of the file, making sure that Class is the name of the final attribute. Load the data set into a data frame df, and call best.svm.cross on inputs df, degree = (1<em>,</em>2<em>,</em>3<em>,</em>4), cost = (0<em>.</em>1<em>,</em>1<em>.</em>0<em>,</em>10<em>.</em>0<em>,</em>100<em>.</em>0<em>,</em>1000<em>.</em>0<em>,</em>10000<em>.</em>0), and <em>n </em>= 10. In a comment, report on your findings.

<ol start="7">

 <li>Implement the R function</li>

</ol>

bootstrap(df, model, p, n)

that takes as input a data frame df, svm model trained on df, probability <em>p</em>, and positive integer <em>n</em>. Function bootstrap then makes <em>n </em>bootstrap samples of df and, for each sample <em>S</em>, determines the accuracy of model tested against <em>S</em>. The <em>n </em>accuracies are then sorted and used to create a confidence interval <em>I </em>so that, with probability <em>p</em>, the model accuracy lies within <em>I</em>. Finally bootstrap returns a list having the two attributes lower and upper that store the lower and upper bounds of the confidence interval.

<ol start="8">

 <li>Use function bootstrap on the Wisconsin Breast Cancer data set, <em>p </em>= 0<em>.</em>90, and <em>n </em>= 100. For the model, train an svm on the entire data set using the values for <em>d </em>and <em>c </em>as reported in Exercise 6. In a comment provide the 90% confidence interval for the accuracy of this model.</li>

</ol>