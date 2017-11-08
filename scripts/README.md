## Off-the-shelf R scripts
These ready-to-use R scripts can easily be added to your R-enabled MicroStrategy environment. Simply save them to your desktop or Intelligence Server and reference them with a MicroStrategy metric.

#### Contents
| Forecasting          | Classification      | Descriptive          |
| -------------------- | ------------------- | -------------------- |
| [ARIMA][arima]                | [k-Nearest Neighbors][knn] | [k-Means Clustering][kcluster]   |
| [Seasonal Forecasting][seasforecast] | [Neural Network][nn]      | [k-Medoids Clustering][kmedoids] |
| [Stepwise Regression][stepreg]  | [Naive Bayes][nb]         | [Pairwise Correlation][pairwise] |
| [Survival Analysis][survival]    | [Random Forest][rf]       |                      |
|                      | [Stepwise Logistic Regression][steplogreg] |             |

#### ARIMA
One of the most common applications of predictive analytics is to forecast time-based data. This analytic uses the Auto-Regressive Integrated with Moving Average (ARIMA) algorithm to project a sequence of values ahead into the future, based on the assumption that data points taken over time may have an internal structure that can be measured. While ARIMA tends to be esoteric and complex, this analytic uses the “auto.arima” function from R’s “forecast” package to search through a variety of possible models in order to find the best one. Not only does this script generate the expected forecast values, it also provides outputs based on confidence bands, nominally set at 80% and 95% confidence levels.

![arima_img]
##### Metric Expression
`RScript<_RScriptFile="ARIMA.R", _InputNames="Target", SortBy=(Month), _Params="CycleLength=12, Horizon=12, Conf1=80, Conf2=95, ImageName='', FileName=''">(Target)`
* [RScript][arima_script]
* [Documentation][arima_doc]
* [Back to the top][lnk_top]

#### Seasonal Forecasting
One of the most common applications of predictive analytics is to forecast time-based data. This analytic uses R’s ordinary least squares regression algorithm to fit the best curve that captures the general trend and seasonal variability of numerical data so it can use to predict future values.

![seasforecast_img]
##### Metric Expression
`RScript<_RScriptFile="SeasonalForecasting.R", _InputNames="Target, Trend, Season", _Params="FileName=''">(Target, Trend, Season)`
* [RScript][seasforecast_script]
* [Documentation][seasforecast_doc]
* [Back to the top][lnk_top]

#### Stepwise Regression
Stepwise Linear Regression is a variant on classical Linear Regression in which variables are only included in the model if they have a significant effect.

##### Metric Expression - Forecast returns the predictions from the model
`RScript<_RScriptFile="StepwiseRegression.R", _InputNames="Target, Vars", _Params="FileName='StepwiseRegression', Stepwise=TRUE">(Target, Vars)`
* [RScript][stepreg_script]
* [Documentation][stepreg_doc]
* [Back to the top][lnk_top]

#### Survival Analysis
Survival Analysis can be used to predict the probability of an event occuring, such as a component failure or a customer being lost. This analytic uses the Cox Regression algorithm to quantify the effect that each independent variable has on the likelihood that such an event will occur at some point in the future.

##### Metric Expression - Risk returns the risk of an event occurring relative to the average 
`RScript<_RScriptFile="Survival.R", _InputNames="Time, Status, Vars", _Params="TrainMode=FALSE, FileName='Survival'">(Time, Status, Vars)`
* [RScript][survival_script]
* [Documentation][survival_doc]
* [Back to the top][lnk_top]

#### k-Nearest Neighbors
k-Nearest Neighbors (kNN) is a simple classification technique that is unique in the sense that no model is explicitly trained. In the kNN process, two datasets are read in: the training dataset in which the dependent variable is already known, and the test dataset in which the dependent variable is unknown. Classifications for the test set are made by determining the k most similar records in the training dataset (known as neighbors) and returning the majority vote amongst those neighbors.

##### Metric Expression - Class returns the predicted class as a string
`RScript<_RScriptFile="kNN.R", _InputNames="ID, Target, Training, Vars", _Params="TrainIncluded=TRUE, k=1, FileName='kNN', Seed=42">(ID, Target, Training, Vars)`
##### Metric Expression - ClassId returns the predicted class as a number
`RScript<_RScriptFile="kNN.R", _InputNames="ID, Target, Training, Vars", _OutputVar="ClassId", _Params="TrainIncluded=TRUE, k=1, FileName='kNN', Seed=42">(ID, Target, Training, Vars)`
* [RScript][knn_script]
* [Documentation][knn_doc]
* [Back to the top][lnk_top]

#### Neural Network
Neural Network is an advanced machine learning classification technique wherein a model is constructed that aims to simulate the thought process performed by the human brain. A model consists of “neurons” that are interconnected by an activation function. Every record is then passed through the network from the appropriate input neuron to the proper output neuron through a series of weights and transformations defined by the activation function.

![nn_img]
##### Metric Expression - Class returns the predicted class as a string
`RScript<_RScriptFile="NeuralNetwork.R", _InputNames="Target, Vars", _Params="FileName='NeuralNetwork', TrainMode=TRUE, NumLayer=3, Seed=42">(Target, Vars)`
##### Metric Expression - ClassId returns the predicted class as a number
`RScript<_RScriptFile="NeuralNetwork.R", _InputNames="Target, Vars", _OutputVar="ClassId", _Params="FileName='NeuralNetwork', TrainMode=TRUE, NumLayer=3, Seed=42">(Target, Vars)`

* [RScript][nn_script]
* [Documentation][nn_doc]
* [Back to the top][lnk_top]

#### Naive Bayes
Naïve Bayes is a simple classification technique wherein the Naïve assumption that the effect of the value of each variable is independent from all other variables is made. For each independent variable, the algorithm then calculates the conditional likelihood of each potential class given the particular value for that variable and then multiplies those effects together to determine the probability for each class. The class with the highest probability is returned as the predicted class.

![nb_img]
##### Metric Expression - Class returns the predicted class as a string
`RScript<_RScriptFile="NaiveBayes.R", _InputNames="Target, Vars", _Params="TrainMode=TRUE, FileName='NaiveBayes', Correction=1">(Target, Vars)`
##### Metric Expression - ClassId returns the predicted class as a number
`RScript<_RScriptFile="NaiveBayes.R", _InputNames="Target, Vars", _OutputVar="ClassId", _Params="TrainMode=TRUE, FileName='NaiveBayes', Correction=1">(Target, Vars)`

* [RScript][nb_script]
* [Documentation][nb_doc]
* [Back to the top][lnk_top]

#### Random Forest
Random Forest is an advanced classification technique wherein the training dataset is used to construct many independent decision trees. Every record is then passed into each individual decision tree for classification, and the class that is predicted by the majority of those decision trees is returned as the predicted class for that record.

![rf_img]
##### Metric Expression - Class returns the predicted class as a string
`RScript<_RScriptFile="RandomForest.R", _InputNames="Target, Vars", _Params="TrainMode=TRUE, FileName='RandomForest', NumTree=750, NumVar=3, Seed=42">(Target, Vars)`
##### Metric Expression - ClassId returns the predicted class as a number
`RScript<_RScriptFile="RandomForest.R", _InputNames="Target, Vars", _OutputVar="ClassId", _Params="TrainMode=TRUE, FileName='RandomForest', NumTree=750, NumVar=3, Seed=42">(Target, Vars)`

* [RScript][rf_script]
* [Documentation][rf_doc]
* [Back to the top][lnk_top]

#### Stepwise Logistic Regression - Probability returns the predicted probability for each record
Stepwise Linear Regression is a variant on classical Linear Regression in which variables are only included in the model if they have a significant effect.

##### Metric Expression
`RScript<_RScriptFile="StepwiseLogistic.R", _InputNames="Target, Vars", _Params="FileName='StepwiseLogistic', Stepwise=TRUE">(Target, Vars)`
* [RScript][steplogreg_script]
* [Documentation][steplogreg_doc]
* [Back to the top][lnk_top]

#### k-Means Clustering
Using the K-Means algorithm, this analytic clusters records "by their nature" so that records within a cluster have more in common with each other than with those records in the other clusters. Each cluster is defined by a central point, it's "mean".

![kcluster_img]
##### Metric Expression
`RScript<_RScriptFile="kMeansClustering.R", _InputNames="Vars", _Params="Exact_k=4, Max_k=10, FileName='', Seed=42">(Vars)`
* [RScript][kcluster_script]
* [Documentation][kcluster_doc]
* [Back to the top][lnk_top]

#### k-Medoids Clustering
Using the K-Medoids algorithm, this analytic clusters records "by their nature" so that records within a cluster have more in common with each other than with those records in the other clusters. Each cluster is defined by a prototypical record, it's "medoid".

![kmedoids_img]
##### Metric Expression - Cluster returns the cluster to which the record belongs
`RScript<_RScriptFile="kMedoidsClustering.R", _InputNames="Vars", _Params="Exact_k=4, Max_k=10, FileName='', Seed=42">(Vars)`
##### Metric Expression - Medoids returns the cluster if a record is the medoid of that cluster, 0 otherwise
`RScript<_RScriptFile="kMedoidsClustering.R", _InputNames="Vars", _OutputVar="Medoids", _Params="Exact_k=4, Max_k=10, FileName='', Seed=42">(Vars)`

* [RScript][kmedoids_script]
* [Documentation][kmedoids_doc]
* [Back to the top][lnk_top]

#### Pairwise Correlation
PairwiseCorr measures the correlation between pairs of numeric variables to show how they behave with respect to each other. The primary output of this analytic is a correlation plot and a correlation table that contain the correlations of the variables when taken in pairs.

![pairwise_img]
##### Metric Expression
`RScript<_RScriptFile="PairwiseCorr.R", _InputNames="Labels, Vars", _Params="HasLabels=TRUE, WindowSize=0, ImageName='PairwiseCorr', FileName='PairwiseCorr'">(Labels, Vars)`
* [RScript][pairwise_script]
* [Documentation][pairwise_doc]
* [Back to the top][lnk_top]


## How to use these scripts in a MicroStrategy dashboard
These R Analytics are deployed to MicroStrategy as metrics by copying the metric expressions provided here into any MicroStrategy Metric Editor. The shelf includes metric expressions for Version 1 of the R Integration Pack as well as variations that take advantage of the new features in Version 2.

Version 2 of the R Integration Pack makes it even simpler for end-users control the analytic's execution thanks to the _Params parameter that allows function parameters to be referenced by name using a string of name-value pairs. This is in addition to the original set of 27 pre-defined parameters (9 boolean, 9 numeric and 9 string).

After you've copied the metric expression for the analytic you wish to deploy:
1. Paste the Metric Expression into any MicroStrategy metric editor
2. Match analytic's inputs and function parameters for your application
3. Name and save the metric so it can be added to any MicroStrategy report or dashboard

## Disclaimers
This page provides programming examples.  MicroStrategy grants you a nonexclusive copyright license to use all programming code examples from which you can use or generate similar function tailored to your own specific needs.  All sample code is provided for illustrative purposes only. These examples have not been thoroughly tested under all conditions. MicroStrategy, therefore, cannot guarantee or imply reliability, serviceability, or function of these programs.  All programs contained herein are provided to you "AS IS" without any warranties of any kind. The implied warranties of non-infringement, merchantability and fitness for a particular purpose are expressly disclaimed.


[lnk_top]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#off-the-shelf-r-scripts>

[arima]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#arima>
[arima_script]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_ARIMA.R>
[arima_doc]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_ARIMA.pdf>
[arima_img]: https://github.com/MicroStrategy/RIntegrationPack/blob/master/assets/RShelf_ARIMA.png

[seasforecast]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#seasonal-forecasting>
[seasforecast_script]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_SeasonalForecasting.R>
[seasforecast_doc]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_SeasonalForecasting.pdf>
[seasforecast_img]: https://github.com/MicroStrategy/RIntegrationPack/blob/master/assets/RShelf_SeasonalForecast.PNG

[stepreg]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#stepwise-regression>
[stepreg_script]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_StepwiseRegression.R>
[stepreg_doc]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_StepwiseRegression.pdf>

[survival]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#survival-analysis>
[survival_script]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_Survival.R>
[survival_doc]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_Survival.pdf>
[survival_img]: https://github.com/MicroStrategy/RIntegrationPack/blob/master/assets/RShelf_Survival.PNG

[knn]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#k-nearest-neighbors>
[knn_script]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_kNN.R>
[knn_doc]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_kNN.pdf>

[nn]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#neural-network>
[nn_script]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_NeuralNetwork.R>
[nn_doc]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_NeuralNetwork.pdf>
[nn_img]: https://github.com/MicroStrategy/RIntegrationPack/blob/master/assets/RShelf_NeuralNetwork.PNG

[nb]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#naive-bayes>
[nb_script]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_NaiveBayes.R>
[nb_doc]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_NaiveBayes.pdf>
[nb_img]: https://github.com/MicroStrategy/RIntegrationPack/blob/master/assets/RShelf_NaiveBayes.PNG

[rf]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#random-forest>
[rf_script]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_RandomForest.R>
[rf_doc]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_RandomForest.pdf>
[rf_img]: https://github.com/MicroStrategy/RIntegrationPack/blob/master/assets/RShelf_RandomForest.PNG

[steplogreg]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#stepwise-logistic-regression>
[steplogreg_script]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_StepwiseLogistic.R>
[steplogreg_doc]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_StepwiseLogistic.pdf>

[kcluster]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#k-means-clustering>
[kcluster_script]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_kMeansClustering.R>
[kcluster_doc]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_kMeansClustering.pdf>
[kcluster_img]: https://github.com/MicroStrategy/RIntegrationPack/blob/master/assets/RShelf_kMeans.PNG

[kmedoids]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#k-medoids-clustering>
[kmedoids_script]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_kMedoidsClustering.R>
[kmedoids_doc]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_kMedoidsClustering.pdf>
[kmedoids_img]: https://github.com/MicroStrategy/RIntegrationPack/blob/master/assets/RShelf_kMedoids.PNG

[pairwise]: <https://github.com/MicroStrategy/RIntegrationPack/tree/master/scripts#pairwise-correlation>
[pairwise_script]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_PairwiseCorr.R>
[pairwise_doc]: <https://github.com/MicroStrategy/RIntegrationPack/blob/master/scripts/RShelf_PairwiseCorr.pdf>
[pairwise_img]: https://github.com/MicroStrategy/RIntegrationPack/blob/master/assets/RShelf_PairwiseCorr.PNG

[img_howtouse]: https://github.com/MicroStrategy/RIntegrationPack/blob/master/assets/RShelf_Params3.png