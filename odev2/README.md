# Regresyon Modelleri Test Sonuçları ve Analizi

Oluşturulan veri seti üzerinden eğitilen 5 farklı regresyon modelinin (Doğrusal, Ridge, Lasso, ElasticNet ve Bayesian Ridge) test sonuçları, hata metrikleri ve denklem parametreleri aşağıda detaylandırılmıştır.

## Model Performans Karşılaştırması

| Model | R² Skoru | MSE | RMSE | MAE | Intercept (Kesişim) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Çoklu Doğrusal Regresyon** | 0.2195 | 604.3572 | 24.5837 | 16.8495 | 49.0947 |
| **Ridge Regresyon (L2)** | 0.2195 | 604.3572 | 24.5837 | 16.8495 | 49.0969 |
| **Lasso Regresyon (L1)** | 0.2195 | 604.3572 | 24.5837 | 16.8487 | 49.0893 |
| **ElasticNet Regresyon** | 0.2195 | 604.3572 | 24.5837 | 16.8491 | 49.0939 |
| **Bayesian Ridge** | 0.1140 | 686.0122 | 26.1918 | 18.5065 | 68.7532 |

---

## Denklem Parametreleri, Katsayılar ve Standart Hatalar

Tüm modeller için değişkenlerin ağırlıkları (katsayılar) ve hesaplanan standart hataları (std_err) aşağıdaki gibidir:

### 1. Çoklu Doğrusal Regresyon
* **Katsayılar:** `A_1: -0.0458` | `A_2: -0.0715` | `A_3: 0.5065`
* **Standart Hatalar:** `Intercept: 30.8348` | `A_1: 0.2617` | `A_2: 0.3025` | `A_3: 0.2712`

### 2. Ridge Regresyon (L2)
* **Katsayılar:** `A_1: -0.0458` | `A_2: -0.0715` | `A_3: 0.5064`
* **Standart Hatalar:** `Intercept: 30.8348` | `A_1: 0.2617` | `A_2: 0.3025` | `A_3: 0.2712`

### 3. Lasso Regresyon (L1)
* **Katsayılar:** `A_1: -0.0458` | `A_2: -0.0713` | `A_3: 0.5062`
* **Standart Hatalar:** `Intercept: 30.8348` | `A_1: 0.2617` | `A_2: 0.3025` | `A_3: 0.2712`

### 4. ElasticNet Regresyon
* **Katsayılar:** `A_1: -0.0458` | `A_2: -0.0713` | `A_3: 0.5063`
* **Standart Hatalar:** `Intercept: 30.8348` | `A_1: 0.2617` | `A_2: 0.3025` | `A_3: 0.2712`

### 5. Bayesian Ridge Regresyon
* **Katsayılar:** `A_1: -0.0223` | `A_2: 0.0210` | `A_3: 0.1460`
* **Standart Hatalar:** `Intercept: 32.8519` | `A_1: 0.2788` | `A_2: 0.3223` | `A_3: 0.2889`

---

## Analiz Yorumu ve Değerlendirme

Modellerden elde edilen çıktılar incelendiğinde aşağıdaki istatistiksel sonuçlara ulaşılmıştır:

*   **Açıklayıcılık Gücü (R²):** Doğrusal, Ridge, Lasso ve ElasticNet modellerinin R-kare değeri yaklaşık **%22** seviyesinde sabit kalmıştır. Ancak Bayesian Ridge modelinde bu oran **%11.4'e** düşmüştür. Bu durum, veri setindeki gürültünün ve dışsal faktörlerin yüksekliğinin, Bayesian yaklaşımının aşırı muhafazakar davranmasına yol açtığını göstermektedir. Fiyat varyansının büyük bir kısmı (%78-88) iklim koşulları, arz/talep şokları veya enflasyon gibi veri setinde bulunmayan dışsal faktörlere bağlıdır.
*   **Katsayı Analizi (Feature Importance):** Bayesian Ridge dışındaki tüm modellerde en yüksek pozitif katsayı `A_3` (T dönemi / bir önceki dönem) değişkenine aittir (~0.506). `A_1` ve `A_2` değişkenlerinin katsayıları negatif ve sıfıra çok yakındır. Bu durum, fiyatı belirleyen en önemli unsurun *"en yakın geçmişteki fiyat"* olduğunu teyit etmektedir.
*   **Standart Hatalar ve Güvenilirlik:** Tüm modellerde katsayıların standart hataları (yaklaşık 0.26 - 0.32 arası), katsayı değerlerinin kendisine oranla oldukça yüksektir (özellikle A_1 ve A_2 için). Bu durum, A_1 ve A_2'nin istatistiksel olarak anlamsız (p-değeri yüksek) değişkenler olabileceğine işaret etmektedir.
*   **Düzenlileştirme (Regularization) Etkisi:** Ridge, Lasso ve ElasticNet algoritmalarının standart Doğrusal Regresyon ile neredeyse birebir aynı sonuçları vermesi, standart çoklu bağlantı (multicollinearity) veya aşırı öğrenme (overfitting) problemi olmadığını gösterir. Ancak Bayesian Ridge algoritmasının katsayıları ciddi şekilde sıfıra doğru baskılaması (A_3'ü 0.50'den 0.14'e çekmesi) ve performansı düşürmesi, modelin veri setindeki zayıf sinyalleri "gürültü" olarak yorumlayıp şiddetli bir düzeltme uyguladığını kanıtlamaktadır.
