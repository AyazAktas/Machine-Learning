Türev, integral ve zincir kuralı denince kulağa hemen ağır matematik gibi geliyor ama aslında günlük hayatta hepimizin yaşadığı şeylerin sayısal ifadesinden ibaret. Bunları anladığında Gradient Descent gibi “makine öğrenmesinin kalbi” olan algoritmaların nasıl çalıştığını da kavramak kolaylaşacak. Hadi adım adım gidelim.

---

## 🎯 Türev (Derivative)

Türev, bir şeyin anlık değişim hızını ölçer.

🔹 **Tanım (matematiksel):**
Bir fonksiyonun belli bir noktadaki eğimidir.

$$
f'(x) = \lim_{h \to 0} \frac{f(x+h)-f(x)}{h}
$$

🔹 **Günlük hayat örneği:**
Araba sürüyorsun, hız göstergesinde 90 km/s yazıyor. Bu aslında türevdir. Çünkü türev, “konumun zamana göre değişim hızı”dır → yani hız.

🔹 **Makine öğrenmesinde yeri:**

* Bir modelin hata fonksiyonunu düşün (loss function). Bizim amacımız bu hatayı küçültmek. Hata fonksiyonunun türevi bize “şu an bu noktada hata hangi yöne doğru azalıyor?” sorusunun cevabını verir.
* Yani türev = “hata fonksiyonunun eğimi → hangi yönde adım atmalıyım?”

---

## 🎯 Zincir Kuralı (Chain Rule)

Bazen fonksiyonlar iç içe geçmiş olur. O zaman türev almak için zincir kuralına ihtiyaç duyarız.

🔹 **Matematiksel ifade:**
Eğer $y = f(g(x))$ ise:

$$
\frac{dy}{dx} = f'(g(x)) \cdot g'(x)
$$

🔹 **Günlük hayat örneği:**
Diyelim ki ben sana her gün kahve ısmarlıyorum. Kahve içmek → seni enerjik yapıyor. Enerjik olman → sınav notunu yükseltiyor.

* Kahve miktarı → enerji (1. ilişki)
* Enerji → sınav notu (2. ilişki)

Sen “kahve miktarı sınav notunu nasıl etkiler?” diye sorarsan bu iki etkiyi zincir kuralıyla çarparız.

🔹 **Makine öğrenmesinde yeri:**

* Sinir ağlarında ileri doğru işlemde aktivasyonlar iç içe fonksiyonlardır.
* Geriye yayılım (backpropagation) tamamen zincir kuralı ile türevleri hesaplayıp hatayı katman katman geriye yaymaktan ibarettir.

---

## 🎯 İntegral (Integral)

İntegral, türevin tersidir. Küçük parçaları toplayıp büyük resmi görmeyi sağlar.

🔹 **Tanım (matematiksel):**
Bir fonksiyonun altındaki alan.

$$
\int f(x) dx
$$

🔹 **Günlük hayat örneği:**
Hız göstergesinden anlık hızları biliyorsun. Ama “ben toplamda kaç kilometre yol yaptım?” dersen işte integral devreye girer. Hızı (küçük parçalar halinde) toplarsın → toplam yol çıkar.

🔹 **Makine öğrenmesinde yeri:**

* Olasılık dağılımlarında “bu aralıkta değer alma ihtimali nedir?” sorusu integralle hesaplanır.
* Continuous (sürekli) modellerde alan hesaplamak integrale bağlıdır.

---

## 🎯 Gradient Descent ile Bağlantı

Gradient Descent (Gradyan İnişi) → en temel optimizasyon yöntemi.

🔹 **Mantık:**
Bir dağın tepesindesin ve gözlerin kapalı. Amacın en kısa yoldan aşağı inmek. Elinle yokluyorsun, eğimin en fazla hangi yönde olduğunu hissediyorsun, o yöne küçük bir adım atıyorsun. Sonra tekrar bakıyor, tekrar adım atıyorsun. İşte Gradient Descent bu.

Formül:

$$
\theta_{new} = \theta_{old} - \alpha \cdot \nabla J(\theta)
$$

* $\theta$: model parametreleri
* $J(\theta)$: hata fonksiyonu (loss)
* $\nabla J(\theta)$: gradyan (türevlerle hesaplanan eğim)
* $\alpha$: öğrenme oranı (learning rate)

🔹 **Bağlantılar:**

* **Türev** → Eğim bilgisini verir, hangi yönde gitmeliyim?
* **Zincir kuralı** → Derin ağlarda bu türevleri katman katman hesaplamamı sağlar.
* **İntegral** → Dağılımlar ve alan hesaplamalarında destekleyici ama Gradient Descent’te doğrudan değil, yan rol oynar.

---

### 🔑 Özet

* Türev = anlık değişim hızı → yön bulma.
* Zincir kuralı = iç içe fonksiyonların türevini çözme → backpropagation.
* İntegral = küçük parçaları toplama → olasılık alanı.
* Gradient Descent = türevlerin verdiği eğimi takip ederek hatayı adım adım azaltma.

---
