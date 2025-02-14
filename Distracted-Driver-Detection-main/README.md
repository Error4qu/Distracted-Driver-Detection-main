# Distracted-Driver-Detection

## Project Overview

This project is done as a part of `Machine Learning` Course.

Driving a car is a complex task, and it requires complete attention. Distracted driving is any activity that takes away the driver’s attention from the road. Approximately 1.35 million people die each year as a result of road traffic crashes.

In this project our aim is to identify whether a driver is driving safely or indulged in distraction activities like texting, drinking etc. We show an in breadth & depth analysis of various features like **HOG, LBP, SURF, KAZE, pixel values** with feature reduction techniques **PCA, LDA** along with **min-max** normalization over different classifiers such as **SVM XGBoost, Bagging, AdaBoost, K-Nearest Neighbors, Decision Trees** and compare their performance by tuning different hyperparameters. We evaluate the performance of these classifiers on metrics such as **Accuracy, Precision, Recall, F1 score and ROC**.

Project Poster can be found in [ML-Poster-Final.pdf](ML_Project_End_Term_PPT.pdf).

Project Report can be found in [ML_Project_EndTerm_Report.pdf](ML_Project_End_Term_Report.pdf).

## Dataset
The dataset contains 22424 driver images in total downloaded from [kaggle](https://www.kaggle.com/c/state-farm-distracted-driver-detection/data). The dataset contains coloured images of size 640 x 480 pixels which are resized to 64 X 64 coloured images for training and testing pusposes.
Stratified splitting is used to split the dataset into 80:10 Training-Testing ratio. The training dataset is further split into 90:10 Training-Validation set.

The 10 classes to predict are:
- Safe driving 
- Texting(right hand) 
- Talking on the phone (right hand)
- Texting (left hand) 
- Talking on the phone (left hand)
- Operating the radio 
- Drinking 
- Reaching behind 
- Hair and makeup  
- Talking to passenger(s). 

<div align="center"><img src="plots/classes_imgs.jpg" height='200px'/></div>


## Algorithm Used

<div align="center"><img src="plots/pipeline.jpeg" /></div>

- Different combinations of feature sets were used shown in Fig 1(**Ugly Duckling Theorem**).
- Evaluated with different classifiers, model parameters were varied using **Grid Search** to find the best parameters (**No Free Lunch Theorem**).
- Deep learning methods CNN and ResNet-101 also used for classification and Performace visualised using Class Activation Maps (CAMs). 
- In PCA, number of components were preserved using **Elbow method over variance of PCA projected data** (Fig. 2).

## Evaluation Metrics and Results

Follwing are the results of the project:

                                        Fig 1. Feature Visualization
   <div align="center"><img src="plots/Final_Feature_extraction.png" height='450px'/></div>                                         

                                Fig 2. Variance of PCA projected over min-max normalized data
<div align="center"><img src="plots/PCA_variance_graphs.png" height='500px'/></div>

                                Fig 3 Receiver Operating Characteristic (ROC) Curves
                                    a. ROC of PCA reduced data
                                    b. ROC of LDA reduced data
                                    c. ROC of LDA on PCA reduced data
<div align="center">
    <img src="plots/roc_over_pca.png" height='225px'/>
    <img src="plots/roc_over_lda.png" height='225px'/>
    <img src="plots/roc_over_lda_over_pca.png" height='225px'/>
</div>

                Fig 4. Optimal Parameters of classifiers after grid search
<div align="center"><img src="plots/optimal_param.png" height='180px'/></div>

     Fig 5. Comparing various classifiers with different feature sets over Accuracy/Recall/Precision/F1 score
                                    a. Results of PCA reduced data
                                    b. Results of LDA reduced data
                                    c. Results of LDA on PCA reduced data
         
<div align="center"><img src="plots/results_pca.png" height='200px'/></div>
<div align="center"><img src="plots/results_lda.png" height='200px'/></div>
<div align="center"><img src="plots/results_lda_over_pca.png" height='200px'/></div>


                                Fig 5. CNN architecture 
<div align="center"><img src="plots/CNN_model.jpeg"/></div>


        Fig 6. Comparing between deep learning classifiers with Accuracy/Recall/Precision/F1 score
                                    a. CNN
                                    b. ResNet-101 [Stratery-1 : Retrain only last layer]
                                    c. ResNet-101 [Stratery-2 : Retrain last few layers]
<div align="center"><img src="plots/results_deep_learning_classifiers.png" height='150px'/></div>


                    Fig 6. ResNet-101 [Stratergy-2] performance measured using Class Activation Maps
<div align="center"><img src="plots/class_activation_map.png"/></div>

## Interpretation of Results


- PCA gives better results compared to LDA and LDA over PCA 
- AdaBoost performed poorly on all sets of data and proved to be a bad choice as data does not suffer from high variance. 
- SVM on PCA projected feature set (HOG, LBP, Color Hist, SURF, GRAY, KAZE & RGB) gave the
best metric scores because of the rich features and kernel tricks to classify data.
- Among Deep Learning methods, ResNet-101 with stratery-2 i.e retrain last few layers gave best accuracy.
-  Feature Extration and Image Augumentation techniques helped in improving overall accuracy.

## References

1. H. Eraqi, Y. Abouelnaga, M. Saad, and M. Moustafa, “Driver Distraction Identification with an Ensemble of Convolutional Neural Networks”, Journal of Advanced Transportation 2019, 1-12; doi: 10.1155/2019/4125865
2. [Class Activation maps](https://snappishproductions.com/blog/2018/01/03/class-activation-mapping-in-pytorch.html.html)
3. [Distracted Driver Detection using Deep Learning](https://medium.com/@sam.bell_43711/distracted-driver-detection-using-deep-learning-ecc7216ae8d0)
4. [ML techniques for Distacted Driver Detection](http://cs229.stanford.edu/proj2019spr/report/24.pdf)

