# Neural Network Charity Analysis

## Overview

In this project, we are looking at the funds distributed by a charitable organization and the effective use of those funds. Our purpose is to find a way to best predict whether or not those transactions are fraudulent by using a neural network to dermine patterns and flag possible future fraud.  In order to do this, we are taking a records of past transactions and the factors that could possibly be determined to flag those that are fraud and building and training a model to determine the likely hood that requests with a similar profile could also be fruadulent.

## Results

* **Data Processing**
  * The data set contains a field for "Is Successful?" which is our target. This is the question we are asking of each transaction. If the request is funded, will it be successful
  
  * The Features of this model include Application type and Classification which are internal codes used to bucket the request types, the affiliation of the request, Use case for the request, the request amount, the income amount of the requestee's organization, type of oganization, active status, and if there are any special considerations
  
  See the list below:
  
   ![Features, target](https://user-images.githubusercontent.com/109319148/205509441-448c2712-de79-4f1c-acfb-e57d9e9291c8.png)
   
   * The list of features originally included EIN and Name as well, which were not useful for analysis and removed. Additionally, the ask amount and special considerations are noisy and are extra variables that are likely confusing our model and could be removed
   
* **Compiling, Training, and Evaluating the Model**

  * Originally, we built the model with 2 hidden layers. The first one had 80 neurons and the second had 30. We used Relu as the activation function. This made sense because we have non negative values. The output layer is using the sigmoid activation which works well for classification. In total, there were 5981 total parameters
  
  ![1st module](https://user-images.githubusercontent.com/109319148/205511364-d71dc9e9-88d8-4e36-8188-f04f691cdde7.png)
  
  * We were not able to achieve a 75% accuracy level 
   ![Screenshot 2022-12-04 143252](https://user-images.githubusercontent.com/109319148/205511404-32be679b-aeb9-4911-8656-86ecf82d9f5b.png)
   
   * In order to optomize the model, I looked at the Ask Amount column. The denisity was really centered around 1 single value of $5,000 and did not seem to help us determine if the request was fraudulent. I had originally tried to bin these values, but found that removing it all together worked just as well. In addition, special considerations was also removed to help remove noise from the model. I reran our original model with this change and did not achieve 75% accuracy.
   
  ![2](https://user-images.githubusercontent.com/109319148/205511557-f5712afc-578b-4947-8cdf-b06f623f4c9d.png)
  
   * I decided to add a third layer and increase the neurons. There are many features and wanted to ggive the model more layers and neurons to see if that would give it more to train. This did not increase accuracy, and actually saw it go down. 

   ![3 layers](https://user-images.githubusercontent.com/109319148/205511623-4f77fc77-429e-47eb-891d-c34407b03385.png)
   

   ![3](https://user-images.githubusercontent.com/109319148/205511642-5f66bf5b-3af7-4548-ae99-703ca140c35e.png)

* I changed the avtivation function to tanh to see if this would help approaching how the model is working through the data. My accuracy score is still not 75% and went down again. 
   ![4](https://user-images.githubusercontent.com/109319148/205511693-f9ce4f0f-8d2e-4e86-bdf6-dcbfff08ad75.png)
   

  ![4 acccuracy](https://user-images.githubusercontent.com/109319148/205511713-f7555a8d-5a67-4245-b7f3-75f243df199b.png)


## Summary
   Overall, an accuracy score of 70+% is better than a coin flip and could give the charity a better idea of which requests require more consideration. There are many features in this model, and the "black box" of deep learning does make it difficult without a lot of trial and error to be able to see which ones are contributing the most to our accuracy score. Since this is a binary classification where we know the output, it might be better and simpler to go with a supervised machine learning model. I would suggest a logistic regression. This would also allow us to look at the coefficients and remove the right noise from the model in the features. 

