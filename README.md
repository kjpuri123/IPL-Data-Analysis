# 🏏 IPL Win Probability Predictor

A machine learning project that predicts the **live win probability** of an IPL team while chasing a target, based on real match conditions.

---

## 📌 Overview

This project uses ball-by-ball IPL match data to train a **Logistic Regression** model that estimates how likely the batting (chasing) team is to win at any point during the second innings of a T20 match.

---

## 🚀 Features

- Cleans and preprocesses raw IPL ball-by-ball data
- Engineers key cricket features: runs left, balls left, wickets remaining, CRR, RRR
- Handles team renames across IPL seasons (e.g., Delhi Daredevils → Delhi Capitals)
- Filters data to only the 10 current active IPL franchises
- Trains a Logistic Regression pipeline with One-Hot Encoding + Standard Scaling
- Saves the trained model as `pipe.pkl` using `pickle`
- Provides an **interactive Jupyter widget** to predict win probability on custom inputs

---

## 📂 Project Structure

```
IPL-Win-Predictor/
│
├── IPL.ipynb                    # Main notebook (EDA + Model training + Widget)
├── IPL.csv.xls                  # Raw ball-by-ball dataset
├── IPL_processed_dataset.csv    # Cleaned & feature-engineered dataset
├── pipe.pkl                     # Saved trained model pipeline
├── requirements.txt             # Python dependencies
└── README.md                    # Project documentation
```

---

## 🧠 Model Details

| Component       | Details                              |
|-----------------|--------------------------------------|
| Algorithm       | Logistic Regression                  |
| Solver          | `liblinear`                          |
| Encoding        | One-Hot Encoding (categorical cols)  |
| Scaling         | Standard Scaler (numeric cols)       |
| Train/Test Split| 75% / 25%                            |
| Target Variable | `result` (1 = batting team wins)     |

### Input Features

| Feature              | Description                              |
|----------------------|------------------------------------------|
| `batting_team`       | Team currently batting (chasing)         |
| `bowling_team`       | Team currently bowling (defending)       |
| `city`               | Venue city of the match                  |
| `runs_left`          | Runs still needed to win                 |
| `balls_left`         | Legal deliveries remaining               |
| `wickets_remaining`  | Wickets in hand for the batting team     |
| `runs_target`        | Total runs target set by the first team  |
| `crr`                | Current Run Rate                         |
| `rrr`                | Required Run Rate                        |

---

## ⚙️ Setup & Usage

### 1. Clone the repository
```bash
git clone https://github.com/your-username/IPL-Win-Predictor.git
cd IPL-Win-Predictor
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the notebook
Open `IPL.ipynb` in **Jupyter Notebook** or **Google Colab** and run all cells.

> **Note:** Update the file path in `pd.read_csv(...)` to match your local data location if not using Colab.

### 4. Use the interactive predictor widget
At the end of the notebook, an **ipywidgets** form lets you enter live match conditions and click **"Predict Win Probability"** to get real-time predictions for both teams.

---

## 📊 Sample EDA Output

- Bar chart: Win % while chasing — by team
- Visualization of key features vs. match outcome

---

## 📋 Requirements

See [`requirements.txt`](requirements.txt) for the full list of dependencies.

---

## 🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you'd like to change.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

