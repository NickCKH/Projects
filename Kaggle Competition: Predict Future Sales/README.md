## Predict Future Sales competition on Kaggle 

![Python 3.6](https://img.shields.io/badge/python-3.6-brightgreen)

This was a competition covered under the Advanced Machine Learning Specialization on Kaggle 
The goal was to predict total sales for every product and store for a Russian software firm: 1C Company

While the logic and evaluation metric of the competition target were simple, the competition was difficult for several reasons: 
- **Timeseries data**: This made coming up with a validation strategy challenging, especially with ensembling/model stacking techniques 
- **Different number of stores and products each month**: as stores would close and change their catalogue, the models had to be robust to tackle unseen products and store combinations 
- **Outlier stores**: Some stores had to be treated/removed due to either duplicate branches (franchise) or having data errors such as ridiculous prices on similar items in other stores 
- **Outlier time periods**: Due to the dataset spanning about half a decade, sales and pricing levels changed over time, and certain timeframes had to be ignored, and inflation had to be accounted for somehow

Was a really interesting competition for me, it was my competition involving timeseries data, and I tried model stacking for the first time. 

Some of the notable techniques incorporated/discarded you will see in the notebook are: 
1. **Cartesian product algorithm**: to get all possible store/product combinations 
2. **Translation library**: to translate russian product names to english 
3. **Deep categorical embedding**: to reduce dimensions of multiple column having high cardinality 
4. **Target encoding**: a very good feature, especially for timeseries data 
5. **Lags**: These are absolutely crucial for any timeseries contest and are usually amongst the top features, I used 6 different types of lags, with various lag intervals for each type, thats a ton of lag features.
6. **Seasonality**: This had decent importance given that timeseries data will have seasonality present somehow 
7. **Model stacking**: This was my first time implementing *stacking*, which involves: 
  - Having several 1st level models (GBDT, NN, Catboost, RR) which all extract different information from the features,  
  - Feeding the predictions of these models into 2nd level models (LR/NN) which aggregates the predictions combined with some second level features into a meta prediction. 
  This works simply because 1st level models cover each others' shortfalls, and the 2nd level models then take a step back and combine the best predictions of the models through a chosen aggregation method. 
  It was a nightmare to implement however, due to the timeseries nature of the dataset, essentially now we needed to have a rolling window for the 1st level models and validate on holdout sets, while training the 2nd level models on ytrain data of the rolling window from the 1st level models. Takes a while to grasp this concept. 
8. **Hyperopt tuning**: This was implemented on the first level models, I ran hyperopt to optimize the parameters of each 1st level model.

All in all this was a fantastic experience, glad to have picked up new techniques along the way, and cool ones at that. 
You can access the notebook here: 
https://github.com/NickCKH/Projects/blob/master/Kaggle%20Competition:%20Predict%20Future%20Sales/AML%20Data%20Comp%20-%20main%20-%20200727.ipynb
