Lineer cebir, makine öğrenmesinin omurgasıdır. Çoğu zaman modelin içinde gördüğümüz karmaşık işlemler, aslında satır satır lineer cebir operasyonlarına dönüşür. Şimdi bunları ele alalım; kavramları tek tek açalım, günlük hayattan örneklerle bağlayalım ve neden makine öğrenmesinde bu kadar kritik olduklarını görelim.

---

## 🎯 Vektör

Vektör, bir sayı listesidir ama sadece liste demek yetmez; bu listenin **büyüklüğü** ve **yönü** vardır.

🔹 **Matematiksel tanım:**
Bir vektör, $\mathbb{R}^n$ uzayında tanımlanmış, $n$ boyutlu bir sayı dizisidir.
Örn: $v = [2, 5, -1]$ üç boyutlu bir vektördür.

🔹 **Günlük hayat örneği:**
Market arabasını düşün. Arabayı **3 Newton** kuvvetle ileri doğru, **2 Newton** sağa doğru itiyorsun. Bu iki sayı (3 ve 2) bir araya geldiğinde senin “hareket ettirme vektörün” oluşuyor. Yani vektör, sadece “kaç” değil, aynı zamanda “nereye” sorusunun da cevabıdır.

🔹 **Makine öğrenmesinde yeri:**
Her veri noktasını bilgisayar aslında bir vektör olarak görür.

* Bir evin fiyatını tahmin etmek istersek, evin metrekaresi, oda sayısı, şehir merkezi uzaklığı… hepsi birer sayı. Bunları \[120, 3, 5] gibi vektör haline getiririz.
* Görsel işleme yaparken her pikselin RGB değeri de bir vektördür.

---

## 🎯 Matris

Matris, vektörlerin tablosu gibi düşünülebilir.

🔹 **Matematiksel tanım:**
Dikdörtgen biçiminde düzenlenmiş sayı tablosudur. Örn:

$$
A = \begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6
\end{bmatrix}
$$

🔹 **Günlük hayat örneği:**
Bir okulun not defterini düşün. Satırlar öğrencileri, sütunlar dersleri temsil etsin. Her hücreye öğrencinin aldığı not yazılır. Bu tablo aslında bir matristir.

🔹 **Makine öğrenmesinde yeri:**

* Veriler genellikle $n \times m$ boyutlu bir matriste saklanır. (n: örnek sayısı, m: özellik sayısı)
* Bir sinir ağında girişten çıkışa olan dönüşümler hep matris çarpımlarıyla yapılır.

---

## 🎯 Determinant

Determinant, matrisin bize verdiği “ölçek faktörü”dür.

🔹 **Matematiksel tanım:**
Bir kare matrisin determinantı, o matrisin alanı/hacmi ne kadar büyütüp küçülttüğünü gösterir.

🔹 **Günlük hayat örneği:**
Bir haritayı büyütüp küçülten fotokopi makinesini düşün. Eğer fotokopi %200 büyütüyorsa, senin kare kağıdın artık 2 kat daha büyük olur. Determinant bu büyütme katsayısını söyler. Eğer determinant 0 çıkarsa, bu şu anlama gelir: matris uzayı bir boyut “çökerterek” sıkıştırıyor (yani bilgiyi kaybediyor).

🔹 **Makine öğrenmesinde yeri:**

* Matrisin tersinin var olup olmadığını anlamak için determinant kontrol edilir.
* Bazı algoritmalarda (örneğin Gaussian dağılımlarında kovaryans matrisinin determinantı) doğrudan hesaplara girer.

---

## 🎯 Eigenvalue (özdeğer) ve Eigenvector (özvektör)

Bunlar lineer cebirin en büyülü kavramlarındandır.

🔹 **Tanım:**

* Bir matrisi vektörle çarptığında, genelde yön değişir. Ama bazı özel vektörler vardır ki, yönleri değişmez; sadece uzunlukları farklılaşır. İşte bu özel vektörler **özvektör**, uzunluklarını ne kadar değiştirdiğini söyleyen katsayı da **özdeğer**dir.

🔹 **Günlük hayat örneği:**
Bir şirketin işleyişini düşün. Şirket her sene yeniden yapılanıyor, ama bazı departmanlar (mesela muhasebe) aynı düzeniyle kalıyor; sadece çalışan sayısı artıyor veya azalıyor. Bu değişmeyen “yön” → özvektör, değişim katsayısı → özdeğer.

🔹 **Makine öğrenmesinde yeri:**

* PCA (Principal Component Analysis) → boyut indirgeme yönteminde, veri dağılımındaki en güçlü yönleri bulmak için özvektör/özdeğerler kullanılır.
* Grafiklerde en baskın yönü, varyansı açıklayan eksenleri çıkarır.

---

## 🎯 SVD (Singular Value Decomposition)

SVD, veriyi üç parçaya ayıran güçlü bir faktörizasyon tekniğidir.

🔹 **Tanım:**
Her matrisi üç matrisin çarpımı olarak yazabiliriz:

$$
A = U \Sigma V^T
$$

* $U$: Satır yönlerini temsil eder.
* $\Sigma$: Tekil değerler (en önemli bilgiler burada).
* $V^T$: Sütun yönlerini temsil eder.

🔹 **Günlük hayat örneği:**
Bir müziği düşün. Müziği üçe ayırabilirsin: vokal, ritim, enstrüman. Bunlar birleşince orijinal müzik ortaya çıkar. SVD de bir matrisi bu bileşenlerine ayırır.

🔹 **Makine öğrenmesinde yeri:**

* PCA aslında SVD’nin özel bir kullanımıdır.
* Öneri sistemlerinde (Netflix, Spotify) kullanıcı–film matrisini faktörleyip gizli özellikleri çıkarırız.
* Gürültü azaltma ve sıkıştırmada da çok kullanılır.

---

### 🔑 Özet

* **Vektör** → özelliklerimizi temsil eden sayı dizileri.
* **Matris** → verilerin tablolaşmış hali.
* **Determinant** → matrisin ölçekleme gücü.
* **Eigenvalue/Eigenvector** → verideki en baskın yönleri keşfetmek.
* **SVD** → matrisleri parçalayarak gizli yapıları ortaya çıkarmak.

Makine öğrenmesinde bu kavramlar olmadan ilerlemek mümkün değil. Çünkü algoritmaların içini açtığımızda gördüğümüz şey, aslında hep bu yapı taşlarının matematiksel dansı.

---
