Algoritmalar & karmaşıklık kısmı, makine öğrenmesi yolculuğunda matematik kadar kritik bir alan. Çünkü algoritmaların nasıl çalıştığını, ne kadar hızlı olduklarını ve hangi veri yapılarıyla desteklendiklerini bilmezsek, çok iyi modeller kursak bile gerçek dünyada çuvallarız. Şimdi uzun, detaylı ve günlük hayatla bağlantılı bir şekilde anlatacağım.

---

# 🎯 Algoritmalar & Karmaşıklık

## 1. Algoritma nedir?

Algoritma, aslında bir “yemek tarifi”dir. Yani belirli bir problemin çözümü için **adım adım verilen talimatlar**.

🔹 **Günlük hayat örneği:**
Sabah çay demlemek istiyorsun:

1. Suyu kaynat.
2. Demliği hazırla.
3. Çayı koy.
4. Suyu ekle.
5. Demlenmesini bekle.

Bu 5 adım → çay demleme algoritmasıdır.

🔹 **Bilgisayar bağlamı:**
Bir listeyi küçükten büyüğe sıralamak, bir kelimeyi aramak, en kısa yolu bulmak… bunların her biri için bir algoritma vardır.

---

## 2. Neden algoritmalar önemli?

Makine öğrenmesinde her şey veriyle ilgili. Veri milyonlarca satıra çıkınca, “hangi yöntem daha hızlı çalışır?” sorusu kritik hale gelir.

Örneğin:

* Elinde 1.000 sayı var → Bubble Sort (yavaş algoritma) belki işini görür.
* Ama 10 milyon sayı varsa → QuickSort veya MergeSort gibi daha verimli algoritmalar kullanmak zorundasın.

Yani **algoritmaların verimliliğini** ölçmek için bir sistem gerekir. İşte burada **Big-O Notation** devreye girer.

---

## 3. Big-O Notation (Büyük O Gösterimi)

Big-O, algoritmanın **zaman ve hafıza karmaşıklığını** anlatır. “Bu algoritma kaç saniyede biter?” yerine, “veri büyüdükçe bu algoritma nasıl ölçeklenir?” sorusuna cevap verir.

### 3.1. Mantık

* Küçük veri → her algoritma hızlıdır.
* Büyük veri → sadece iyi algoritmalar ayakta kalır.

Big-O, en kötü durumu (worst case) ifade eder.

### 3.2. Yaygın karmaşıklık sınıfları

1. **O(1) – Sabit zaman**
   Algoritma, veri boyutu artsa bile hep aynı sürede çalışır.
   🔹 Örnek: Bir dizideki ilk elemana erişmek.

2. **O(log n) – Logaritmik zaman**
   Veri büyüdükçe adım sayısı logaritmik artar.
   🔹 Örnek: İkili arama (binary search). 1.000.000 elemanda sadece \~20 adımda sonuç bulur.

3. **O(n) – Doğrusal zaman**
   Her elemanı kontrol etmek gerekir.
   🔹 Örnek: Bir listeyi baştan sona dolaşmak.

4. **O(n log n) – Karma zaman**
   Veriyi parçalara ayırıp her parçayı işleyen algoritmalar.
   🔹 Örnek: MergeSort, QuickSort.

5. **O(n²) – Kare zaman**
   İç içe döngüler varsa ortaya çıkar.
   🔹 Örnek: Bubble Sort, Selection Sort.

6. **O(2^n) – Üstel zaman**
   Her ek veri, işlem süresini ikiye katlar.
   🔹 Örnek: Gezgin satıcı (TSP), brute-force kombinasyon arama.

7. **O(n!) – Faktöriyel zaman**
   En hızlı büyüyen tür. Çok kısa sürede imkansız hale gelir.
   🔹 Örnek: Tüm olası sıralamaları denemek.

---

### 3.3. Günlük hayat benzetmesi

* **O(1):** Bir otoparkta senin özel park yerin var → direkt girersin.
* **O(log n):** Bir telefon rehberinde arama → ortadan başla, yarıya indir.
* **O(n):** Her arabayı tek tek kontrol et, seninki hangisi?
* **O(n²):** Her arabanın yanına git, her kapıyı tek tek açmayı dene.
* **O(2^n):** Tüm kombinasyonları dene → araba + şoför + saat vs.

---

## 4. Temel Veri Yapıları

Veri yapıları, algoritmaların üzerinde koştuğu “zemindir”. İyi bir algoritma bile yanlış veri yapısıyla birleşirse yavaş çalışır.

### 4.1. Dizi (Array)

* **Tanım:** Bellekte ardışık elemanlardan oluşur.
* **Avantaj:** İndeksle hızlı erişim (O(1)).
* **Dezavantaj:** Ortaya eleman eklemek/silmek pahalıdır (O(n)).

🔹 **Örnek:** Öğrencilerin numaralarının listesi.

---

### 4.2. Bağlı Liste (Linked List)

* **Tanım:** Her eleman, bir sonrakini işaret eder.
* **Avantaj:** Eleman ekleme/silme hızlıdır.
* **Dezavantaj:** Ortadaki elemana erişim yavaştır (O(n)).

🔹 **Örnek:** Metro vagonları birbirine zincirle bağlıdır. Ortadakine ulaşmak için baştan yürürsün.

---

### 4.3. Yığın (Stack)

* **Tanım:** LIFO (Last In, First Out) → en son giren, ilk çıkar.
* **Örnek:** Tabak yığını. En üstteki tabağı alırsın.

🔹 **Algoritmalarda:** Fonksiyon çağrıları, undo işlemleri.

---

### 4.4. Kuyruk (Queue)

* **Tanım:** FIFO (First In, First Out) → ilk giren, ilk çıkar.
* **Örnek:** Banka sırası. İlk gelen müşteri önce hizmet alır.

🔹 **Algoritmalarda:** İşlemci görev sırası, BFS (Breadth-First Search).

---

### 4.5. Ağaç (Tree)

* **Tanım:** Hiyerarşik yapı. Her düğümün çocukları olabilir.
* **Örnek:** Aile soy ağacı.

🔹 **Algoritmalarda:**

* İkili arama ağacı → hızlı arama (O(log n)).
* Karar ağaçları → ML’de sınıflandırma.

---

### 4.6. Grafik (Graph)

* **Tanım:** Düğümler ve onları bağlayan kenarlardan oluşur.
* **Örnek:** Facebook arkadaşlık ilişkileri.

🔹 **Algoritmalarda:**

* En kısa yol (Dijkstra).
* Ağ analizi (GNN – Graph Neural Networks).

---

### 4.7. Hash Tablosu

* **Tanım:** Anahtar–değer eşleşmeleri.
* **Avantaj:** Ortalama O(1) erişim.
* **Örnek:** Kimlik numarası → isim.

🔹 **Algoritmalarda:**

* Veri tabanları.
* Neredeyse tüm modern ML framework’lerinde özellik–değer eşleşmeleri.

---

## 5. Makine Öğrenmesi ile Bağlantı

* **Big-O** → Veri arttığında hangi model/algoritma daha verimli çalışır? (ör: KNN O(n) olduğu için büyük veride sorun çıkarır.)
* **Veri yapıları** → Verilerin saklanması ve işlenmesi için kritik. Örn: ağaç yapıları → karar ağaçları, hash tabloları → NLP’de kelime sözlükleri.
* **Algoritmalar** → ML’nin temelinde aslında klasik bilgisayar bilimleri algoritmaları vardır. Örn: Gradient Boosting = birden fazla karar ağacı + optimizasyon.

---

