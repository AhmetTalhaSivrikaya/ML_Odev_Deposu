#  İşe Alım Tahmini - Sınıflandırma Modelleri Karşılaştırması

Bu projede, adayların akademik başarım metrikleri, mülakat puanları ve iş deneyimleri kullanılarak **işe alınıp alınmayacağını (Placed / Not Placed)** tahmin eden ikili bir sınıflandırma (binary classification) modeli geliştirilmiştir. 

---

##  Kullanılan Teknolojiler ve Kütüphaneler

| Kategori | Teknolojiler / Metotlar |
| :--- | :--- |
| **Dil & Ortam** | Python 3.13+ |
| **Veri Analizi** | Pandas, NumPy |
| **Görselleştirme** | Matplotlib |
| **Ön İşleme (Preprocessing)** | `StandardScaler`, `LabelEncoder`, `train_test_split` (%70 Eğitim, %30 Test) |
| **Algoritmalar** | Logistic Regression, Decision Tree, KNN, Support Vector Machine (SVM) |

---

##  Genel Model Performans Karşılaştırması

| Model | Doğruluk (Accuracy) | Doğruluk (%) | Performans Durumu |
| :--- | :---: | :---: | :--- |
| **Lojistik Regresyon** | **0.8154** | **%81.54** | 🥇 En Yüksek Başarım (Ölçeklenmiş Veri) |
| **KNN (K-Nearest Neighbors)** | 0.7692 | %76.92 | 🥈 Dengeli Performans |
| **SVM (Support Vector Machine)** | 0.7538 | %75.38 | 🥉 Kararlı Ayrıştırma |
| **Karar Ağacı (Decision Tree)** | 0.7385 | %73.85 | 🎗️ Temel Kural Tabanlı |

---

##  Detaylı Karmaşıklık Matrisleri (Confusion Matrices) ve Metrikler

### 1. Lojistik Regresyon (Accuracy: %81.54)

| Gerçek / Tahmin | Tahmin: Not Placed (0) | Tahmin: Placed (1) |
| :--- | :---: | :---: |
| **Gerçek: Not Placed (0)** | **10** (Doğru Negatif) | **10** (Yanlış Pozitif) |
| **Gerçek: Placed (1)** | **2** (Yanlış Negatif) | **43** (Doğru Pozitif) |

---

### 2. KNN - K-Nearest Neighbors (Accuracy: %76.92)

| Gerçek / Tahmin | Tahmin: Not Placed (0) | Tahmin: Placed (1) |
| :--- | :---: | :---: |
| **Gerçek: Not Placed (0)** | **8** (Doğru Negatif) | **12** (Yanlış Pozitif) |
| **Gerçek: Placed (1)** | **3** (Yanlış Negatif) | **42** (Doğru Pozitif) |

---

### 3. SVM - Support Vector Machine (Accuracy: %75.38)

| Gerçek / Tahmin | Tahmin: Not Placed (0) | Tahmin: Placed (1) |
| :--- | :---: | :---: |
| **Gerçek: Not Placed (0)** | **6** (Doğru Negatif) | **14** (Yanlış Pozitif) |
| **Gerçek: Placed (1)** | **2** (Yanlış Negatif) | **43** (Doğru Pozitif) |

---

### 4. Karar Ağacı - Decision Tree (Accuracy: %73.85)

| Gerçek / Tahmin | Tahmin: Not Placed (0) | Tahmin: Placed (1) |
| :--- | :---: | :---: |
| **Gerçek: Not Placed (0)** | **9** (Doğru Negatif) | **11** (Yanlış Pozitif) |
| **Gerçek: Placed (1)** | **6** (Yanlış Negatif) | **39** (Doğru Pozitif) |

---

##  Analiz ve Değerlendirme Tablosu

| İnceleme Alanı | Tespit Edilen Sonuç ve Analiz |
| :--- | :--- |
| **Veri Ölçekleme Etkisi** | Lojistik Regresyon, KNN ve SVM algoritmaları `StandardScaler` ile ölçeklendirildiğinde performans yükselmiştir. Lojistik Regresyon %81.54 ile zirvede yer almıştır. |
| **Sınıf Yakalama Oranı** | Tüm modeller `Placed (1)` sınıfını yüksek oranla doğru tahmin ederken (%90+ recall), azınlıkta olan `Not Placed (0)` sınıfını tahmin etmekte zorlanmıştır. |
| **Model Tipi Farkı** | Ağaç tabanlı modeller bu veri seti boyutunda aşırı öğrenmeye (overfitting) meylli olduğu için doğrusal ve mesafe tabanlı modellerin gerisinde kalmıştır. |

---
