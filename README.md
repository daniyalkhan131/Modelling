# Modelling

stacking and blending-

stacking just like bagging and boosting it is an esmeble technique
on kaggle mostly this used
it is very similar to voting ensemble, bascically extended version like thing
in stacking, output comming from base classifiers are provided to a classifier that
lear from those and output and then predict. in voting we do voting of output from base
classifier while in this we put those base output to a different model(called meta model).

step1- train base models
step2- calc predictions using base models
step3- train meta model on the new data

for prediction, give i?p to base model then give output to meta model

stacking vs bagging?boosting
-base model differwnt in stcaking
-training  (o/p from base model)

problem-
we do training and prediction on the same data for base model learning so it arise
problem of overfitting
	methods to avoid this-
		hold out method
			take 80% for train and 20% for test then out of 80% of train
			take 80% for taining base model and remaining for meta model
			when we use this then called as Blending
			
			train base model on train data, train meta model on validation data
			then testing done on test data

		k-fold method
			using this then called as Stacking
			divide the full data into train and test then do divide train data
			into k equal parts and with k-1 parts use that for training 1stbase
			model then predict using remainig part then take next k-1 parts and
			do training of same 1st model and do this for all one parts for
			prediction. if we have 800 rows in train data then we gor here 800
			prediction value for 1st model, do same thing with 2nd base model
			and get 800 rows then same for 3rd base model,
			now we have 800 of all base model prediction so give that to meta 
			model along with train target and do training of that.
			here meta model is trained before base models
			above base model trainings we dont consider as they all are trained
			k-1 times.
			Now train base models by directly giving them train data


multi layer stacking
it is like making a neural network, each neuron can be different model
take first layer models be m1 m2 m3 the all giving output to 2nd layer model m4 m5 m6
and in 3rd layer m6 is present
divide data into train and test
then divide training data into d1 d2 d3 parts
train m1 m2 m3 using d1 and then do prediction using d2 of these 3 models
then do training of m4 m5 m6 using predictions by m1 m2 m3 and target of d2
and then do prediction on m4 m5 m6 using of d3 and then do training of m7 model using
predictions by m4 m5 m6 and target of d3 
this is blending tech.
think how implemented with k fold(homework)

simple stacking is present in sklearn
stack method for telling in what form o/p from base model go to i/p in meta model as model
are different so we need to tell, if auto then o/p goes acc. to model used
passthrough True is for sending orginial data alog with prediction of base model
but generally it is False
 
