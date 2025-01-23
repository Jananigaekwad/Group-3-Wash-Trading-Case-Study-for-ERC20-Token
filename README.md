# Group-3-Wash-Trading-Case-Study-for-ERC20-Token

## Project Overview
This project focuses on detecting **wash trading** activities within the transaction history of the NEAR ERC20 token. Wash trading is a manipulative practice in cryptocurrency trading that inflates transaction volumes to mislead investors about a token's liquidity and demand. 
# The models implemented include:
- **Isolation Forest**
- **Local Outlier Factor (LOF)**
- **One-Class SVM**

The detection process uses an ensemble approach, combining the outputs of multiple models for robust anomaly identification.

## Dataset
The dataset contains transaction records of the NEAR ERC20 token from **January 1, 2024, to June 25, 2024**. Key columns include:
- `Transaction Hash`: Unique identifier for each transaction.
- `Block Number`: The block containing the transaction.
- `Unix Timestamp`: Transaction timestamp in Unix format.
- `DateTime (UTC)`: Transaction date and time in UTC format.
- `From` and `To` Addresses: Wallet addresses for sending and receiving tokens.
- `Quantity`: Volume of NEAR tokens transferred.
- `Method`: Transaction type (e.g., swaps or specific actions).

The dataset enables the identification of anomalies through time-series trends, volume patterns, and network structures.

---

## Machine Learning Models
### 1. **Isolation Forest**
- Detects anomalies by isolating observations in the feature space.
- Key parameters:
  - Contamination: 5% (expected proportion of anomalies).
  - Random State: Ensures reproducibility.

### 2. **Local Outlier Factor (LOF)**
- Flags anomalies by comparing the local density of a transaction to its neighbors.
- Key parameters:
  - `n_neighbors`: 20 (optimal local density comparison).
  - Contamination: 5%.

### 3. **One-Class SVM**
- Distinguishes normal transactions from anomalies using a support vector machine.
- Key parameters:
  - Gamma: `auto` (scales based on feature space).
  - Nu: 0.05 (expected proportion of outliers).

### Ensemble Voting
- Combines predictions from all three models.
- An anomaly is flagged if at least **two out of three models** agree.
### Temporal Models (ARIMA and LSTM):

• ARIMA parameters (5,1,2) were set based on data seasonality and trend
decomposition to capture transaction volume patterns accurately.
• LSTM epochs and batch size were optimized to balance prediction accuracy
with computational efficiency.

Fine-tuning focused on adjusting contamination levels, neighbourhood size, and model
parameters for accuracy, ensuring reliable detection of suspicious trading activities.

---

## Methodology
1. **Data Preprocessing**
   - Handle missing values.
   - Normalize features using standard scaling techniques.

2. **Statistical Hypothesis Testing**
   - Mann-Whitney U Test revealed significant shifts in transaction behavior on key dates.

3. **Model Training**
   - Train and fine-tune Isolation Forest, LOF, and One-Class SVM models.
   - Perform hyperparameter optimization to enhance accuracy.

4. **Evaluation**
   - Metrics used: Precision, Recall, F1-Score, and AUC-ROC.
   - Anomalies visualized through time-series plots and density graphs.

---

