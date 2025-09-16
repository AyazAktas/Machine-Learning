İstatistik ve olasılık, makine öğrenmesinin belki de en kritik temellerinden biri. Çünkü her model, bir şekilde belirsizliği anlamaya ve verideki örüntüleri sayılarla özetlemeye çalışıyor.

---

## 🎯 Ortalama (Mean)

Ortalama, bir veri grubunun “merkezini” bulmaya çalıştığımız ölçüdür.

🔹 **Matematiksel tanım:**

$$
\mu = \frac{1}{n} \sum_{i=1}^{n} x_i
$$

Yani bütün değerleri topla, eleman sayısına böl.

🔹 **Günlük hayat örneği:**
Sınıfta 5 kişinin boyu olsun: 160, 170, 165, 180, 175. Bu beş boyu topladığında 850 çıkar, 5’e bölersin, ortalama boy 170 cm olur. İşte bu sınıfın genel “merkezi yüksekliği”.

🔹 **Makine öğrenmesinde yeri:**

* Naive Bayes gibi olasılık modellerinde sınıfın dağılım merkezi ortalama ile temsil edilir.
* K-Means kümeleme, kümelerin merkezini ortalama alarak bulur.

---

## 🎯 Varyans (Variance)

Ortalama bize “merkezi” söyler, varyans ise verinin o merkezin etrafında ne kadar dağınık olduğunu.

🔹 **Matematiksel tanım:**

$$
\sigma^2 = \frac{1}{n} \sum_{i=1}^{n} (x_i - \mu)^2
$$

Her değerin ortalamadan farkının karesini alırız, sonra ortalamasını buluruz.

🔹 **Günlük hayat örneği:**
İki sınıfı düşün:

* A sınıfında herkes 170 cm civarında.
* B sınıfında bazıları 150 cm, bazıları 190 cm.

İki sınıfın ortalaması aynı olabilir (170 cm), ama dağılım farklıdır. İşte varyans bunu yakalar.

🔹 **Makine öğrenmesinde yeri:**

* Regresyon modellerinde hataların varyansını azaltmak hedeflenir.
* PCA (boyut indirgeme) en yüksek varyansı açıklayan yönleri bulur.

---

## 🎯 Kovaryans (Covariance)

Varyans, tek bir değişkenin ne kadar dağıldığını söyler. Kovaryans, **iki değişkenin birlikte nasıl hareket ettiğini** söyler.

🔹 **Matematiksel tanım:**

$$
cov(X, Y) = \frac{1}{n} \sum_{i=1}^{n} (x_i - \bar{x})(y_i - \bar{y})
$$

🔹 **Yorum:**

* Eğer pozitif → X artarken Y de artma eğiliminde.
* Eğer negatif → X artarken Y azalma eğiliminde.
* Eğer sıfır → aralarında doğrusal ilişki yok.

🔹 **Günlük hayat örneği:**
Sıcaklık ile dondurma satışı → sıcaklık arttıkça dondurma satışı artar (pozitif kovaryans).
Sıcaklık ile kaban satışı → sıcaklık arttıkça kaban satışı düşer (negatif kovaryans).

🔹 **Makine öğrenmesinde yeri:**

* PCA kovaryans matrisini kullanarak hangi yönlerin en fazla varyansı açıkladığını bulur.
* Özellikler arasındaki ilişkiyi incelemek için kovaryans çok önemlidir.

---

## 🎯 Olasılık Dağılımları

Şimdi işin en heyecanlı kısmına geliyoruz. Dağılımlar, belirsizliğin haritasıdır. Bir değişkenin hangi değerleri alma ihtimali olduğunu bize söyler.

---

### 1. Normal Dağılım (Gauss Dağılımı)

🔹 **Tanım:**
Simetrik, çan eğrisi şeklindeki dağılım. Çoğu doğal olay buna uyar (insan boyu, sınav notları, ölçüm hataları).

Formülü:

$$
f(x) = \frac{1}{\sqrt{2 \pi \sigma^2}} e^{ -\frac{(x - \mu)^2}{2\sigma^2} }
$$

🔹 **Özellikleri:**

* Ortalama = medyan = mod.
* %68 değer ortalamanın 1 standart sapma içinde, %95’i 2 standart sapma içinde.

🔹 **Günlük hayat örneği:**
Bir üniversite sınavında herkes 50–60 civarı alıyor, çok yüksek ve çok düşük alan az.

🔹 **ML’de kullanımı:**

* Linear Regression hata terimlerinin normal dağılması varsayılır.
* Gaussian Naive Bayes sınıflandırmada temel varsayımdır.

---

### 2. Bernoulli Dağılımı

🔹 **Tanım:**
Tek denemede sadece iki sonuç (başarı/başarısızlık, evet/hayır, 0/1).

Formülü:

$$
P(X=1) = p, \quad P(X=0) = 1-p
$$

🔹 **Günlük hayat örneği:**
Yazı tura atışı: “yazı” gelme olasılığı p, “tura” gelme olasılığı 1-p.

🔹 **ML’de kullanımı:**

* Lojistik regresyon çıktısı aslında Bernoulli dağılımı ile yorumlanır.
* İkili sınıflandırma problemlerinde temel yapı taşıdır.

---

### 3. Binomial Dağılım

🔹 **Tanım:**
Birden fazla Bernoulli denemesinin toplamı. Yani “n kez yazı-tura attığında kaç defa yazı gelir?” sorusunun cevabı.

Formülü:

$$
P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}
$$

🔹 **Günlük hayat örneği:**
10 kez basket atışında 6’sını sokma ihtimali.

🔹 **ML’de kullanımı:**

* Model doğruluğunu test ederken başarı sayılarının dağılımı binomiyale göre hesaplanır.

---

### 4. Poisson Dağılımı

🔹 **Tanım:**
Belli bir zaman aralığında nadir olayların sayısını modelleyen dağılım.

Formülü:

$$
P(X=k) = \frac{\lambda^k e^{-\lambda}}{k!}
$$

Burada $\lambda$, beklenen ortalama olay sayısıdır.

🔹 **Günlük hayat örneği:**

* 1 saatte gelen müşteri sayısı.
* Bir yıl içinde meydana gelen deprem sayısı.

🔹 **ML’de kullanımı:**

* NLP’de kelime frekanslarını modellemek.
* Queue (kuyruk) sistemlerinde olayları anlamak.

---

### 5. Exponential Dağılım

🔹 **Tanım:**
Poisson olayları arasındaki süreyi modelleyen dağılım.

Formülü:

$$
f(x;\lambda) = \lambda e^{-\lambda x}
$$

🔹 **Günlük hayat örneği:**
Otobüs durağında beklerken otobüsün gelme süresi, bir radyum atomunun ne kadar sürede parçalanacağı.

🔹 **ML’de kullanımı:**

* Survival analysis (sağkalım analizi).
* Sistemlerin arıza süresini modellemek.

---

## 🎙️ Özet

* Ortalama → verinin merkezi.
* Varyans → verinin yayılımı.
* Kovaryans → iki değişkenin birlikte hareketi.
* Normal dağılım → doğadaki çoğu şeyin şekli.
* Bernoulli → tek atışlık olaylar.
* Binomial → birden çok Bernoulli.
* Poisson → belirli zaman aralığında olay sayısı.
* Exponential → olaylar arasındaki süre.

Makine öğrenmesinde modellerin çoğu, bu dağılımlar üzerine kuruludur. Aslında algoritmaların arka planına baktığında hep bu istatistiksel varsayımları görürsün.

---

