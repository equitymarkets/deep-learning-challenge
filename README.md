# deep-learning-challenge

In the original run, I acheived a final Epoch 100 accuracy of .7392 and an rough accuracy of .7341.

For attempted optimization 1, I dropped two more columns in addition to 'EIN' and 'NAME': 'STATUS' and 'SPECIAL_CONSIDERATION'. I changed the Other bins to be more inclusive: driving the 'APPLICATION_TYPE' cutoff from 500 to 1000 and the 'CLASSIFICATION' cutoff from 1000 to 2000. I added two hidden layers, both of the 'softcell' activation type, with 40 and 20 neurons. I drove the existing 'relu' layers from 80 to 160 neurons and 30 to 60 neurons. Finally, I added 100 epochs to the training session. Basically, I doubled everything. These changes drove down my column inputs (input_dim variable in the input layer) from 43 to 35. The changes did not help model accuracy, however, as the model saw a drop in final Epoch 200 accuracy to .7358 and a rough accuracy of .7250. 

For attempted optimization 2, 




Note: It is generally preferable not to repeat lines of code. In the Optimization file, most lines of code are repeated in each optimization trial, some subtle differences, some without. This is so the tester can clearly run each or any optimization from the same file without having to track down variables or pieces of data from the first optimization. 
