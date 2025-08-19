# 🏦 Analisis Prediksi Customer Churn Nasabah Bank Menggunakan Machine Learning

Sistem ini membangun pipeline machine learning end-to-end untuk **memprediksi churn nasabah bank** secara proaktif, membongkar faktor-faktornya, serta mengoptimalkan dampak bisnis melalui analisis ROI kampanye retensi. Proyek ini dirancang untuk siap produksi, mudah diintegrasikan, dan didukung oleh best practice data science terkini.

---

## 📚 Daftar Isi

- [Latar Belakang & Konteks](#latar-belakang--konteks)
- [Rumusan Masalah](#rumusan-masalah)
- [Tujuan Penelitian](#tujuan-penelitian)
- [Dataset](#dataset)
- [Alur Kerja (Workflow)](#alur-kerja-workflow)
- [Struktur Folder & File](#struktur-folder--file)
- [Instalasi dan Setup](#instalasi-dan-setup)
- [Cara Menjalankan Notebook](#cara-menjalankan-notebook)
- [Penjelasan Pipeline dan Model](#penjelasan-pipeline-dan-model)
- [Hasil & Evaluasi](#hasil--evaluasi)
- [Business Impact & ROI](#business-impact--roi)
- [Interprestasi Model & Insights Bisnis](#interprestasi-model--insights-bisnis)
- [Roadmap Pengembangan](#roadmap-pengembangan)
- [Continuous Improvement](#continuous-improvement)
- [Referensi](#referensi)
- [Kontributor](#kontributor)

---

## 📋 Latar Belakang & Konteks

Industri perbankan menghadapi tantangan besar untuk **mempertahankan nasabah** di tengah persaingan fintech dan digital banking. Churn nasabah (berhenti menggunakan layanan) berdampak besar pada profitabilitas, _customer lifetime value_, dan efisiensi bisnis. Machine learning dapat membantu bank:
- Mendeteksi _early warning signals_ churn
- Mengidentifikasi faktor utama penyebab churn
- Mempersonalisasi strategi retensi
- Mengoptimalkan ROI kampanye retensi

---

## ❓ Rumusan Masalah

Bagaimana bank dapat **secara proaktif mengidentifikasi nasabah loyal yang berisiko churn** dan memahami _root cause_-nya untuk optimalisasi strategi retensi?

Sub-masalah:
1. Deteksi dini risiko churn
2. Analisis faktor utama (root cause)
3. Optimasi dampak bisnis (threshold, ROI)
4. Integrasi dan monitoring model

---

## 🎯 Tujuan Penelitian

- Membangun model prediksi churn dengan **akurasi tinggi** (target PR AUC > 0.85)
- Mengimplementasikan best practice anti-leakage
- Mengidentifikasi _top factors_ churn untuk actionable insights
- Membuat pipeline siap produksi, mudah diintegrasikan, dan dapat _continuous monitoring_

---

## 📦 Dataset

- **Source utama:** BankChurners.csv (dataset publik industri perbankan)
- **Size:** 10.127 nasabah, 23 fitur
- **Target:** `Attrition_Flag` (di-mapping ke Churn 0/1)
- **Fitur:** Demografi, transaksi, produk, perilaku, dsb.
- **Note:** Data loyal (≥6 bulan) dan _leakage columns_ dihapus.

---

## 🔗 Struktur Folder & File

```
.
├── Analisis Prediksi Customer Churn Nasabah Bank Menggunakan Machine Learning.ipynb  # Notebook utama
├── models/         # Model terlatih, artifact pickled
├── reports/        # Grafik, laporan evaluasi
├── artifacts/      # Metrics, config, feature importance, dsb
├── BankChurners.csv
├── requirements.txt
├── README.md
```

---

## ⚙️ Instalasi dan Setup

### 1. Clone Repository
```bash
git clone https://github.com/mbulusfamily/Analisis-Prediksi-Customer-Churn-Nasabah-Bank-Menggunakan-Machine-Learning.git
cd Analisis-Prediksi-Customer-Churn-Nasabah-Bank-Menggunakan-Machine-Learning
```

### 2. Install Dependencies
Disarankan menggunakan **virtual environment** (conda/venv).
```bash
pip install -r requirements.txt
```
_Package utama:_ numpy, pandas, scikit-learn, xgboost, imbalanced-learn, matplotlib, shap, joblib, scipy, dll.

### 3. Siapkan Data
Pastikan file **BankChurners.csv** tersedia di folder utama.

---

## 🚀 Cara Menjalankan Notebook

1. Buka Jupyter Notebook/Lab
2. Jalankan notebook utama:  
   `Analisis Prediksi Customer Churn Nasabah Bank Menggunakan Machine Learning.ipynb`
3. Ikuti cell step-by-step untuk:
   - Data loading, validasi, anti-leakage
   - EDA & preprocessing pipeline
   - Train-test split (stratified, anti-leakage)
   - Modeling (Logistic Regression, Random Forest, XGBoost)
   - Hyperparameter tuning (cross-validation PR AUC)
   - Evaluasi holdout set
   - Optimasi threshold dan ROI
   - Interpretasi model (feature importance, SHAP)
   - Output artifacts siap produksi

---

## 📝 Penjelasan Pipeline dan Model

- **Preprocessing:** Imputasi, scaling numeric, one-hot categorical. Semua dilakukan dalam pipeline untuk cegah _data leakage_.
- **Model candidates:** Logistic Regression, Random Forest, XGBoost.
- **Imbalance handling:** SMOTE, scale_pos_weight (XGBoost), class_weight (sklearn).
- **Hyperparameter tuning:** RandomizedSearchCV dengan cross-validation (PR AUC utama).
- **Evaluasi:** Confusion matrix, precision, recall, F1, ROC AUC, PR AUC.
- **Threshold optimization:** ROI-based untuk bisnis, bukan default 0.5.
- **Interpretability:** Feature importance & SHAP values untuk explainability ke stakeholder non-teknis.

---

## 📈 Hasil & Evaluasi

- **Best model:** XGBoost
- **ROC AUC:** 0.993
- **PR AUC:** 0.967
- **Precision:** 98%
- **Recall:** 58% (threshold optimal bisnis)
- **Threshold optimal:** 0.990 (ROI-based)
- **Confusion matrix, PR/ROC curves:** Tersedia di folder reports/artifacts

---

## 💰 Business Impact & ROI

- **ROI kampanye retensi (based on model):** 8.84x
- **Precision tinggi** → targeting efisien, minim false positive
- **Recall cukup** → >50% nasabah churn terdeteksi
- **Recommended actions:** Pilot 100-500 nasabah high-risk, dashboard monitoring, training CS, A/B testing kampanye

---

## 🔍 Interprestasi Model & Insights Bisnis

- **Faktor utama churn:**  
  1. Aktivitas transaksi rendah  
  2. Saldo bergulir rendah  
  3. Nilai transaksi rendah
- **Insights:**  
  - Early warning system bisa monitoring harian
  - Personalisasi kampanye retensi sesuai profil risiko
  - Targeting cost-effective hanya pada nasabah high-probability

---

## 🛣️ Roadmap Pengembangan

1. Foundation & Data Preparation (done)
2. Model Development & Tuning (done)
3. Business Optimization (done)
4. Interpretability & Insights (done)
5. Production Readiness (done)
6. Advanced Experimentation (done)
7. Implementation Planning (ongoing)
8. Continuous Improvement (ongoing)

---

## 🔄 Continuous Improvement

- **Model drift detection**
- **Periodic retraining**
- **Performance dashboard**
- **Business impact tracking**
- **Integration with CRM & real-time scoring**

---

## 📚 Referensi

- [BankChurners Dataset](https://www.kaggle.com/datasets/sakshigoyal7/credit-card-customers)
- [scikit-learn Documentation](https://scikit-learn.org/)
- [XGBoost Documentation](https://xgboost.readthedocs.io/)
- [SHAP Explainability](https://shap.readthedocs.io/)
- Literatur churn prediction banking: [Google Scholar](https://scholar.google.com/scholar?q=bank+customer+churn+machine+learning)

---

## 👥 Kontributor

- mbulusfamily (owner & author)
- [OpenAI Copilot](https://github.com/features/copilot) (ide, support, automation)

---

**🚀 Siap diimplementasikan untuk deployment produksi & integrasi dengan sistem bank!**

Jika ada pertanyaan, saran, atau request fitur tambahan, silakan buka [Issue](https://github.com/mbulusfamily/Analisis-Prediksi-Customer-Churn-Nasabah-Bank-Menggunakan-Machine-Learning/issues) di repo ini.
