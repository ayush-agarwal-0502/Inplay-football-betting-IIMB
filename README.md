

# IN-PLAY-BETTING

This project is about predicting the outcome of football matches. The outcomes are categorized into three classes: Home team wins, Away team wins, and Draw. The project is divided into several notebooks, each serving a specific purpose.

* __Teammates :__ Ayush Agarwal (IIT BHU ECE'24) , Aakash Sharma (IIT BHU EP), Anuj (IIT BHU Civil)
* __Entry For :__ IIMB (Indian Institute of Management, Bangalore) , Vista (Business Fest)
* __Tools Used :__ Excel, Power BI, Python Libraries
* __Problem Tackled :__ In-Play Betting in Football Matches using Data Analytics
* __Domain Knowledge Used :__ Data Analytics, Machine Learning (Classification) 

![image](https://github.com/ayush-agarwal-0502/Inplay-football-betting-IIMB/assets/86561124/18b250d9-2d79-4756-807f-ed11f5389559)

## EDA_n_training.ipynb

This notebook is responsible for the initial exploration of the dataset and training of the model for predicting home team wins. It includes data preprocessing, exploratory data analysis, and model training. The model used for prediction is Logistic Regression. The trained model is then saved for future use.

## away_train.ipynb

This notebook is similar to the previous one but is responsible for predicting if the away team wins. It follows the same steps: data preprocessing, exploratory data analysis, and model training. The model used for prediction is also Logistic Regression. The trained model is then saved for future use.

## draw_train.ipynb

This notebook is responsible for predicting if the match ends in a draw. It follows the same steps as the previous notebooks: data preprocessing, exploratory data analysis, and model training. The model used for prediction is Logistic Regression. The trained model is then saved for future use.

## prediction.ipynb

This notebook is responsible for making the final prediction. It loads the previously trained models and uses them to predict the outcome of the matches. The prediction is based on the probabilities given by each model for each class. The class with the highest probability is chosen as the final prediction. The weights of the probabilities are adjusted based on the precision of each model's performance. The final prediction score on the testing dataset is approximately 68.8% .

### predict_outcome_weighted(X) explained

This function takes as input a Pandas dataframe X that holds match data. The dataframe should contain a column named `HTGD` which represents the Home Team Goal Difference.

It uses three pre-trained logistic regression models (`lr_home_model.pkl`, `lr_away_model.pkl`, and `lr_draw_model.pkl`) to predict the outcome of a football match: `Home Win` (represented as 2), `Away Win` (represented as 0), or `Draw` (represented as 1). Each prediction is weighted by a pre-defined precision weight.

If the `HTGD` (Home Team Goal Difference) is greater than 1, it predicts a `Home Win`. If `HTGD` is less than 1, it predicts an `Away Win`. If `HTGD` equals 1, it uses the trained models to predict the match outcome, factoring in the precision weights.

Below is the flowchart to explain the process:
```
                  ┌───────────────┐
                  │  Start        │
                  └──────┬────────┘
                         ▼
          ┌─────────────────────────────┐
          │Load logistic regression     │
          │models from .pkl files       │
          └───────┬─────────────────────┘
                  ▼
┌─────────┐      ┌─────────────────────┐      ┌─────────┐
│HTGD > 1 │───►  │Predict Home Win     │ ◄──  │HTGD < 1 │
└─────────┘      └───────┬─────────────┘      └─────────┘
                         │      ┌────────────┐
                         │      │  Else      │
                         │      └─────┬──────┘
                         ▼            ▼
┌──────────────────────────────────────────────────────┐
│Calculate outcome probabilities with each model       │
│and corresponding precision weights                   │
└─────────────────────────────┬────────────────────────┘
                              ▼
          ┌──────────────────────────────────────────────┐
          │Determine the outcome with the highest        │
          │weighted probability                          │
          └───────┬──────────────────────────────────────┘
                  ▼
         ┌────────────────────┐
         │  Return predictions│
         └────────────────────┘
```
### Predictions

The function returns a list of predictions for the matches in the input dataframe, represented as follows:

`2 : Home Win`
`0 : Away Win`
`1 : Draw`
Feel free to experiment with different match data and precision weights. Enjoy your match predictions!

Note:

Please make sure to have the joblib library installed in your environment and your logistic regression models (.pkl files) should be in the same directory as your Python script for the function to work properly.

## Conclusion

This project demonstrates the process of predicting the outcome of football matches using machine learning. It includes data preprocessing, exploratory data analysis, model training, and prediction. The models used for prediction are trained using Logistic Regression and their performance is evaluated based on their precision. The final prediction is made by comparing the probabilities given by each model for each class and choosing the class with the highest probability.
