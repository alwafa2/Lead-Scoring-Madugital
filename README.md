# Lead Scoring Madugital
Proyek ini bertujuan untuk membangun model machine learning yang dapat memprediksi kemungkinan konversi prospek (leads) menjadi pelanggan. Dengan model ini, tim pemasaran dan penjualan dapat memprioritaskan prospek yang memiliki peluang konversi tinggi, sehingga meningkatkan efisiensi dan efektivitas strategi pemasaran.

## 🗂️  Struktur Proyek
```
.
├── data/                         # Dataset dan file pendukung
├── model/                        # File model yang sudah dilatih (jika ada)
├── madu.ipynb                    # Notebook utama untuk eksplorasi dan modeling
├── BACA SAYA TERLEBIH DAHULU.txt # Catatan awal penggunaan proyek
├── README.md                     # Dokumentasi proyek
└── .gitattributes                # Pengaturan atribut Git
```

## 🧰  Teknologi dan Library
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
 
## 📈 Output & Evaluasi Model
Beberapa model dikembangkan dan dievaluasi dengan metrik precision, recall, f1-score, dan accuracy. Berikut ringkasannya:

| Model                      | Accuracy | F1 Score |
| -------------------------- | -------- | -------- |
| Logistic Regression        | 94%      | 0.92     |
| Decision Tree              | 92%      | 0.90     |
| Random Forest              | 94%      | 0.93     |
| **Random Forest (tuning)** | **94%**  | **0.93** |

**Best Parameters (Random Forest)**

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

## 🔍 Fitur Terpenting
Model Random Forest menunjukkan bahwa fitur-fitur berikut memiliki kontribusi signifikan dalam prediksi konversi lead:

- `Tags_Will revert after reading the email`
- `Total Time Spent on Website`
- `Last Notable Activity_SMS Sent`
- `Tags_Ringing`
- `Lead Profile_Potential Lead`
- `Tags_Not Specified`
- `Lead Quality_Might be`
- `Tags_Closed by Horizzon`
- `Tags_Lost to EINS`
- `Lead Quality_Not Specified`

Fitur-fitur ini dapat menjadi fokus utama dalam strategi pemasaran digital perusahaan.

## 🚀 Deployment dan Prediksi Individual

Setelah model dan preprocessor disimpan, kamu bisa memuatnya kembali dan melakukan prediksi terhadap satu input data baru.

### 🔒 Menyimpan Model dan Preprocessor

```python
if not os.path.exists('model'):
    os.mkdir('model')

pickle.dump(best_rf_model, open('model/best_rf_model.sav', 'wb'))
pickle.dump(preprocessor, open('model/preprocessor.sav', 'wb'))
```

### 📤 Memuat dan Menggunakan Model

```python
best_rf_model = pickle.load(open('model/best_rf_model.sav', 'rb'))
preprocessor = pickle.load(open('model/preprocessor.sav', 'rb'))

data = { 'Prospect ID': '2a369e36-ca95-4ca9-9e4f-9d27175aa320', ... }

data_df = pd.DataFrame([data])
data_preprocessed = preprocessor.transform(data_df)
probability = best_rf_model.predict_proba(data_preprocessed)[0][1]
score = round(probability * 100, 2)

if probability < 0.5:
    category = 'COLD'
elif probability >= 0.75:
    category = 'HOT'
else:
    category = 'WARM'

print(f"Customer dengan ID {data['Prospect ID']} masuk kategori {category} leads dengan score: {score}")
```

📌 **Contoh Output**:

```
Customer dengan ID 2a369e36-ca95-4ca9-9e4f-9d27175aa320, masuk dalam kategori HOT leads, dengan score : 84.95
```


## 🚀 Cara Menjalankan

1. Clone repositori ini:

   ```bash
   git clone https://github.com/alwafa2/Lead-Scoring-Madugital.git
   cd Lead-Scoring-Madugital
   ```

2. (Opsional) Buat virtual environment dan aktifkan:

   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   venv\Scripts\activate   # Windows
   ```

3. Install dependencies:

   ```bash
   pip install pandas numpy matplotlib scikit-learn
   ```

4. Jalankan notebook:

   ```bash
   jupyter notebook madu.ipynb
   ```


