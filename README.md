# Higgs-Boson-Machine-Learning-Challenge-by-ATLAS


<center> <a href="https://ibb.co/mhzwBFP"><img src="https://i.ibb.co/XFJg4kG/ddd.png" alt="ddd" border="0"></a> </center>


## About The project 
this is typically project of machine learning for physics proposed by ATLAS in 2014 on the famous platform [**"Kaggle"**](https://www.kaggle.com/c/higgs-boson)  known as "the higgs boson challenge " 
It was given by the associate professor [**"Olivier Schwander"**](http://www-connex.lip6.fr/~schwander/en/) as a 4 weeks assignments , where he asked us to simulate the challenge even though the project deadlines were overdue many years ago .  

It is a binary classification problem where we will use the simulated data with features characterizing events detected by ATLAS, we should classify examples ( particles events ) into "tau tau decay of a Higgs boson" encoded by ‘s’ ( aka signal )  versus "background" encoded by ‘b’ .
The target is represented by the column “Label” .

The evaluation metric used is the AMS and it's described as the following : 
<a href="https://ibb.co/6ZGbWYK"><img src="https://i.ibb.co/ZJvKMdQ/Izly.png" alt="Izly" border="0"></a>

We need a column called 'weights' in order to estimate this metric of this challenge which is fundamentally based on the latter . Thus we will gather it from CERN open data : http://opendata.cern.ch/record/328  . However ,  for a good ethical challenging environment 
we will obviously never use the testing data and keep it **unseen** for a true trustful model estimation of our work  .

a full report was given to expain the entire approach 

## Testing 


## License
October,2019

[MIT license](http://opensource.org/licenses/MIT).
