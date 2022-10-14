## Title : LDA and QDA as generative classifiers
- LDA is a very common dimensionality reduction technique, which projects the data along the directions of mean and tries to maximize that distance. This property can also be exploited to build classifiers that separate data based on the mean and variance such that the interclass scatter is maximum.

### Mathematical Intuition
Given input **X** feature vectors and output classes **Y**, for any generative model, our aim is to model the joint probability distribution of X and Y i.e. **_P(X,Y)_**, given a set of parameters **W**, i.e. P(X,Y|W).

The model is generative because we can always generate new data points as long as we know the distribution parameters.

We know that : **_P(X,Y)_** = **_P(X|Y)_** **_P(Y)_**.
Similarly, **_P(X,Y|W)_** = **_P(X|Y,W)P(Y|W)_**
    - Now we need to find ways to compute he probability : P(X|Y,W) and P(Y). Since W is fixed once we have identified a correct model, we just need to find ways to compute : P(X|Y) and P(Y).
    - For given input data (X) and labels Y, P(Y) is a simple counting problem.

Now we need to determine ways to calculate P(X|Y). If we assume that this distribution is Gaussian in nature (i.e. have a prior belief that the input data is Gaussian), then we can model this distribution with a mean and covariance per class distribution i.e. **P(X|Y= yi) where yi = {Set of valid output classes}.**

For example, if we have two different classes, Then 
![image.png](/img/img6.png)
where,
![image.png](/img/img5.png)
- These two equations can be simply calculated using the Gaussian formula.
    - i.e. ![image.png](/img/img4.png)
    - Now there are two different ways we can approach.

- For LDA, we assume that each of the class have same covariance i.e. ![image.png](/img/img3.png)
- For QDA, we assume that each of the class have different covariance i.e. ![image.png](/img/img2.png)
    - Hence, it is important to know the covariance of your data before applying LDA or QDA.


Now to predict our outcomes , We know that following equation holds true:
        - ![image.png](/img/img1.png)
    - We know the mean, variance parameters, hence we can simply plug the values in this equation.
    
Demo:
    - Here, I generate two random gaussian samples of dimension = 2, classes = 2 with same and different covariances. As expected QDA applies well in both the cases, however, LDA applies well for only the first case.
    - ![image.png](/img/img7.png)
    - 
    - Github Link :
    
