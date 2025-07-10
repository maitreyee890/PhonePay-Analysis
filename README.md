# 📊 PhonePe Pulse Data Analysis

This project explores transaction and user behavior data from the [PhonePe Pulse GitHub Repository](https://github.com/PhonePe/pulse). It analyzes and visualizes digital payment trends using public JSON datasets hosted on GitHub.

---

## 🧠 Objective

To load, clean, and visualize PhonePe transaction data for various states in India, beginning with Andhra Pradesh (2018 Q1), with a focus on:

* Understanding payment modes
* Analyzing transaction amounts and frequency
* Visualizing digital payment patterns

---

## 📁 Project Structure

The project is structured as a Jupyter Notebook (`PhonePe.ipynb`) that:

1. **Loads JSON data** from PhonePe Pulse GitHub repo.
2. **Processes and flattens nested data** like `paymentInstruments`.
3. **Performs Exploratory Data Analysis (EDA)**.
4. **Generates visualizations** for payment count and amount by category.

---

## 🔍 Data Sources

All data is fetched from:

```
https://raw.githubusercontent.com/PhonePe/pulse/master/data/
```

Example path used:

```
aggregated/transaction/country/india/state/andhra-pradesh/2018/1.json
```

---

## 📦 Dependencies

Make sure to install the following Python packages:

```bash
pip install pandas numpy requests matplotlib seaborn
```

---

## 🚀 How It Works

### 🔹 1. Load Data

```python
response = requests.get(url)
data = response.json()
```

### 🔹 2. Flatten `paymentInstruments`

```python
# Extract 'count' and 'amount'
df['count'] = df['paymentInstruments'].apply(lambda x: x[0]['count'])
df['amount'] = df['paymentInstruments'].apply(lambda x: x[0]['amount'])
```

### 🔹 3. Create Metrics

```python
df['amount_per_transaction'] = df['amount'] / df['count']
```

### 🔹 4. Visualize

```python
sns.barplot(x='name', y='amount', data=df)
```

---

## 📊 Sample Visualizations

* **Bar charts** for:

  * Transaction Amount by Type (e.g., P2P, merchant)
  * Transaction Count by Type

---

## 📝 Notes

* The notebook currently analyzes only **Andhra Pradesh (Q1 2018)** data.
* You can extend it by looping over states/quarters/years.
* Error handling is implemented for invalid or missing URLs.

---

## 📈 Future Scope

* Add analysis for user data and map data.
* Build dashboards using Plotly/Dash or Streamlit.
* Automate the full data ingestion pipeline.

---

