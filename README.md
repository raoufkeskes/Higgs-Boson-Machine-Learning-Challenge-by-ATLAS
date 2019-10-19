# Higgs-Boson-Machine-Learning-Challenge-by-ATLAS


<center> <a href="https://ibb.co/mhzwBFP"><img src="https://i.ibb.co/XFJg4kG/ddd.png" alt="ddd" border="0"></a> </center>


## About The project 
this is typically project of machine learning for physics proposed by ATLAS in 2014 on the famous platform [**"Kaggle"**](https://www.kaggle.com/c/higgs-boson)  known as "the higgs boson challenge " 
It was given by the associate professor [**"Olivier Schwander"**](http://www-connex.lip6.fr/~schwander/en/) as a 4 weeks assignments , where he asked us to simulate the challenge even though the project deadlines were overdue many years ago .  

It is a binary classification problem where we will use the simulated data with features characterizing events detected by ATLAS, we should classify examples ( particles events ) into "tau tau decay of a Higgs boson" encoded by ‘s’ ( aka signal )  versus "background" encoded by ‘b’ .
The target is represented by the column “Label” .

The evaluation metric used is the AMS and it's described as the following ( click on the image for a clear image ) : 
<a href="https://ibb.co/6ZGbWYK"><img src="https://i.ibb.co/ZJvKMdQ/Izly.png" alt="Izly" border="0"></a>

We need a fundamental column called 'weights' of our testing data in order to estimate the metric of this challenge . Therefore , we will gather it from CERN open data : http://opendata.cern.ch/record/328 to use it in the final estimation on unseen data after a whole bunch of work !
However ,  for a good ethical challenging environment we will obviously never use the testing data and keep it **unseen** for a true trustful model estimation of our work to evaluate ourselves and learn .
Note that during the challenge this evaluation task was handled by the backend system of KAGGLE .


**a full report was given to expain the entire approach from scratch**

## Our outstanding model !
we have been working for days fine-tuning a [**"LightGBM"**](https://lightgbm.readthedocs.io) model on the validation set .  

## Decision Explainability 

## Results 
We outperformed the competition winner with a margin of 1.2 on the AMS metric and trained/validated ( 250 000 examples ) testing on ( 550 000 examples ) 
our final score is        : 5.02846
the winner has a score of : 3.80581

## how to test it 
- Install lightGBM following these instructions : https://lightgbm.readthedocs.io/en/latest/Installation-Guide.html
```
import lightgbm as lgb


clf = lgb.Booster(model_file='model.txt') 

# fine_tuned threshold
threshold = 0.84

Y_pred = ( clf.predict ( X_test ) > th ).astype("int") 


#### define the AMS score ####
'''
- an implementation of the AMS score of you need it to evaluate 
'''
def ams(s, b):
    return np.sqrt(2 * ((s + b + 10) * np.log(1.0 + s/(b + 10)) - s))

def get_ams_score(W, Y, Y_pred):
    s = W * (Y == 1) * (Y_pred == 1)
    b = W * (Y == 0) * (Y_pred == 1)
    s = np.sum(s)
    b = np.sum(b)
    return ams(s, b)
#############################

```



## References 

[1] Guolin Ke , Qi Meng , Thomas Finley , Taifeng Wang , Wei Chen , Weidong Ma , Qiwei Ye , Tie-Yan Liu ; LightGBM: A Highly Efficient Gradient Boosting Decision Tree , NIPS Conference 2017

https://papers.nips.cc/paper/6907-lightgbm-a-highly-efficient-gradient-boosting-decision-tree.pdf

## License
October,2019

[MIT license](http://opensource.org/licenses/MIT).
