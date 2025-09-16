# Machine-Learning
Sıfırdan başlayanlar için hazırlanan Makine Öğrenmesi yolculuğu. Temelden ileri seviye konulara, notlar ve projelerle uzmanlığa giden rehber.
---
# 🗺 Machine Learning Yol Haritası 

---

## 1. Temel Bilgi ve Matematiksel Altyapı

🎯 **Amaç:** ML algoritmalarının dayandığı matematik ve bilgisayar bilimi temelini kavramak.

* **Lineer Cebir** → Vektör, matris, determinant, eigenvalue, eigenvector, SVD.

  * 🔗 *Kullanımı:* PCA, boyut indirgeme, derin öğrenmede ağırlık matrisleri.

* **İstatistik & Olasılık** → Ortalama, varyans, kovaryans, dağılımlar (Normal, Bernoulli, Binomial, Poisson, Exponential).

  * 🔗 *Kullanımı:* Naive Bayes, regresyon varsayımları, olasılık tabanlı modeller.

* **Calculus** → Türev, zincir kuralı, integral.

  * 🔗 *Kullanımı:* Gradient Descent, optimizasyon, sinir ağı eğitimi.

* **Algoritmalar & Karmaşıklık** → Big-O Notation, temel veri yapıları.

  * 🔗 *Kullanımı:* ML algoritmalarının zaman/uzay karmaşıklığını anlamak.

* **Python Ekosistemi** → NumPy, Pandas, Matplotlib, Seaborn.

  * 🔗 *Kullanımı:* Veri işleme, görselleştirme, model hazırlığı.

---

## 2. Veri Ön İşleme ve Keşifsel Analiz (EDA)

🎯 **Amaç:** Veriyi anlamak, temizlemek, dönüştürmek.

* Eksik veri yönetimi (imputation).
* Ölçekleme → Normalization, Standardization.
* **Encoding** → One-Hot, Label, Target encoding.
* Outlier detection.
* Feature Engineering → Yeni özellik türetme, domain knowledge.
* Feature Selection → Korelasyon, PCA, RFE, mutual info.
* Görselleştirme → Histogram, scatter plot, heatmap.

---

## 3. Klasik Makine Öğrenmesi Modelleri

🎯 **Amaç:** Denetimli & denetimsiz temel algoritmaları öğrenmek.

* **Denetimli Öğrenme** → Linear/Logistic Regression, Decision Tree, Random Forest, Gradient Boosting (XGBoost, LightGBM, CatBoost), SVM, k-NN, Naive Bayes.
* **Denetimsiz Öğrenme** → K-Means, DBSCAN, Hierarchical Clustering.
* Boyut indirgeme → PCA, t-SNE, UMAP.
* Model Değerlendirme → Confusion Matrix, Precision, Recall, F1, ROC-AUC.
* Cross Validation & Hyperparameter Tuning.

---

## 4. Derin Öğrenme (Deep Learning)

🎯 **Amaç:** Yapay sinir ağlarıyla karmaşık veriler üzerinde çalışmak.

* **ANN** → Katmanlar, aktivasyon fonksiyonları, optimizasyon algoritmaları.
* Düzenlileştirme → Dropout, Batch Normalization.
* **CNN** → Görüntü işleme.
* **RNN, LSTM, GRU** → Zaman serisi & metin.
* **Transformers** → Attention, BERT, GPT.
* **Autoencoders & GANs** → Üretici modeller.
* 🔗 *Hangi model nerede kullanılır?*

  * Image → CNN.
  * Text → RNN, Transformer.
  * Tabular → Gradient Boosting, MLP.
  * Time-series → LSTM, GRU.

---

## 5. Model Performansı ve İyileştirme

🎯 **Amaç:** Overfitting/underfitting’i çözmek, model güvenilirliğini artırmak.

* Bias-Variance Tradeoff.
* L1 & L2 Regularization.
* Data Augmentation → rotation, flip, cutout, mixup.
* Transfer Learning.
* Explainable AI → SHAP, LIME.

---

## 6. Özel Konular ve Modern Yaklaşımlar

🎯 **Amaç:** Güncel ML/DL tekniklerini öğrenmek.

* Imbalanced Data → SMOTE, class weighting.
* Graph Neural Networks (GNNs).
* Reinforcement Learning (RL).
* LLMs → Fine-tuning, LoRA, PEFT.

---

## 7. Gerçek Dünya Projeleri

🎯 **Amaç:** Teoriyi uygulamaya dökmek.

* Klasik ML Projeleri → Iris, Titanic, Housing Price.
* DL Projeleri → MNIST, CIFAR-10, IMDb sentiment analysis.
* End-to-End Projeler →

  * Öneri sistemleri (film, ürün).
  * Sağlık tahminleri (diabet, kalp).
  * Finans (fraud detection, kredi skoru).
  * Tabular veri → churn prediction, kredi skoru.
  * Gerçek zamanlı uygulama → chatbot, anomaly detection.

---

## 🔥 Ek Bölüm: Veri Analizi ve Algoritma Seçimi

🎯 **Amaç:** Doğru veri → doğru algoritma → doğru model.

* EDA → Veri dağılımı ve ilişkileri inceleme.
* Veri türüne göre algoritma seçimi:

  * Sayısal → Regresyon.
  * Kategorik → Sınıflandırma.
  * Etiketsiz → Kümeleme.
  * Zaman serisi → ARIMA, LSTM.
  * Metin → Naive Bayes, Transformer.
* Feature Engineering → Encoding, scaling, domain knowledge.
* Model Interpretability → Hangi feature sonucu etkiliyor? (SHAP, LIME).

---
