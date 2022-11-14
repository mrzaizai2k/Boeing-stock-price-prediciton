# Boeing-stock-price-prediciton
Check out my 2 YOUTUBE channels for more:
1. [Mrzaizai2k - AI](https://www.youtube.com/channel/UCFGCVG0P2eLS5jkDaE0vSfA) (NEW)
2. [Mrzaizai2k](https://www.youtube.com/channel/UCCq3lQ1W437euT9eq2_26HQ) (old)

[Kaggle Notebook](https://www.kaggle.com/code/bomaich/boeing-stock-price-prediction)

# TABLE OF CONTENTS
* [INTRODUCTION](#INTRODUCTION)
* [PROBLEMS](#PROBLEMS)
* [SCOPE](#SCOPE)
* [CONCLUSION](#CONCLUSION)

# INTRODUCTION

I suppose you may have thought about utilizing ML/AI to forecast stock price at some point. That was, in fact, my fantasy when I was a freshman in college. I set out to create a model to forecast them back then and wanted to live a prosperous life for the rest of my days. But I ran into trouble.

* I didn't anything about finance
* In lack of knowledge about ML/AI
* My computer wasn't powerful (It's pretty weak to run even the simple code on VScode)

Even though I have found solutions to all of the aforementioned issues, I am currently unable to pay my rent :)).  Just try, even if we can't make a dream come true.

# PROBLEMS

I started to read papers and searching for the code on Kaggle. And I found this Note book: [📊Stock Market Analysis 📈 + Prediction using LSTM](https://www.kaggle.com/code/faressayah/stock-market-analysis-prediction-using-lstm/notebook). In general, the visualization was really good. Nevertheless, the APPLE stock prediction was wrong (The model is simply predict by mimicking the price of the day before). And I found that a lot of people make the same mistakes. 

1. Using the close price only (this feature has a normal distribution which is almost random)
2. Using Minmax scaler instead of Standard scaler (the close price doesn't have upper bound)
3. Not compare their model to a baseline model (Naive forecast)
4. Not using other features to predict (News, volume, oil price, FED interest rate)
5. The model is so simple (I guess its because they want to make a reference)
6. Final test on the valid data???

You can see more with [LSTM time series + stock price prediction = FAIL](https://www.kaggle.com/code/carlmcbrideellis/lstm-time-series-stock-price-prediction-fail) and [Predicting Stock Prices with LSTMs: One Mistake Everyone Makes](https://www.youtube.com/watch?v=Vfx1L2jh2Ng&list=WL&index=4)

However, instead of predicting price, some papers are trying to solve the classification task (Buy, Sell, Keep) with the given information to optimize the value. Or they tried to applied other models to solve this task (CNN, CNN+LSTM, GAN...)

# SCOPE

It goes without saying that there are several issues to address and  methods to tackle this task in a single notebook. I think a whole system is required. I'll attempt to address a few minor problems in this notebook, which you are welcome to use as a reference. Along the way, we'll be tackling the following issues:

* Using Standard scaler
* Using other features like oil price/ other stock price/ return price/Volume to predict
* More complicated model (I'll teach you how to create a model function, not using Sequential)
* How to split data and test it right
* Compare our model to Naive basline model

Even though I really want to develop a system that uses news and company reports (P/E, P/B, and Capital) as features or converts them into a classification algorithm, I don't have any data, and the system would be too large to fit in a single notebook.

The models I used in this notebook are
* [Simple CNN](#3.7.1-Simple-CNN)
* [Multi LSTM](#3.7.2-Multi-LSTM)
* [Complex CNN](#3.7.3-Complex-CNN)
* [CNN + LSTM](#3.7.4-CNN-+-LSTM)
* [LSTM + Dense](#3.7.5-LSTM-+-Dense)

# CONCLUSION

Look at the pictures below, we can see that in general, when we increase the input_width and OUT_STEPS. 
* The MAE and RMSE increase. It shows that the predictions are more related to recent data. Furthermore,  
* Multi LSTM model errors in test data are higher than validation data (The window size can solve overfitting??)
* One exception is CNN+LSTM model. The errors increase. I still don't know why more complicated models achieve worse results than simple ones (the simple CNN which has just 1 Conv layer/use the last 3 time steps) gain outstanding performance

<p align="center"><img src="doc/input_width = 10 OUT_STEPS = 5.png" width="500"></p>
<p align="center"><i>Figure. input_width = 10,  OUT_STEPS = 5 </i></p>

<p align="center"><img src="doc/input_width = 20 OUT_STEPS = 10.png" width="500"></p>
<p align="center"><i>Figure. input_width = 20,  OUT_STEPS = 10 </i></p>

