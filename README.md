Machine Learning Stock Price Prediction Model

The goal of implementing this model is to predict stock prices using an LSTM neural network.

To create this stock price prediction model, several machine learning techniques were implemented systematically. First, historical stock data was collected using the yfinance library. The dataset included daily closing prices, trading volume, and other key financial metrics. To improve the model’s predictive power, feature engineering was applied by introducing the 50-day moving average (MA_50), 200-day moving average (MA_200), and a volatility measure based on the rolling standard deviation of price changes.

Data normalization was performed using the MinMaxScaler to scale all numerical values between 0 and 1 to ensure that the model could learn patterns without being biased toward large numbers.

To handle time-series forecasting, the data was transformed into sequential input-output pairs. A 100-day lookback window was used by training the model to predict the stock price for the 101st day based on the past 100 days of stock prices and other features.

The dataset was then split into training (70%), validation (15%), and testing (15%) sets to make sure that the model generalised well to unseen data. The LSTM neural network was used for predictions. The model architecture included:
1. An initial LSTM layer with 128 units, which retained sequential dependencies.
2. A dropout layer (20%), which randomly ignored some neurons to prevent overfitting.
3. A second LSTM layer with 64 units, which further refined learned patterns.
4. Another dropout layer (20%) to maintain regularisation.
5. A fully connected dense layer with 25 neurons and ReLU activation, allowing the model to learn non-linear relationships.
6. A final dense output layer with 1 neuron, which generated the predicted stock price.

To optimise learning, the model was compiled using the Adam optimiser and Mean Squared Error (MSE) as the loss function. During training, Early Stopping was applied, which automatically stopped training when the validation loss stopped improving, which prevented unnecessary computations and overfitting.

Once the model was trained, it was used to predict stock prices on the test dataset. Since the model's predictions were in a normalised range (0 to 1), an inverse transformation was applied to restore the prices to their original scale. The Root Mean Squared Error (RMSE) was calculated to evaluate the accuracy of the predictions.

To ensure that the LSTM model performed better than traditional methods, it was compared against two baseline models:
1. The 50-day moving average (MA_50) model, which predicted stock prices based on the simple moving average.
2. The persistence model, which assumed that the stock price on any given day would remain the same as the previous day's closing price.

Finally, the actual stock prices versus the predicted values were plotted on a chart to visualise the model's performance.
