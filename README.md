# deep-learning-challenge


## Preprocessing and Explanation 

The purpose of this analysis is to predict the y-value (IS_SUCCESSFUL - whether or not the money was used effectively) so that we may better understand the success of future charity ventures. 

The target variable is the 'IS_SUCCESSFUL' field, since we want to know our prediction value given the other variables. 

The features, after deleting the 'EIN' and 'NAME' columns (which, as identifiers, have no real statistical purpose and can be considered neither targets nor features), are 'APPLICATION_TYPE', 'AFFILIATION',	'CLASSIFICATION', 'USE_CASE',	'ORGANIZATION',	'STATUS',	'INCOME_AMT',	'SPECIAL_CONSIDERATIONS',	'ASK_AMT'	and 'IS_SUCCESSFUL'. While I attempted to drop many of the columns with practice runs, deleting any of them seems to only make the accuracy worse. 

<img width="100%" alt="Targets and Features" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/f2fe7b70-19c5-4cff-8fe6-7b7ab438a824">

Most likely, 'EIN' and 'NAME' should be dropped because they are unlikely to bring any value to the analysis. However, there may be some value in leaving 'NAME' in the analysis, but due to a continuous technical glitch I was unable to run the program with 'NAME' included in later optimizations. 

<img width="100%" alt="Removing EIN and NAME columns" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/d2bb2a8e-5448-4993-8bf8-b3b6772b1f22">

The original model uses 3 layers, 80, 30, and 1 neurons in each respective layer, and the relu, relu, and sigmoid functions for each. 

<img width="100%" alt="Meta Data" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/15094217-e7f2-4be0-9322-7ecd72d9b040">

The original model did not acheive target performance, with an Epoch 100 accuracy of .7389 and a rough result accuracy of .7313. In further optimizations I was only able to increase the accuracy to about 74%. (Explanation below.) 

<img width="100%" alt="First results" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/233573b0-3b7c-408e-8ea6-c2f08e4352f9">

Below I highlight some of the steps that were taken to increase accuracy in the models. 

Some ideas were:
* Change the amount of epochs for testing
* Change the amount of column inputs (summed up in the input_dim parameter in the first layer). 
* Change the amount of layers, activation functions of the layers, and neurons within the layers. 
* Drop or keep different columns, notably ones that may not directly relate to the analysis at hand. 

## Compiling, Training, and Evaluating the Model

In the original run, I acheived a final Epoch 100 accuracy of .7389 and an rough accuracy of .7313. This model used 80, 30, and 1 neurons for the respective input, hidden, and output layers. It deletes both the 'EIN' and 'NAME' columns since these variables are neither targets nor features. 'APPLICATION_TYPE' is binned so that values with less than 500 can all be in one 'Other' category. Similarly, for the 'CLASSIFICATION', I binned the 'Other' category at 1000, so values less than that would go into an 'Other' category for analysis. Below are the loss and accuracy charts:

<img width="60%" alt="Loss" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/071c356a-6ada-4f0c-948c-df5b7669540f">

<img width="60%" alt="Accuracy" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/c2600944-3eb9-4aef-8334-08a7117fc8f3">


For attempted optimization 1, I dropped two more columns in addition to 'EIN' and 'NAME': 'STATUS' and 'SPECIAL_CONSIDERATION'. I changed the Other bins to be more inclusive: driving the 'APPLICATION_TYPE' cutoff from 500 to 1000 and the 'CLASSIFICATION' cutoff from 1000 to 2000. I added two hidden layers, both of the 'softcell' activation type, with 40 and 20 neurons. I drove the existing 'relu' layers from 80 to 160 neurons and 30 to 60 neurons. Finally, I subtracted 50 epochs from the training session. Basically, I doubled everything and halved the epochs. These changes drove down my column inputs (input_dim variable in the input layer) from 43 to 35. The changes did not help model accuracy, however, as the model saw a drop in final Epoch 200 accuracy to .7331 and a rough accuracy of .7252. 

<img width="60%" alt="Loss" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/afdad1fe-2e60-42e0-aa1f-6c84cc7c4339">

<img width="60%" alt="Accuracy" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/e985cff2-4568-445c-9c95-3da91b455e24">


Most ask amounts are for 5000. To get a better handle on the data, for attempted optimization 2 I simply dropped these rows altogether and ran the original criteria on the model. While I realize this does not provide a true prediction, I felt that dropping the most common value would give us a better idea of what we might be able to do to optimize the results in this or future runs. I used other inputs from the original model-43 binary columns, 3 layers, relu-relu-sigmoid, and 'EIN' and 'NAME' deletions. This also did not work to optimize the model, and gave an Epoch 100 accuracy value of .7073 and a rough accuracy of .6824.

<img width="60%" alt="Loss" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/386edbd3-cdb2-4aaf-83de-7c14955c6d58">

<img width="60%" alt="Accuracy" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/d35cf12e-cfcb-4a0d-9c6b-dc4d57159ce3">


For optimization 3 I started to see results. My optimization here, which cuts the threshold for the application_types and classifications down to 15 and 100, acheived an Epoch 100 accuracy value of .7397 and a rough accuracy of .7307. 

<img width="60%" alt="Loss" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/a98e7cc6-d2c5-4f27-8925-e4f88e241898">

<img width="60%" alt="Accuracy" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/82640f21-48c0-43a2-80d8-bbe84f0e8150">

For optimization 4 I tried to apply everything I have learned about what works and what does not work for this dataset, to try to acheive over .7500. First I tried to leave the 'NAME' column in, in thinking that name may have something to do with success over a large dataset. But due to a program crash with this line of code, and results that were hardly improved (less than .005) I removed this optimization. In the future I may find a way to optimize the code without the 'NAME' category. In the final run I added a layer and used Fibonacci numbers for the neurons in each of the first three layers-13, 21, and 34 (1 for output). I did not improve the model over my best score however, and acheived .7379 on the final Epoch 100 and .7298 for rough result. 

<img width="60%" alt="Screenshot 2023-06-05 at 12 44 34 AM" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/3daf5842-282d-4444-8156-18cb5d4a3f76">

<img width="60%" alt="Screenshot 2023-06-05 at 12 44 41 AM" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/f40e4af0-d8f7-4cfd-9727-57bdd8cff1b0">

## Summary 

This was a learning experience, from first using Google Colab to increased usage of PySpark, to using these models for the first time. I learned about the relu activation function (rectified linear unit), which is a newer model and considered optimal in most cases. Relu is the default activation function for the Perceptron architecture and is linear for half of the model, and non-linear for the other half. Older functions, such as tanh and sigmoid are used less in the present, because they are not user-friendly to many layers and can saturate the data (move extreme values to 1 (positive) and 0 or -1 (negative). Softmax uses vectors of probabilities, which sounded promising, but didn't acheive good results in this analysis. I returned to relu functions, with sigmoid at the output, in later runs. 

My later models will work with binning different values and playing with the bin sizes, as well as possibly adding back in the 'NAME' column. In addition, I will work with the number of neurons in each activation layer. With a little work I should be able to acheive the target accuracy of 75%, given that I have gotten to 74% in a previous model. 

Note: It is generally preferable not to repeat lines of code. In the Optimization file, most lines of code are repeated in each optimization trial, some subtle differences, some without. This is so the tester can clearly run each or any optimization from the same file without having to track down variables or pieces of data from the first optimization. 
