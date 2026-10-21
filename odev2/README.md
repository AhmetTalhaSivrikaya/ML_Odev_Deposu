Oluşturulan veri seti üzerinden eğitilen 3 farklı regresyon modelinin test sonuçları, hata metrikleri ve denklem parametreleri aşağıda sunulmuştur.
Çoklu Doğrusal Regresyon (Multiple Linear Regression)
Performans Metrikleri:
R^2 Skoru: 0.2195
MSE: 604.3572
RMSE: 24.5837
MAE: 16.8495
Denklem Parametreleri(model.intercept_ & model.coef_):
model.intercept_: 49.0947
model.coef_: A_1: -0.0458 | A_2: -0.0715 | A_3: 0.5065
Standart Hatalar (std_err):
Intercept: 30.8348 | A_1: 0.2617 | A_2: 0.3025 | A_3: 0.27122. 
Ridge Regresyon (L2 Regularization)
Performans Metrikleri:
$R^2$ Skoru: 0.2195
MSE: 604.3572
RMSE: 24.5837
MAE: 16.8495
Denklem Parametreleri:
model.intercept_: 49.0969
model.coef_: A_1: -0.0458 | A_2: -0.0715 | A_3: 0.50643. 
Lasso Regresyon (L1 Regularization)Performans Metrikleri:
$R^2$ Skoru: 0.2195
MSE: 604.3572
RMSE: 24.5837
MAE: 16.8487
Denklem Parametreleri:
model.intercept_: 49.0893
model.coef_: A_1: -0.0458 | A_2: -0.0713 | A_3: 0.5062
Analiz Yorumu ve DeğerlendirmeModellerden elde edilen çıktılar incelendiğinde aşağıdaki istatistiksel sonuçlara ulaşılmıştır:
Açıklayıcılık Gücü ($R^2$): Modellerin R-kare değeri yaklaşık %22 seviyesindedir. 
Bu durum, gelecekteki erik fiyatlarının %22'sinin geçmiş fiyat hareketleriyle açıklanabildiğini göstermektedir. 
Geriye kalan %78'lik varyansın iklim koşulları, arz/talep şokları, enflasyon ve mevsimsellik gibi dışsal faktörlere bağlı olduğu değerlendirilmektedir.
Katsayı Analizi (model.coef_): Tüm modellerde en yüksek pozitif katsayı A_3 (T dönemi / bir önceki dönem) değişkenine aittir (~0.506). 
A_1 ve A_2 değişkenlerinin katsayıları negatif ve sıfıra çok yakın çıkmıştır. 
Bu durum, fiyatı belirleyen en önemli unsurun "en yakın geçmişteki fiyat" olduğunu, uzak geçmişin fiyat üzerinde anlamlı bir ağırlığı olmadığını kanıtlamaktadır.
Düzenlileştirme Etkisi: Ridge ve Lasso algoritmalarının, standart Doğrusal Regresyon ile neredeyse birebir aynı R² ve hata (RMSE) oranlarını vermesi, elimizdeki özellikler (A_1, A_2, A_3) arasında modeli bozacak düzeyde şiddetli bir çoklu bağlantı (multicollinearity) veya aşırı öğrenme (overfitting) problemi olmadığını göstermektedir.
