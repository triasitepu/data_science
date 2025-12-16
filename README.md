📘 Judul Proyek
Analisis Perbandingan Model Baseline, Machine Learning, dan Deep Learning untuk Klasifikasi Penyakit Hepatitis C Berdasarkan Data Laboratorium Darah

👤 Informasi
Nama: Tria Wilujeng Rahayu br Sitepu
Repo: https://github.com/triasitepu/data_science.git
Video: https://drive.google.com/drive/folders/1kqHdqYFDP-c_E735wFDHX_XX184ZNbRv?usp=sharing
1. 🎯 Ringkasan Proyek
Proyek ini bertujuan untuk mengklasifikasi kondisi pasien berdasarkan data HCV (Hepatitis C Virus) ke dalam beberapa kategori, yaitu Blood Donor, Suspect Blood Donor, Hepatitis, Fibrosis, dan Cirrhosis, menggunakan dataset hcvdat0.csv. Dalam proyek ini dilakukan tahapan berikut:

Melakukan data cleaning & preparation, termasuk penanganan nilai hilang.
Melakukan encoding terhadap fitur kategorikal ('Sex') dan variabel target ('Category').
Membangun beberapa model klasifikasi:
Baseline Model: Logistic Regression
Advanced ML Model: Random Forest
Deep Learning Model: Multilayer Perceptron (MLP) dengan Scikit-learn
Deep Learning Model: Multilayer Perceptron (MLP) dengan Keras/TensorFlow
Melakukan evaluasi performa dan membandingkan hasil antar model.
Melakukan analisis feature importance untuk model Random Forest.
2. 📄 Problem & Goals
Problem Statements:
Klasifikasi kondisi Hepatitis C secara manual dapat rumit dan memakan waktu, memerlukan model prediktif yang akurat untuk membantu diagnosis.
Dataset HCV memiliki nilai hilang dan fitur kategorikal yang memerlukan preprocessing yang tepat untuk memastikan model dapat mempelajari pola dengan baik.
Terdapat ketidakseimbangan kelas (class imbalance) yang signifikan dalam dataset HCV, yang dapat memengaruhi performa model dan memerlukan teknik penanganan khusus seperti SMOTE.
Diperlukan perbandingan performa antara model baseline, model machine learning lanjutan, dan deep learning untuk menentukan pendekatan terbaik dalam klasifikasi kondisi Hepatitis C.
Memahami fitur-fitur laboratorium darah mana yang paling berkorelasi atau paling penting dalam memprediksi kondisi Hepatitis C.
Goals:
Mengembangkan empat model berbeda (Logistic Regression, Random Forest, Scikit-learn MLP, dan Keras MLP) untuk melakukan klasifikasi kondisi pasien Hepatitis C menggunakan dataset hcvdat0.csv.
Mencapai akurasi klasifikasi yang tinggi pada model terbaik sebagai indikator keberhasilan prediksi kondisi pasien.
Melakukan preprocessing data secara benar, termasuk imputasi nilai hilang, encoding fitur, scaling, dan penanganan class imbalance (SMOTE), serta pembagian data train–test, agar model dapat mempelajari pola secara optimal.
Mengevaluasi dan membandingkan performa keempat model menggunakan metrik seperti accuracy, precision, recall, dan f1-score untuk menentukan model paling efektif.
Mengidentifikasi fitur yang paling berpengaruh terhadap klasifikasi kondisi Hepatitis C melalui analisis feature importance.

project/
│
├── data/                   # Dataset (tidak di-commit, download manual)
│
├── notebooks/              # Jupyter notebooks
│   └── mushroom.ipynb
│
├── src/                    # Source code
│   
├── models/                 # Saved models
│   ├── lmodel_baseline_logistic_regression.pkl
│   ├── ml_random_forest_smote.pkl
│   └── deep_learning_mlp_smote.pkl
│
├── images/                 # Visualizations
│   └── Confusion Matrix_logistic regression.png
│   └── Confusion_Matrix_RandomForest.png
│   └── Confusion_Matrix_Keras MLP.png
│   └── Confusion_Matrix_MLP Classifier.png
│   └── Distribusi Kategori Penyakit Hepatitis C.png
│   └── Feature Importance.png
│   └── Heatmap Korelasi Antar Fitur Laboratorium Darah.png
│   └── Perbandingan Metrik Kinerja Antar Model.png
│   └── Plot histogram semua fitur.png
│   └── Model Loss Over Epoch.png
│
├── requirements.txt        # Dependencies
├── Checklist_Submit.md
├── .gitignore
└── README.md

3. 📊 Dataset
Sumber: UCI Machine Learning Repository
Jumlah Data: 615
Tipe: Structured tabular data 
Fitur Utama


Fitur	Deskripsi
Age	Usia pasien
Sex	Jenis kelamin pasien (sudah di-encode)
ALB	Albumin
ALP	Alkaline Phosphatase
ALT	Alanine Aminotransferase
AST	Aspartate Aminotransferase
BIL	Bilirubin
CHE	Cholinesterase
CHOL	Cholesterol
CREA	Creatinine
GGT	Gamma-Glutamyl Transferase
PROT	Protein Total


4. 🔧 Data Preparation
Cleaning (missing/duplicate/outliers): Penanganan nilai hilang dengan imputasi median. Tidak ada duplikasi yang terdeteksi. Outlier ditangani secara implisit oleh RobustScaler.
Transformasi (encoding/scaling):
Sex di-encode dengan LabelEncoder.
Target Category di-encode dengan LabelEncoder.
Fitur numerik diskalakan menggunakan RobustScaler untuk menangani outlier.
Ketidakseimbangan kelas ditangani menggunakan SMOTE pada data pelatihan.
Splitting (train/val/test): Data dibagi menjadi 80% data pelatihan dan 20% data pengujian (train_test_split dengan random_state=42 dan stratify).
5. 🤖 Modeling
Model 1 – Baseline: Logistic Regression (dilatih dengan pipeline yang menyertakan imputasi, scaling, dan SMOTE).
Model 2 – Advanced ML: Random Forest Classifier (dilatih dengan pipeline yang menyertakan imputasi, scaling, dan SMOTE).
Model 3 – Deep Learning:
MLP Classifier dari Scikit-learn (dilatih dengan pipeline yang menyertakan imputasi, scaling, dan SMOTE).
Keras MLP (model Sequential dengan 2 hidden layer, dilatih dengan data hasil SMOTE dan scaling).
6. 🧪 Evaluation
Metrik: Accuracy, Precision, Recall, F1-Score (rata-rata tertimbang atau per kelas).

Hasil Singkat
Model	Accuracy	Weighted Avg F1-Score	Catatan
Logistic Regression	0.9756	0.97	Performa sangat baik, terutama untuk kelas mayoritas.
Random Forest	1.0000	1.00	Performa sempurna pada data uji, potensi overfitting.
Scikit-learn MLP	0.9593	0.96	Performa baik, sedikit di bawah RF dan LR.
Keras MLP	0.9675	0.97	Performa baik, menunjukkan stabilitas loss dan akurasi.
7. 🏁 Kesimpulan
Model terbaik: Random Forest

Performa:

Accuracy = 1.00

Precision = 1.00

Recall = 1.00

Alasan:

Mampu menangkap pola non-linear dengan sangat baik.
Robust terhadap noise dan variabilitas fitur.
Kinerjanya stabil pada dataset tabular seperti klasifikasi jamur.
Menghasilkan performa sempurna tanpa kehilangan generalisasi.
Insight:

Model sederhana seperti Logistic Regression saja sudah memberikan akurasi sangat tinggi (~99.88%), menandakan dataset ini mudah dipelajari.
Model Random Forest mampu mencapai performa sempurna karena dapat menangkap interaksi fitur yang tidak dapat ditangani dengan baik oleh model linear.
Model Deep Learning tidak unggul pada dataset tabular kecil seperti ini, sehingga performanya lebih rendah meskipun arsitektur dan hyperparameter sudah dioptimalkan
8. 🔮 Future Work
Tambah data: Mengumpulkan lebih banyak data, terutama untuk kelas-kelas minoritas, untuk meningkatkan generalisasi model.
Tuning model: Melakukan hyperparameter tuning yang lebih ekstensif untuk semua model (misalnya, GridSearchCV, RandomizedSearchCV) untuk menemukan kombinasi parameter optimal.
Coba arsitektur DL lain: Mengeksplorasi arsitektur Deep Learning yang lebih kompleks atau mencoba model lain (misalnya, Gradient Boosting, XGBoost).
Analisis Overfitting: Melakukan validasi silang yang lebih ketat atau menggunakan teknik regulasi tambahan untuk memitigasi potensi overfitting, terutama pada model Random Forest yang mencapai akurasi sempurna.
Interpretability: Menganalisis lebih lanjut interpretasi model, terutama untuk model Deep Learning.
Deployment: Mengembangkan aplikasi web atau API untuk memprediksi kondisi Hepatitis C secara real-time.
9. 🔁 Reproducibility
Gunakan Environment: python -m venv environment environment\Script\activate

Install Dependencies: pip install -r requirements.txt

Install Library: pip install pandas seaborn matplotlib scikit-learn pip install tensorflow