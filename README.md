# deep-learning-challenge


Preprocessing and Explanation 

The purpose of this analysis is to predict the y-value (IS_SUCCESSFUL - whether or not the money was used effectively) so that we may better understand the success of future charity ventures. 

The target variable is the 'IS_SUCCESSFUL' field, since we want to know our prediction value given the other variables. 

The features, after deleting the 'EIN' and 'NAME' columns (which, as identifiers, have no real statistical purpose and can be considered neither targets nor features), are 'APPLICATION_TYPE', 'AFFILIATION',	'CLASSIFICATION', 'USE_CASE',	'ORGANIZATION',	'STATUS',	'INCOME_AMT',	'SPECIAL_CONSIDERATIONS',	'ASK_AMT'	and 'IS_SUCCESSFUL'. While I attempted to drop many of the columns with practice runs, deleting any of them seems to only make the accuracy worse. 

<img width="100%" alt="Targets and Features" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/f2fe7b70-19c5-4cff-8fe6-7b7ab438a824">

Most likely, 'EIN' and 'NAME' should be dropped because they are unlikely to bring any value to the analysis. However, there may be some value in leaving 'NAME' in the analysis, but due to a continuous technical glitch I was unable to run the program with 'NAME' included in later optimizations. 

<img width="100%" alt="Removing EIN and NAME columns" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/d2bb2a8e-5448-4993-8bf8-b3b6772b1f22">

The original model uses 3 layers, 80, 30, and 1 neurons in each respective layer, and the relu, relu, and sigmoid functions for each. 

<img width="100%" alt="Meta Data" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/15094217-e7f2-4be0-9322-7ecd72d9b040">

The original model did not acheive target performance, and in further optimizations I was only able to increase the accuracy to about 74%. (Explanation below.) 

<img width="100%" alt="First results" src="https://github.com/equitymarkets/deep-learning-challenge/assets/49753517/233573b0-3b7c-408e-8ea6-c2f08e4352f9">



Compiling, Training, and Evaluating the Model

In the original run, I acheived a final Epoch 100 accuracy of .7392 and an rough accuracy of .7341. This model used 80, 30, and 1 neurons for the respective input, hidden, and output layers. It deletes both the 'EIN' and 'NAME' columns since these variables are neither targets nor features. 'APPLICATION_TYPE' is binned so that values with less than 500 can all be in one 'Other' category. Similarly, for the 'CLASSIFICATION', I binned the 'Other' category at 1000, so values less than that would go into an 'Other' category for analysis. 

For attempted optimization 1, I dropped two more columns in addition to 'EIN' and 'NAME': 'STATUS' and 'SPECIAL_CONSIDERATION'. I changed the Other bins to be more inclusive: driving the 'APPLICATION_TYPE' cutoff from 500 to 1000 and the 'CLASSIFICATION' cutoff from 1000 to 2000. I added two hidden layers, both of the 'softcell' activation type, with 40 and 20 neurons. I drove the existing 'relu' layers from 80 to 160 neurons and 30 to 60 neurons. Finally, I added 100 epochs to the training session. Basically, I doubled everything. These changes drove down my column inputs (input_dim variable in the input layer) from 43 to 35. The changes did not help model accuracy, however, as the model saw a drop in final Epoch 200 accuracy to .7358 and a rough accuracy of .7250. 

Most ask amounts are for 5000. To get a better handle on the data, for attempted optimization 2 I simply dropped these rows altogether and ran the original criteria on the model. While I realize this does not provide a true prediction, I felt that dropping the most common value would give us a better idea of what we might be able to do to optimize the results in this or future runs. This also did not work to optimize the model, and gave an Epoch 100 accuracy value of .7073 and a rough accuracy of .6824.

For optimization 3 I started to see results. My optimization here, which cuts the threshold for the application_types and classifications down to 15 and 100, acheived an Epoch 100 accuracy value of .7399 and a rough accuracy of 

For optimization 4 I tried to apply everything I have learned about what works and what does not work for this dataset, to try to acheive over .7500. 

Summary 

Note: It is generally preferable not to repeat lines of code. In the Optimization file, most lines of code are repeated in each optimization trial, some subtle differences, some without. This is so the tester can clearly run each or any optimization from the same file without having to track down variables or pieces of data from the first optimization. 
