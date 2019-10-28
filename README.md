input data: 

company_feature = [key:cid,feat_1,...,featN]
location_feature = [key:bid,feat_1,...,featM]

corresponding file link: https://drive.google.com/drive/folders/1eOzqzBmGu0DLxuXrtOJ_F7dGsOQ0x5Ww?usp=sharing

output: score of company and location

file:

1. linkCompanyAndLocation.ipynb

	Assign each company a location by geo information, if the distance between company and location is less than 1km.

2.	LR pipeline.ipynb

	Prediction model test.
	Data normalization is done.
	Predict the score of company and location with their feature directly: [ company_feat, location_feat], using Logistic Regression.

3.	gbdt_pipeline.ipynb

	 Model test.
	 Data normalization is done.
	 Predict the score of company and location with their feature directly: [ company_feat, location_feat], using Gradient Boosting Tree.

4. unsupervised learning pipeline.ipynb

	Prediction model test.
	Data normalization is done.
	Predict the score of company and location by projecting each building into company feature space, which means represent each building with companies inside it.

5. unsupervised scorecard generator.ipynb

	Generate the score of company and location through the whole data.
	Because the calculation is too big in some city, we slice the distance matrix into several rows to make it work.

6. LR pipeline with unsupervised score.ipynb

	Prediction model test.
	Data normalization is done.
	Predict the score of company and location with their features and score of unsupervised result: [ company_feat, location_feat, score], using Logistic Regression.
	To prevent data leak, if the company is in one location, then their score will be calculated without that company.

7. LR cross feature.ipynb

	Prediction model test.
	Data normalization is done.
	Predict the score of company and location with their features and cross-feature: [ company_feat, location_feat, company_x_location_feat ], using Logistic Regression.

8. standard_test_unsupervised_learning.ipynb, standard_test_supervised_learning_lr.ipynb, standard_test_supervised_learning_lr_ensemble.ipynb
	
	Standard test for unsupervised/supervised method, with identical testset.
	Each company from testset are compared with all the locations in that city.
	Both auc of roc and topk-recalled precision is evaluated.
	Each company in testset is invisible to trainset.
	During the procedure of ensembling, in order to avoid information leak, each company is dropped from his own building when calculating the similarity score.


