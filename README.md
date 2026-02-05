## Short-Term Energy Consumption Forecasting: A Comparative Study of ARIMA and LSTM Models

This research project explores the application of classical statistical models (ARIMA) and deep learning approaches (LSTM) to short-term energy consumption forecasting, providing a comparative analysis of their predictive performance.

📄 **Full Research Report**: [Download PDF](paper.pdf)

For a comprehensive analysis of the methodology, results, and theoretical framework, please refer to the complete research paper.

### 📊 Project Overview

As energy consumption patterns become increasingly complex and non-linear, accurate short-term forecasting has become critical for energy management and grid optimization. This work compares two distinct approaches to time series forecasting:

**ARIMA (Autoregressive Integrated Moving Average)**: A classical statistical model that relies on stationarity assumptions and differencing techniques to capture temporal dependencies in time series data.

**LSTM (Long Short-Term Memory)**: A deep learning architecture based on recurrent neural networks designed to capture long-term dependencies and complex non-linear patterns through memory cells with gating mechanisms.

The study evaluates both models on hourly energy consumption data to determine which approach provides superior forecasting accuracy for short-term predictions.

### 🧮 Methodology

**ARIMA Model**

The ARIMA model is characterized by three parameters $(p, d, q)$:

- **p**: Order of the Autoregressive (AR) component
- **d**: Degree of differencing (Integrated component)  
- **q**: Order of the Moving Average (MA) component

The model equation for ARIMA$(p,d,q)$ can be expressed as:

$$\phi(B)(1-B)^d y_t = \theta(B)\epsilon_t$$

Where $\phi(B)$ represents the autoregressive polynomial, $\theta(B)$ represents the moving average polynomial, $B$ is the backshift operator, and $\epsilon_t$ represents white noise.

**LSTM Model**

The LSTM network is a recurrent neural architecture designed to better handle long-term dependencies than a standard RNN.

It uses **memory cells** and **gates** to control the flow of information over time. In a simplified form, the LSTM cell update can be expressed as:

$$C_t = f_t \odot C_{t-1} + i_t \odot \tilde{C}_t$$
$$h_t = o_t \odot \tanh(C_t)$$

Where:

- $f_t$ is the forget gate (what to discard from the past),
- $i_t$ is the input gate (what new information to store),
- $o_t$ is the output gate (what information to expose at time $t$),
- $C_t$ is the cell state and $h_t$ the hidden state.

Thanks to this mechanism, the LSTM can:

- retain consumption trends over several hours or days,
- ignore noisy or irrelevant fluctuations,
- better capture complex non-linear relationships present in energy time series.

### 📈 Key Results

Experiments conducted on the Hourly Energy Consumption dataset reveal:

**Superior Performance**: The LSTM model achieved a **65% reduction in Mean Squared Error (MSE)** compared to the ARIMA model, with MSE values of 434,007.12 versus 1,250,099.61 respectively.

**Trend Capture**: While the ARIMA model managed to follow the overall trend of energy consumption, it struggled with complex non-linearities and seasonal fluctuations, resulting in significant residual variability.

**Precise Alignment**: The LSTM network demonstrated remarkable alignment between predicted values and actual observations, even on unseen test data, confirming its ability to model complex sequential dependencies.

| Model | MSE |
|-------|-----|
| ARIMA (1,0,0) | 1,250,099.61 |
| LSTM | 434,007.12 |

### Visualization of Results

**Figure 1: ARIMA Predictions vs Actual Values**

![ARIMA Results](visualization/arima-pred.png)

This figure illustrates the temporal evolution of ARIMA predictions compared to actual energy consumption values. The analysis reveals that while the model captures the general trend, there is significant variability in the residuals, indicating limitations in handling non-stationary components.

**Figure 2: LSTM Predictions vs Actual Values**

![LSTM Results](visualization/lstm-pred.png)

The LSTM model demonstrates superior performance with extremely precise alignment between predicted values and actual observations. The network effectively captures complex temporal dependencies that traditional statistical models fail to model.


### 🛠️ Technologies & Tools

- **Language**: Python
- **Statistical Modeling**: statsmodels (ARIMA)
- **Deep Learning**: PyTorch (LSTM)
- **Data Processing**: Pandas, NumPy
- **Visualization**: Matplotlib, Seaborn

### 📚 References

1. Nashirah Abu Bakar and Sofian Rosbi. "Autoregressive Integrated Moving Average (ARIMA) Model for Forecasting Cryptocurrency Exchange Rate in High Volatility Environment: A New Insight of Bitcoin Transaction". In: *IJAERS* 4.11 (2017), pp. 130–137.

2. Christian Bakke Vennerød, Adrian Kjærran, and Erling Stray Bugge. *Long Short-term Memory RNN*. May 14, 2021. arXiv: 2105.06756[cs].
