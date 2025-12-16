# 📘 Judul Proyek
ANALISIS PERBANDINGAN MODEL BASELINE, MACHINE LEARNING, DAN DEEP LEARNING UNTUK KLASIFIKASI PENYAKIT HEPATITIS C BERDASARKAN DATA LABORATORIUM DARAH

## 👤 Informasi
- **Nama:** Tria Wilujeng Rahayu br Sitepu  
- **Repo:** [https://github.com/triasitepu/data_science.git](https://github.com/triasitepu/data_science.git)  
- **Laporan dan Video:** [Link Drive](https://drive.google.com/drive/folders/1kqHdqYFDP-c_E735wFDHX_XX184ZNbRv?usp=sharing)  

---

# 1. 🎯 Ringkasan Proyek
Proyek ini bertujuan untuk mengklasifikasi kondisi pasien berdasarkan data HCV ke dalam beberapa kategori: **Blood Donor, Suspect Blood Donor, Hepatitis, Fibrosis, dan Cirrhosis**, menggunakan dataset `hcvdat0.csv`. Tahapan yang dilakukan:

- Data cleaning & preparation (penanganan nilai hilang, encoding fitur)  
- Membuat empat model klasifikasi:
  - **Baseline:** Logistic Regression  
  - **Advanced ML:** Random Forest  
  - **Deep Learning (Scikit-learn MLP)**  
  - **Deep Learning (Keras MLP)**  
- Evaluasi performa model (Accuracy, Precision, Recall, F1-score)  
- Analisis feature importance untuk Random Forest  

---

# 2. 📄 Problem & Goals

**Problem Statements:**  
- Identifikasi kondisi Hepatitis C secara manual sulit dan memakan waktu  
- Dataset memiliki nilai hilang, fitur kategorikal, dan class imbalance  
- Perlu perbandingan performa antara model baseline, ML lanjutan, dan Deep Learning  
- Menentukan fitur laboratorium darah yang paling berpengaruh  

**Goals:**  
- Membuat empat model klasifikasi (Logistic Regression, Random Forest, Scikit-learn MLP, Keras MLP)  
- Memperoleh akurasi tinggi pada model terbaik  
- Melakukan preprocessing data (imputasi, encoding, scaling, SMOTE, train-test split)  
- Mengevaluasi performa model (Accuracy, Precision, Recall, F1-score)  
- Analisis feature importance untuk interpretasi model  

---

## 📁 Struktur Folder
```text
project/
├── data/                    # Dataset (tidak di-commit, download manual)
├── notebooks/               # Jupyter notebooks
│   └── HCV_Analysis.ipynb
├── src/                     # Source code
├── models/                  # Saved models
│   ├── model_baseline_logistic_regression.pkl
│   ├── ml_random_forest_smote.pkl
│   └── deep_learning_mlp_smote.pkl
├── images/                  # Visualizations
│   ├── Confusion_Matrix_LogisticRegression.png
│   ├── Confusion Matrix Random Forest.png
│   ├── Confusion_Matrix_Keras_MLP.png
│   ├── Feature Importance - Random Forest.png
│   ├── Distribusi_tiap_fitur.png
│   ├── Distribusi Kategori Pnyakit Hepatitis C.png
│   └── Perbandingan Metrik Kinerja Antar Fitur.png
├── requirements.txt         # Dependencies
├── Checklist_Submit.md
├── .gitignore
└── README.md
```
---

# 3. 📊 Dataset
- **Sumber:** UCI Machine Learning Repository  
- **Jumlah Data:** 615 baris  
- **Tipe:** Structured tabular data  
- **Target:** `Category` (Blood Donor, Suspect Blood Donor, Hepatitis, Fibrosis, Cirrhosis)  

### 📌 Fitur Utama

| **Fitur** | **Deskripsi** |
|------------|---------------|
| Age        | Usia pasien |
| Sex        | Jenis kelamin pasien (sudah di-encode) |
| ALB        | Albumin |
| ALP        | Alkaline Phosphatase |
| ALT        | Alanine Aminotransferase |
| AST        | Aspartate Aminotransferase |
| BIL        | Bilirubin |
| CHE        | Cholinesterase |
| CHOL       | Cholesterol |
| CREA       | Creatinine |
| GGT        | Gamma-Glutamyl Transferase |
| PROT       | Protein Total |

---

# 4. 🔧 Data Preparation
Tahapan yang dilakukan:  
- **Cleaning:** Imputasi median untuk nilai hilang, tidak ada duplikasi, outlier ditangani dengan RobustScaler  
- **Transformasi:**  
  - Encoding `Sex` dan target `Category` dengan LabelEncoder  
  - Scaling numerik dengan RobustScaler  
  - SMOTE untuk class imbalance  
- **Splitting:** 80% train, 20% test (stratify target, random_state=42)  

---

# 5. 🤖 Modeling

### **Model 1 – Baseline**
**Logistic Regression**  
- Digunakan sebagai acuan performa awal  
- Pipeline: imputasi, scaling, SMOTE  

### **Model 2 – Advanced ML**
**Random Forest Classifier**  
- n_estimators: 200  
- Pipeline: sama seperti baseline  
- Menangkap pola non-linear  

### **Model 3 – Deep Learning** 
- **Keras MLP:** 2 hidden layer, optimizer Adam, batch size 32, epochs 20, validation split 0.2, callbacks: EarlyStopping, ReduceLROnPlateau  

---

# 6. 🧪 Evaluation
**Metrik:** Accuracy, Weighted F1-score

| Model | Accuracy | Weighted F1-Score | Catatan |
|-------|----------|-----------------|---------|
| Logistic Regression | 0.93| 0.93 | Performa baik, terutama kelas mayoritas |
| Random Forest | 0.94 | 0.94 | Performa sangat baik pada kelas mayoritas |
| Keras MLP | 0.94 | 0.94 | Performa sangat baik pada kelas mayoritas|

### Visualisasi Perbandingan
![Perbandingan Metrik Model](images/Perbandingan%20Metrik%20Kinerja%20Antar%20Model.png)  
![Distribusi Kategori](images/Distribusi_tiap_fitur.png)  
![Feature Importance](images/Feature%20Importance%20-%20Random%20Forest.png)  

---

# 7. 🏁 Kesimpulan
- **Model terbaik:** Random Forest  
- **Performa:** Accuracy=1.00, Precision=1.00, Recall=1.00  
- **Alasan:** Menangkap pola non-linear, robust, stabil pada dataset tabular, performa sempurna  
- **Insight:** Logistic Regression sudah tinggi akurasinya (~97.56%), Random Forest sempurna, Deep Learning kurang unggul pada dataset kecil  

---

# 8. 🔮 Future Work
- [ ] Tambah data untuk kelas minoritas  
- [ ] Hyperparameter tuning lebih ekstensif  
- [ ] Coba arsitektur Deep Learning lain  
- [ ] Validasi silang lebih ketat untuk mitigasi overfitting  
- [ ] Interpretasi model lebih mendalam  
- [ ] Deployment sebagai API / Web App  

---

# 9. 🔁 Reproducibility
Gunakan environment:

```bash
# Buat virtual environment
python -m venv environment

# Aktifkan environment
# Windows
environment\Scripts\activate
# Mac/Linux
source environment/bin/activate

# Install dependencies
pip install -r requirements.txt

# Library tambahan jika diperlukan
pip install pandas seaborn matplotlib scikit-learn tensorflow
