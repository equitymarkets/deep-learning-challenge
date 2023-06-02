# deep-learning-challenge


Overview of the analysis: Explain the purpose of this analysis.

The purpose of this analysis is to predict charity funding. 

Results: Using bulleted lists and images to support your answers, address the following questions:

Data Preprocessing

What variable(s) are the target(s) for your model?
What variable(s) are the features for your model?
What variable(s) should be removed from the input data because they are neither targets nor features?
Compiling, Training, and Evaluating the Model

How many neurons, layers, and activation functions did you select for your neural network model, and why?
Were you able to achieve the target model performance?
What steps did you take in your attempts to increase model performance?




In the original run, I acheived a final Epoch 100 accuracy of .7392 and an rough accuracy of .7341.

For attempted optimization 1, I dropped two more columns in addition to 'EIN' and 'NAME': 'STATUS' and 'SPECIAL_CONSIDERATION'. I changed the Other bins to be more inclusive: driving the 'APPLICATION_TYPE' cutoff from 500 to 1000 and the 'CLASSIFICATION' cutoff from 1000 to 2000. I added two hidden layers, both of the 'softcell' activation type, with 40 and 20 neurons. I drove the existing 'relu' layers from 80 to 160 neurons and 30 to 60 neurons. Finally, I added 100 epochs to the training session. Basically, I doubled everything. These changes drove down my column inputs (input_dim variable in the input layer) from 43 to 35. The changes did not help model accuracy, however, as the model saw a drop in final Epoch 200 accuracy to .7358 and a rough accuracy of .7250. 

Most ask amounts are for 5000. To get a better handle on the data, for attempted optimization 2 I simply dropped these rows altogether and ran the original criteria on the model. While I realize this does not provide a true prediction, I felt that dropping the most common value would give us a better idea of what we might be able to do to optimize the results in this or future runs. This also did not work to optimize the model, and gave an Epoch 100 accuracy value of .7073 and a rough accuracy of .6824.

For optimization 3 I started to see results. My optimization here, which cuts the threshold for the application_types and classifications down to 15 and 100, acheived an Epoch 100 accuracy value of .7399 and a rough accuracy of 

For optimization 4 I tried to apply everything I have learned about what works and what does not work for this dataset, to try to acheive over .7500. 

Note: It is generally preferable not to repeat lines of code. In the Optimization file, most lines of code are repeated in each optimization trial, some subtle differences, some without. This is so the tester can clearly run each or any optimization from the same file without having to track down variables or pieces of data from the first optimization. 
