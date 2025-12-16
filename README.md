
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
- **Scikit-learn MLP:** Pipeline sama seperti di atas  
- **Keras MLP:** 2 hidden layer, optimizer Adam, batch size 32, epochs 50, validation split 0.2, callbacks: EarlyStopping, ReduceLROnPlateau  

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
