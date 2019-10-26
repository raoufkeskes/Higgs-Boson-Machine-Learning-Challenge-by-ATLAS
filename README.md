# Higgs-Boson-Machine-Learning-Challenge-by-ATLAS


<center> <a href="https://ibb.co/mhzwBFP"><img src="https://i.ibb.co/XFJg4kG/ddd.png" alt="ddd" border="0"></a> </center>


## About The project 
this is typically project of machine learning for physics proposed by ATLAS in 2014 on the famous platform [**"Kaggle"**](https://www.kaggle.com/c/higgs-boson)  known as "the higgs boson challenge " 
It was given by the associate professor [**"Olivier Schwander"**](http://www-connex.lip6.fr/~schwander/en/) as a 4 weeks assignment , where he asked us to simulate the challenge even though the project deadlines were overdue many years ago .  

It is a binary classification problem where we will use the simulated data with features characterizing events detected by ATLAS, we should classify examples ( particles events ) into "tau tau decay of a Higgs boson" encoded by ‘s’ ( aka signal )  versus "background" encoded by ‘b’ .
The target is represented by the column “Label” .

The evaluation metric used is the AMS and it's described as the following ( click on the image for a clear image ) : 
<a href="https://ibb.co/6ZGbWYK"><img src="https://i.ibb.co/ZJvKMdQ/Izly.png" alt="Izly" border="0"></a>


**a full report was given to expain the entire approach from scratch**

## Our outstanding model !
we spent few days fine-tuning a [**"LightGBM"**](https://lightgbm.readthedocs.io) model on the validation set .  

## Results 
trained/validated on ( 250 000 examples ) tested on ( 550 000 examples ) 

our final submitted kaggle score is    : **3.54272**

the winner has a score of              : **3.80581**

We are sure that if we had more time and only one project to do we would outperform him 

## how to test it 
1)  Install lightGBM following these instructions : https://lightgbm.readthedocs.io/en/latest/Installation-Guide.html

2) this is a code snippet for AMSMetric
```
#### define the AMS score ####
'''
- an implementation of the AMS score if you need it  
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

3) load the model and predict 
```
import lightgbm as lgb


clf = lgb.Booster(model_file='model.txt') 

# fine_tuned threshold
threshold = 0.84

Y_pred = ( clf.predict ( X_test ) > th ).astype("int") 


```



## References 

[1] Guolin Ke , Qi Meng , Thomas Finley , Taifeng Wang , Wei Chen , Weidong Ma , Qiwei Ye , Tie-Yan Liu ; LightGBM: A Highly Efficient Gradient Boosting Decision Tree , NIPS Conference 2017

https://papers.nips.cc/paper/6907-lightgbm-a-highly-efficient-gradient-boosting-decision-tree.pdf

## License
October,2019

[MIT license](http://opensource.org/licenses/MIT).
