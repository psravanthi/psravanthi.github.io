
Predicting movie gross revenue

Can you predict the success or more so, the total gross of a movie at the box office? 
What ensures the financial success of a movie? Is it the genre, or is it the star power of a certain actor? 
I tried to answer some of these questions by tinkering around with data from boxofficemojo.com and IMDB.com

In this analysis, I scrapped 10 years of movie data from boxofficemojo.



Scrapped the following details from the movie page
Insert screen shot

The actor/director/writer/producer's information was collected from their respective pages

Insert screen shoot

I went ahead and built a linear regression on the following features:
Genre
Run Time
MPAA - Rating
Budget
Number of screens
Number of movies
Actors previous avg. gross
Producer previous avg. gross
Director previous avg. gross
Writer previous avg. gross

Prima facie the model looked good. Too good to be true! I had an R-squared of around 0.83 ! And, my coefficients were of the order
e+07 making the model too sensitive to changes. Did i overfit my data?

I divided the model into train and test data and ran the model on the data. The R-squared dropped to 0.63. I surely did overfit 
my model. 

I went on to check if I have some more problems with the data and the model, in general. The following results caught my eye:
Prob(Omnibus):  0.000
Prob(JB):   0.00
The p-value is less than 0.05, rejecting the null hypothesis of having a normally distributed data
(Insert graphs)
 
 I have some options to care of this. I can either collect more data, so that the data follows normal distribution by central
 limit theorem or I can try to transform the data so that it follows a normal distribution. I chose to apply a logarithmic
 transformation.
 
 Insert graphs.
 
 Having taken care of the non-normal distribution, I have one more problem on my hand. Overfitting !
 Regularization seems to be a plausible solution. So, Lasso or Ridge it is ! 
 I further divided my data - Train data, validation data, test data
 
 Model formulation:
 At each iteration I reduced the number of model parameters by taking out variables that are not significant, and it 
 improves the model performance both on the training set and test set
 After multiple iterations and cross validations, i came up with a model that seem to be consistent with the train 
 and test data.
 
 My results :
 Method : Ridge Regression with 10-fold cross validation

R-square on test data : 0.78
Mean -squared error : 0.9758

Method : Lasso Regression with 10-fold cross validation

R-square on test data : 0.78
Mean -squared error : 0.9755

Both the models seems to have similar results. I went ahead with Lasso, as i want to get rid of less significant variables.

The significant features per the model are :
positive :<insert>
negative:<insert>

So, how well did the model perform on the test data?
<insert>
Got 20 out of 25 right. Not so bad !
 


 
