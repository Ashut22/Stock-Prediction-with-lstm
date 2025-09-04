# Stock Price Prediction using LSTM

This project demonstrates how to build a **Stock Price Prediction Model** using **Long Short-Term Memory (LSTM)** networks.  
The dataset used is **Apple Inc. (AAPL)** historical stock prices.

---

## 📌 Project Workflow

### 1. Data Loading and Exploration
- Loaded `AAPL.csv` containing stock price history with columns such as:
  - `date`, `open`, `high`, `low`, `close`, `volume`, `adjClose`, etc.
- Used `pandas` to explore dataset (`df.info()`) and understand shape, columns, and datatypes.

### 2. Data Preprocessing
- Extracted the `close` price column for modeling.
- Applied **MinMaxScaler** to normalize values into the range `[0,1]`.
- Split the dataset into **training (70%)** and **testing (30%)** sets.

### 3. Dataset Preparation
- Defined a helper function `create_dataset()` to transform the time series into supervised learning format:
  - Input: Previous 100 time steps (`t, t+1, …, t+99`)
  - Output: Next value (`t+100`)
- Reshaped data into LSTM-compatible format: `(samples, time steps, features)`.

### 4. Model Architecture
Built a **Stacked LSTM** model using Keras:

- 3 LSTM layers (50 units each)  
- 1 Dense layer (output = 1)  
- Loss function: `mean_squared_error`  
- Optimizer: `adam`  

---

## 🧑‍💻 Model Training & Evaluation

- Trained the model on training data.  
- Predictions were made on both train and test sets.  

### Performance Metrics:
- **Train RMSE:** `149.99`  
- **Test RMSE:** `247.73`  

This shows the model fits training data well but struggles slightly on unseen test data due to stock market volatility.

---

## 📊 Visualizations

1. **Training vs Test Predictions**  
   Overlayed actual stock prices with predicted values.

2. **Forecasting Next 30 Days**  
   - Recursive prediction using the last 100 days of test data.  
   - Generated next 30 stock price predictions.  
   - Plotted actual vs forecasted values.

3. **Extended Time Series**  
   - Appended predictions to the original dataset.  
   - Plotted entire stock history along with 30-day forecast extension.

---
**Requirements**:
- Python 3.8+
- Libraries:
- numpy
- pandas
- matplotlib
- scikit-learn
- tensorflow / keras
