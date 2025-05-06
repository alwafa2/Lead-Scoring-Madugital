# Lead Scoring Madugital
Proyek ini bertujuan untuk membangun model machine learning yang dapat memprediksi kemungkinan konversi prospek (leads) menjadi pelanggan. Dengan model ini, tim pemasaran dan penjualan dapat memprioritaskan prospek yang memiliki peluang konversi tinggi, sehingga meningkatkan efisiensi dan efektivitas strategi pemasaran.

#  Struktur Proyek

├── data/                 # Berisi dataset yang digunakan

├── model/                # Menyimpan model yang telah dilatih

├── madu.ipynb            # Notebook utama untuk analisis dan pemodelan

├── README.md             # Dokumentasi proyek

└── .gitattributes        # Pengaturan atribut Git

#  Teknologi dan Library
Proyek ini dibangun menggunakan Python dengan bantuan berbagai library:

- `pandas`, `numpy` – manipulasi dan analisis data
- `matplotlib.pyplot` – visualisasi data
- `os`, `pickle` – manajemen file dan penyimpanan model
- `scikit-learn`:
  - Model: `LogisticRegression`, `DecisionTreeClassifier`, `RandomForestClassifier`, `LinearRegression`, `KMeans`
  - Preprocessing: `StandardScaler`, `MinMaxScaler`
  - Evaluasi: `classification_report`, `f1_score`
  - Optimasi: `RandomizedSearchCV`
  - Data splitting: `train_test_split`
 
# Output & Evaluasi Model
Beberapa model dikembangkan dan dievaluasi dengan metrik precision, recall, f1-score, dan accuracy. Berikut ringkasannya:

| Model                      | Accuracy | F1 Score |
| -------------------------- | -------- | -------- |
| Logistic Regression        | 94%      | 0.92     |
| Decision Tree              | 92%      | 0.90     |
| Random Forest              | 94%      | 0.93     |
| **Random Forest (tuning)** | **94%**  | **0.93** |

## Best Parameters (Random Forest):

   ```python
{
  'n_estimators': 1000,
  'min_samples_split': 7,
  'min_samples_leaf': 1,
  'max_features': 'sqrt',
  'max_depth': 70,
  'bootstrap': True
}
```

# Fitur Terpenting
Model Random Forest menunjukkan bahwa fitur-fitur berikut memiliki kontribusi signifikan dalam prediksi konversi lead:

1. Tags_Will revert after reading the email

2. Total Time Spent on Website

3. Last Notable Activity_SMS Sent

4. Tags_Ringing

5. Lead Profile_Potential Lead

6. Tags_Not Specified

7. Lead Quality_Might be

8. Tags_Closed by Horizzon

9. Tags_Lost to EINS

10. Lead Quality_Not Specified

Fitur-fitur ini dapat menjadi fokus utama dalam strategi pemasaran digital perusahaan.


##  Cara Menjalankan

 Clone repositori ini:

   ```bash
   git clone https://github.com/alwafa2/Lead-Scoring-Madugital.git
   cd Lead-Scoring-Madugital
