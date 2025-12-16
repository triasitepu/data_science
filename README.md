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
UAS_HCV/
│
├── data/                   # Dataset (tidak di-commit, download manual)
│
├── notebooks/              # Jupyter notebooks
│   └── HCV_Analysis.ipynb
│
├── src/                    # Source code
│
├── models/                 # Saved models
│   ├── lmodel_baseline_logistic_regression.pkl
│   ├── ml_random_forest_smote.pkl
│   └── deep_learning_mlp_smote.pkl
│
├── images/                 # Visualizations
│   ├── Confusion_Matrix_LogisticRegression.png
│   ├── Confusion_Matrix_RandomForest.png
│   ├── Confusion_Matrix_Keras_MLP.png
│   ├── Feature_Importance.png
│   ├── Distribusi_Kategori.png
│   └── Perbandingan_Metrik_Model.png
│
├── requirements.txt        # Dependencies
├── Checklist_Submit.md
├── .gitignore
└── README.md



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
- **Scikit-learn MLP:** Pipeline sama seperti di atas  
- **Keras MLP:** 2 hidden layer, optimizer Adam, batch size 32, epochs 20, validation split 0.2, callbacks: EarlyStopping, ReduceLROnPlateau  

---

# 6. 🧪 Evaluation
**Metrik:** Accuracy, Weighted F1-score

| Model | Accuracy | Weighted F1-Score | Catatan |
|-------|----------|-----------------|---------|
| Logistic Regression | 0.9756 | 0.97 | Performa baik, terutama kelas mayoritas |
| Random Forest | 1.0000 | 1.00 | Performa sempurna, potensi overfitting |
| Scikit-learn MLP | 0.9593 | 0.96 | Performa baik, sedikit di bawah RF dan LR |
| Keras MLP | 0.9675 | 0.97 | Stabil, performa baik |

### Visualisasi Perbandingan
![Perbandingan Metrik Model](images/Perbandingan_Metrik_Model.png)  
![Distribusi Kategori](images/Distribusi_Kategori.png)  
![Feature Importance](images/Feature_Importance.png)  

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
