# Stock-Prediction: Take stock price of any company you want and predicts its price by using LSTM. Use only Jupyter notebook code.

# Introduction to LSTMs:

Long Short-Term Memory models are extremely powerful time-series models. They can predict an arbitrary number of steps into the future. An LSTM module (or cell) has 5 essential components which allows it to model both long-term and short-term data.

Cell state (ct) - This represents the internal memory of the cell which stores both short term memory and long-term memories

Hidden state (ht) - This is output state information calculated w.r.t. current input, previous hidden state and current cell input which you eventually use to predict the future stock market prices. Additionally, the hidden state can decide to only retrive the short or long-term or both types of memory stored in the cell state to make the next prediction.

Input gate (it) - Decides how much information from current input flows to the cell state

Forget gate (ft) - Decides how much information from the current input and the previous cell state flows into the current cell state

Output gate (ot) - Decides how much information from the current cell state flows into the hidden state, so that if needed LSTM can only pick the long-term memories or short-term memories and long-term memories

# Running the LSTM:

Here you will train and predict stock price movements for several epochs and see whether the predictions get better or worse over time. You follow the following procedure.

1.Define a test set of starting points (test_points_seq) on the time series to evaluate the model on

2.For each epoch

    (a).For full sequence length of training data
    
      (i).Unroll a set of num_unrollings batches
      
      (ii).Train the neural network with the unrolled batches
      
    (b).Calculate the average training loss
    
    (c).For each starting point in the test set
    
      (i).Update the LSTM state by iterating through the previous num_unrollings data points found before the test point
      
      (ii).Make predictions for n_predict_once steps continuously, using the previous prediction as the current input
      
      (iii).Calculate the MSE loss between the n_predict_once points predicted and the true stock prices at those time stamps

# Visualizing the Predictions

You can see how the MSE loss is going down with the amount of training. This is good sign that the model is learning something useful. To quantify your findings, you can compare the network's MSE loss to the MSE loss you obtained when doing the standard averaging (0.004). You can see that the LSTM is doing better than the standard averaging. And you know that standard averaging (though not perfect) followed the true stock prices movements reasonably.
