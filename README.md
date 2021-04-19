# pands-project2021 - Iris Dataset

# Author : Michelle O'Connor

# Programs to be installed  

# Contents

1.0 Introduction   
 - 1.1 History of Iris Dataset
 - 1.2 Use of Iris Dataset

2.0 Loading and understanding the Iris dataset  
 - 2.1 Loading the dataset   
 - 2.2 Understanding the dataset  

3.0 Data Visualisation   
 - 3.1 Histograms   
 - 3.2 Boxplots   
 - 3.3 Scatterplot  

4.0 


# 1.0 Introduction

## 1.1 History of Iris Dataset  

The Iris flower data set or Fisher's Iris data set is a multivariate data set introduced by the British statistician, eugenicist, and biologist Ronald Fisher in his 1936 paper __The use of multiple measurements in taxonomic problems__ as an example of linear discriminant analysis.  

The Iris dataset consists of the following:

50 samples of 3 different species of Iris where used in the dataset (total 150 samples)  
    1.Iris setosa   
    2.Iris Virginica  
    3.Iris Veriscolor  

There are 4 variables measured in the Iris dataset were   
    1.Length of sepals (cm)  
    2.Width of sepals (cm)   
    3.Length of petals (cm)  
    4.Width of petals (cm)   


## 1.2 Use of Iris Dataset 

Based on the combination of the features (Sepal Lenght, Sepal Width, Petal Length, Petal Width), Fisher developed a linear discriminant model to distinguish the species from each other based on the morphology of their flowers.  

This discriminant function performed well in discriminating between these species, except some overlap between Iris versicolor and Iris virginica. 
The Iris setosa is noticeably different from the other two species.

Using this linear discriminant model, this data set became a typical test case for many statistical classification techniques in machine learning and became the “hello world” of Machine Learning.

“Hello World” is often the first program written by people learning to code, the iris dataset is generally the first dataset used as an introduction into Machine Learning. 

References
These measures were used to create a linear discriminant model to classify the species.
The dataset is often used in data mining, classification and clustering examples and to test algorithms.


https://www.ritchieng.com/machine-learning-iris-dataset/
https://en.wikipedia.org/wiki/Iris_flower_data_set
https://towardsdatascience.com/the-iris-dataset-a-little-bit-of-history-and-biology-fb4812f5a7b5
http://www.lac.inpe.br/~rafael.santos/Docs/CAP394/WholeStory-Iris.html

Adding image to Github read me file  
https://www.youtube.com/watch?v=hHbWF1Bvgf4
![](Iris_Image.png)

# 2.0 Loading and understanding the Iris dataset:

## 2.1 Loading the dataset  
The Iris dataset is widely available on the internet. The dataset is included in R base and Python in the machine learning package Scikit-learn, so that users can access it without having to find a source for it.  

For this project, however I am treating the iris dataset as dataset that needs to be loaded in so I use pandas to import the data from a csv file and create a dataframe.    
I rename the columns so that they include the measurement type 'cm' in the title and I rename the class column to species. 

    path = ""
    filenameForIrisData = path + "iris.csv"
    df = pd.read_csv(filenameForIrisData)
    iris_df = df.rename(columns = {"sepallength" : "sepallengthcm", "sepalwidth" : "sepalwidthcm",   
    "petallength" : "petallengthcm", "petalwidth" : "petalwidthcm", "class" : "species"})

## 2.2 Understanding the dataset   

To start with understanding the dataset, I preview a sample of the data, for example the first 5 rows
    print(iris_df.head(5))   
            sepallengthcm  sepalwidthcm  petallengthcm  petalwidthcm      species  
        0            5.1           3.5            1.4           0.2  Iris-setosa  
        1            4.9           3.0            1.4           0.2  Iris-setosa   
        2            4.7           3.2            1.3           0.2  Iris-setosa   
        3            4.6           3.1            1.5           0.2  Iris-setosa   
        4            5.0           3.6            1.4           0.2  Iris-setosa    

This shows the dataset has 5 columns and an unknown quantity of the rows.

I then build upon this to extract different views of the data:  

* Show the full size (shape) of the dataset.  
        We have 150 samples for the 5 columns    
    
        print(iris_df.shape)  

        (150, 5) = 150 rows, 5 columns


* Show the number of instances, the number of attributes and if any null values exist in the dataset.  
        We have 150 instances for 5 attributes of which no null values exist.    
    
        print(iris_df.info())

        #   Column         Non-Null Count  Dtype
        ---  ------         --------------  -----
        0   sepallengthcm  150 non-null    float64
        1   sepalwidthcm   150 non-null    float64
        2   petallengthcm  150 non-null    float64
        3   petalwidthcm   150 non-null    float64
        4   species        150 non-null    object
        dtypes: float64(4), object(1)

* Show how many instances the dataset contains by species.  
        The dataset has an equal number of 50 instances for each species.  
           
        print(iris_df.groupby('species').size())   

        Iris-setosa        50
        Iris-versicolor    50
        Iris-virginica     50

* Show the basic statistical details of the dataframe (iris dataset).  
        This shows the count, mean, std, min, 25%, 50%, 75%, max infor for each attribute/feature. 
        
        print(iris_df.describe())

               sepallength  sepalwidth  petallength  petalwidth
        count   150.000000  150.000000   150.000000  150.000000
        mean      5.843333    3.054000     3.758667    1.198667
        std       0.828066    0.433594     1.764420    0.763161
        min       4.300000    2.000000     1.000000    0.100000
        25%       5.100000    2.800000     1.600000    0.300000
        50%       5.800000    3.000000     4.350000    1.300000
        75%       6.400000    3.300000     5.100000    1.800000
        max       7.900000    4.400000     6.900000    2.500000


* Show the summary of each variable by the species  
        print(iris_df.groupby("species").describe())

        To extract this data into a newly created single text file, we need to make the output in a   
        string format using str. 

            with open(".\Variable_Summary.txt", "wt") as i:
            i.write(str(iris_df.groupby("species").describe()))


https://www.c-sharpcorner.com/article/a-first-machine-learning-project-in-python-with-iris-dataset/
https://www.c-sharpcorner.com/article/a-first-machine-learning-project-in-python-with-iris-dataset/
https://www.kaggle.com/adityabhat24/iris-data-analysis-and-machine-learning-python
https://towardsdatascience.com/how-to-use-groupby-and-aggregate-functions-in-pandas-for-quick-data-analysis-c19e7ea76367

# 3.0 Data Visualisation 

With a basic understanding of the data, we move to data visualisation to help us compare and observe trends within the data.

There are many visualation options within python using matplotlib and seaborn. 

## 3.1 Historgrams  

Histograms show the distribution of the number of instances by each individual attribute. 

    Code to display a histogram for the sepal length:
    plt.figure(figsize = (10, 7)) = set the size (in inches) of the histogram
    x = iris_df["sepallengthcm"] = defining the data input
    plt.hist(x, bins = 20, color = "green") = plotting the histogram (x=input data, bin = number of columns, colour of bin/column = green)
    plt.title("Sepal Length in cm") = adding a title
    plt.xlabel("Sepal Length cm") = adding a name to the xlabel (horizontal line)
    plt.ylabel("Count") = adding a name to the ylabel (vertical line)
    plt.savefig("Sepal_Length.png") = saving the histogram as an image to the folder
    plt.show() = displaying the histogram


## 3.2 Boxplot  

Boxplot show the range the individual attributes fall into, it represents the minimum, first quartile (25% or lower), median, third quartile (75% or upper) and maximum of the dataset.  
The box on the plot shows between the first (25%) and third quartile (75%) on the range. The horizontal line that goes through the box is the median.  
The top and bottom lines known as 'whiskers' extend from the ends of the box to the minimun and maximum value.    
Any data points past the whiskers (represented by a diamond) are considered as outliers.  

Using Seaborn we plot a Boxplot for each attribute (4 Boxplots in total). 
To show 4 Boxplots on the one output requires a 2 x 2 (2 columns and 2 rows), therefore subplot(2,2) is required.  
The 3rd value in the subplot indicates where on the output the plot is shown, as follows 1 - Top Left, 2 - Top Right, 3 - Bottom Left, 4 - Bottom Right, 
for example (2,2,3) would show on the bottom left of the output.  
On the plot the x axis is the species type, y axis is the attribute  

    plt.figure(figsize=(15,10)) = set the size of the boxplot 
    plt.subplot(2,2,1)    
    sns.boxplot(x='species',y='sepallengthcm',data=iris_df)
    plt.subplot(2,2,2)    
    sns.boxplot(x='species',y='sepalwidthcm',data=iris_df)     
    plt.subplot(2,2,3)    
    sns.boxplot(x='species',y='petallengthcm',data=iris_df)     
    plt.subplot(2,2,4)    
    sns.boxplot(x='species',y='petalwidthcm',data=iris_df)
    plt.savefig("Box_plot.png")
    plt.show()


Analyising the box plots, the sepal length and sepal width data results are close, with some overlap between all 3 species.   
However for the petal length and petal width, the Iris Setosa is visually clearly different from the Veriscolor and Virginica.   
The Iris Setosa petal length and petal width attributes data do not overlap with the Veriscolor and Virginica.  

![](Box_plot.png)  

##  3.3 Violinplot  

The Violinplot groups by species, similar to the boxplot it shows how the length and width vary according to the species.  
However the violinplot show the density of the results, the thinner part shows that there is less occurances whereas the fatter part conveys higher density or high occurences.  

The code for a Violinplot is similar to Boxplot, to have all showing on the one output requires a 2 x 2 (2 columns and 2 rows), therefore subplot(2,2) is required.   
The 3rd value in the subplot indicates where on the output the plot is shown, as follows 1 - Top Left, 2 - Top Right, 3 - Bottom Left, 4 - Bottom Right.  
On the plot the x axis is the species type, y axis is the attribute 

    plt.figure(figsize=(15,10))
    plt.subplot(2,2,1)
    sns.violinplot(x='species',y='petallengthcm',data=iris_df)
    plt.subplot(2,2,2)
    sns.violinplot(x='species',y='petalwidthcm',data=iris_df)
    plt.subplot(2,2,3)
    sns.violinplot(x='species',y='sepallengthcm',data=iris_df)
    plt.subplot(2,2,4)
    sns.violinplot(x='species',y='sepalwidthcm',data=iris_df)
    plt.show()

## 3.3 Scatterplot (Pairsplot)  

Scatter plot is very useful when we are analyzing the relationship between 2 features on x and y axis.
In seaborn library there is a pairplot function which is very useful to scatter plot all the features at once instead of plotting them individually.  

The pair plot used to figure out a distribution of single variables and the relationship between two variables.  
If the pair plot is given a solution for that as a clear understanding of each flower sets at a single graph.  
Each flower scatters plots represented in different colors.  

For each pair of attributes, we can use a scatter plot to visualize their joint distribution  
sns.pairplot(iris_df, hue="species", diag_kind="kde")  
plt.show()  

## 3.4 Correlation and Heatmaps  

A Heatmap is used to show correlation. 

To show the values on the heatmap, insert "annot = True" and use cmap to pick the colour palette of your choice 
The output shows that Sepal Width and Length are not correlated, and Petal Width and Length are highly correlated.  

    print(iris_df.corr())
    plt.figure(figsize=(15,10))
    sns.heatmap(iris_df.corr(), annot = True, cmap = 'rocket') 
    plt.show()

https://stackabuse.com/ultimate-guide-to-heatmaps-in-seaborn-with-python/  
https://www.kaggle.com/ash316/ml-from-scratch-with-iris  
http://www.cse.msu.edu/~ptan/dmbook/tutorials/tutorial3/tutorial3.html
https://www.c-sharpcorner.com/article/a-first-machine-learning-project-in-python-with-iris-dataset/  

# 4.0 Train and Validate the data (Machine learning)  

The Iris dataset can be used by a machine learning model to illustrate classification (a method used to determine the type of an object by comparison with similar objects that have previously been categorised).   
Once trained on known data, the machine learning model can make a predictive classification by comparing a test object to the output of its training data.

Steps To Be followed When Applying an Algorithm.  
1. Split the dataset into training and testing dataset.  
2. The testing dataset is generally smaller than training one as it will help in training the model better. I have chose a 75%:25% training:testing split.  
3. Select an algorithm based on the problem (classification or regression). 
4. Pass the training dataset to the algorithm to train it, use the .fit() method.  
5. Then pass the testing data to the trained algorithm to predict the outcome, use the .predict() method.  
6. Check the accuracy by passing the predicted outcome and the actual output to the model.
7. Check against other algorithms.  
8. Final model selection.  

~ Make note that am using the sklearn.datasets import load_iris

The preliminary step is to define the attributes or input group (i.e. 4 features sepal length, sepal width, petal length, petal width) as X=iris.data and define the target or output group (species) as y=iris.target.    

    X=iris.data
    y=iris.target

**Step 1 - Split the Datset**  
My first step was to split the dataset into training and testing dataset, I have chosen a 75%:25% split:
75% of the data will be training data - X_train, y_train for training the model
25% of the data will be testing data - X_test, y_test for testing the model     

    from sklearn.model_selection import train_test_split
    X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.25)

**Step 2 - Training and Testing Dataset shape**   
To show the shape/size of the train and test data samples
X_train is 75% of 150 = 112 rows of data in 4 columns (the 4 features/variables)
y_train is 75% of 150 = 112 rows of the species column
X_train is 25% of 150 = 38 rows of data in 4 columns (the 4 features/variables)
y_train is 25% of 150 = 38 rows of the species column   

    print("X_train shape: {}".format(X_train.shape))
    print("y_train shape: {}".format(y_train.shape))
    print("X_test shape: {}".format(X_test.shape))
    print("y_test shape: {}".format(y_test.shape))   

**Step 3 - Select an algorithm** 
I have chosen the k-nearest neighbours (knn) classifier as the algorithm to make a prediction of the species for sample data of one new data point.   
k is the number of nearest neighbours and is the core deciding factor. K is set by the user, we can consider any fixed number k of neighbors in the training.   
The algorithm calculates the distance between the new data point with the training examples.  
The model picks 'k' (as determined by the user) entries in the training data which are closest to the new data point and then is does a majority vote, that is it takes the most common species among those 'k' entries to be the class of the new data point.   
When k=1, the algorithm is know as the nearest neighbour algorithm.    
We can now make a prediction using the majority class among them. For our example, we will use one neighbor (k=1). 

**Step 4 - Pass the training set to the algorithm** 

I now use the fit method of the knn object, to train the algorithm with the training data X_train (containing the training data of the 4 features) and the training output y_train (containing the corresponding species), this builds up our model on the training set.  
We enter sample data (X_new) and show the shape of the data, it is one row (1 sample) with 4 columns of data (the 4 features/variables sepal and petal measurements).   

    knn = KNeighborsClassifier(n_neighbors=1)  
    knn.fit(X_train, y_train)  
    X_new = np.array([[5, 2.9, 1, 0.2]])  
    print("X_new.shape: {}".format(X_new.shape))   

**Step 5 - Predict Species**   

I now use the predict method of the knn object to predict the species of the sample data X_new and print the outcome. In the iris dataset, it has a species class of 0, also know as the setosa. 

    prediction = knn.predict(X_new)
    print("Prediction: {}".format(prediction))
    print("Predicted target name: {}".format(iris['target_names'][prediction]))  


**Step 6 - Check model accuracy** 

A question that remains is how can we trust the results of the model.  

The test data that was created was not used to build the model, but we do know the correct species for each iris in the test set.   
Therefore, we can make a prediction for each iris in the test data and compare it against its species, so we can know if the model is correctly predicting the species for a given flower.  
To measure how well the model works, we can obtain the accuracy of the number of flowers for which the right species was predicted.  

Using the X_test data containing the testing data (25% of the dataset) of the 4 features, I print out the prediction of the species using only the 4 features.  
And then compare the prediction of the species 'y_pred' to the actual species 'y_test'.   

    y_pred = knn.predict(X_test)
    print("Test set predictions:\n {}".format(y_pred))
    print("Test set score (np.mean): {:.2f}".format(np.mean(y_pred == y_test)))

Another way to do this would be to use the score method of the knn object, which will compute the test set accuracy 

    print("Test set score (knn.score): {:.2f}".format(knn.score(X_test, y_test)))



For this model, the accuracy on the test set is 0.97, which means the model made the right prediction for 97% of the irises in the given dataset,  
We can expect the model to be correct 97% of the time for predicting the species of new irises.  
This is a high level of accuracy and it means that our model may be trustworthy enough to use.  

While the iris dataset and classification is simple, it is a good example to illustrate how a machine learning problem should be approached and how useful the outcome can be. 


**Step 7 - Compare to other algorithms**   

An additional step that can be done is to spot check other algorithms to see their results. 
I will test 6 different algorithms, this is a good mixture of simple linear (LR and LDA), nonlinear (KNN, CART, NB and SVM) algorithms.  

    models = []
    models.append(('LR', LogisticRegression(solver='liblinear', multi_class='ovr')))
    models.append(('LDA', LinearDiscriminantAnalysis()))
    models.append(('KNN', KNeighborsClassifier()))
    models.append(('CART', DecisionTreeClassifier()))
    models.append(('NB', GaussianNB()))
    models.append(('SVM', SVC(gamma='auto')))

# evaluate each model in turn insert notes 
    results = []
    names = []
    for name, model in models:
        kfold = StratifiedKFold(n_splits=10, random_state=1, shuffle=True)
        cv_results = cross_val_score(model, X_train, y_train, cv=kfold, scoring='accuracy')
        results.append(cv_results)
        names.append(name)
        print('%s: %f (%f)' % (name, cv_results.mean(), cv_results.std()))

We can also create a plot of the model evaluation results and compare the spread and the mean accuracy of each model.  
A useful way to compare the samples of results for each algorithm is to create a box and whisker plot for each distribution and compare the distributions.

    plt.boxplot(results, labels=names)
    plt.title('Algorithm Comparison')
    plt.show()  

We can see that the box and whisker plots are squashed at the top of the range, with many evaluations achieving 100% accuracy, and some pushing down into the high 80% accuracies.  

# Make predictions on test/validation dataset 

**Step 8 - Final model selection**    


The results in the previous section suggest that the LDA was the most accurate model, I will use this model as the final model.  
Now we want to get an idea of the accuracy of the model on our validation set.  
This will give us an independent final check on the accuracy of the best model.  

I can fit the model on the entire training dataset and make predictions on the testing dataset.
    model = LinearDiscriminantAnalysis()
    model.fit(X_train, y_train)
    predictions = model.predict(X_test)

We can evaluate the predictions by comparing them to the expected results in the testing set and then calculate classification accuracy, as well as a confusion matrix and a classification report.  

    print(accuracy_score(y_test, predictions))
    print(confusion_matrix(y_test, predictions))
    print(classification_report(y_test, predictions))  

We can see that the accuracy is 1.0 or about 100% on the hold out dataset. The confusion matrix provides an indication of the errors made.
Finally, the classification report provides a breakdown of each class by precision, recall, f1-score and support showing excellent results (granted the validation dataset was small).  



https://medium.com/gft-engineering/start-to-learn-machine-learning-with-the-iris-flower-classification-challenge-4859a920e5e3
https://machinelearningmastery.com/machine-learning-in-python-step-by-step/
https://machinelearningmastery.com/make-predictions-scikit-learn/








https://kedro.readthedocs.io/en/stable/02_get_started/05_example_project.html
