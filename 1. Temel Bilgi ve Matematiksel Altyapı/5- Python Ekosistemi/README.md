NumPy, Python’daki bilimsel hesaplamaların kalbi. Makine öğrenmesinde kullandığımız tüm framework’ler (Pandas, Scikit-Learn, TensorFlow, PyTorch) arka planda hep NumPy dizileri üzerinde çalışıyor. O yüzden NumPy’ı çok sağlam öğrenmek, seni doğrudan ML’de hızlandırır. Şimdi en temelden başlayıp ileri seviyeye kadar **özelliklerini, fonksiyonlarını, kullanım senaryolarını ve kod örneklerini** tek tek anlatacağım.

---

# 🔹 NumPy Nedir?

NumPy = **Numerical Python**.

* Çok boyutlu diziler (**ndarray**) oluşturmak için en hızlı kütüphane.
* C/C++ ile yazıldığı için **saf Python listelerinden onlarca kat hızlı**.
* Vektörizasyon (toplama, çıkarma, çarpma işlemlerini tüm diziye aynı anda uygulama) sağlar.
* ML’de “veriyi matris/vektör gibi saklama ve işleme” işini yapar.

---

# 🔹 1. NumPy Dizileri (ndarray)

## Dizi Oluşturma

```python
import numpy as np

# Listeyi numpy array'e çevirme
arr = np.array([1, 2, 3, 4])
print(arr)   # [1 2 3 4]

# 2D array
arr2d = np.array([[1, 2], [3, 4]])
print(arr2d)
```

## Hazır Fonksiyonlarla Oluşturma

```python
np.zeros((2,3))      # 2x3 sıfırlardan oluşan matris
np.ones((3,3))       # 3x3 birlerden oluşan matris
np.full((2,2), 7)    # 7 ile doldurulmuş 2x2 matris
np.eye(3)            # 3x3 birim matris
np.arange(0,10,2)    # [0 2 4 6 8]
np.linspace(0,1,5)   # [0.  0.25  0.5  0.75  1.]
```

## Rasgele Diziler

```python
np.random.rand(2,3)       # 0-1 arası rastgele sayılar
np.random.randn(2,3)      # Normal dağılımdan (Gaussian)
np.random.randint(1,10,(3,3)) # 1-10 arası rastgele tam sayılar
```

---

# 🔹 2. Dizi Özellikleri

```python
arr = np.array([[1,2,3],[4,5,6]])

print(arr.shape)   # (2,3) → 2 satır 3 sütun
print(arr.ndim)    # 2 → boyut sayısı
print(arr.size)    # 6 → toplam eleman sayısı
print(arr.dtype)   # int64 (veya float64)
```

---

# 🔹 3. İndeksleme & Dilimleme

## Tek Boyutlu

```python
arr = np.array([10, 20, 30, 40])
print(arr[0])      # 10
print(arr[-1])     # 40
print(arr[1:3])    # [20 30]
```

## Çok Boyutlu

```python
arr = np.array([[1,2,3],[4,5,6],[7,8,9]])
print(arr[0,1])     # 1. satır, 2. sütun → 2
print(arr[:,1])     # 2. sütun → [2 5 8]
print(arr[1,:])     # 2. satır → [4 5 6]
```

## Mantıksal İndeksleme

```python
arr = np.array([1,2,3,4,5])
print(arr[arr > 3])    # [4 5]
```

---

# 🔹 4. Vektörize İşlemler

NumPy’ın en güçlü yanı → Döngü yazmadan tüm diziye işlem yapabilirsin.

```python
a = np.array([1,2,3])
b = np.array([4,5,6])

print(a + b)     # [5 7 9]
print(a * b)     # [ 4 10 18]
print(a ** 2)    # [1 4 9]
print(np.sqrt(a))# [1. 1.414 1.732]
```

**Not:** Python listeleriyle yapmaya kalksan tek tek dolaşman gerekir, NumPy bunu tek satırda yapar.

---

# 🔹 5. İstatistiksel Fonksiyonlar

```python
arr = np.array([1,2,3,4,5])

print(np.mean(arr))    # 3.0 → ortalama
print(np.median(arr))  # 3.0 → medyan
print(np.std(arr))     # 1.414 → standart sapma
print(np.var(arr))     # 2.0 → varyans
print(np.min(arr))     # 1
print(np.max(arr))     # 5
print(np.sum(arr))     # 15
```

Çok boyutlu dizilerde:

```python
mat = np.array([[1,2,3],[4,5,6]])
print(np.mean(mat, axis=0)) # [2.5 3.5 4.5] → sütun ort.
print(np.mean(mat, axis=1)) # [2. 5.]       → satır ort.
```

---

# 🔹 6. Lineer Cebir Fonksiyonları

NumPy, lineer cebirin yapı taşıdır.

```python
A = np.array([[1,2],[3,4]])
B = np.array([[5,6],[7,8]])

# Matris çarpımı
print(np.dot(A,B))  
print(A @ B)         # aynı şey

# Transpoz
print(A.T)

# Determinant
print(np.linalg.det(A))

# Ters matris
print(np.linalg.inv(A))

# Eigenvalue & Eigenvector
vals, vecs = np.linalg.eig(A)
print(vals)  # özdeğerler
print(vecs)  # özvektörler

# Singular Value Decomposition (SVD)
U, S, Vt = np.linalg.svd(A)
print(S)
```

---

# 🔹 7. Faydalı Fonksiyonlar

```python
arr = np.array([1,2,3,4,5])

print(np.unique(arr))          # Tekrar edenleri sil
print(np.sort(arr))            # Sıralama
print(np.argsort(arr))         # Sıralama indexleri
print(np.argmax(arr))          # Maks. elemanın indexi
print(np.argmin(arr))          # Min. elemanın indexi
```

---

# 🔹 8. Broadcast (Yayınlama)

NumPy diziler farklı boyutta olsa bile işlemleri akıllıca yapabilir.

```python
a = np.array([[1,2,3],[4,5,6]])
b = np.array([10,20,30])

print(a + b)
# [[11 22 33]
#  [14 25 36]]
```

Burada 1x3 dizi, 2x3 matrise otomatik olarak “yayınlandı” ve toplama yapıldı.

---

# 🔹 9. Maskeleme ve Koşullu İşlemler

```python
arr = np.array([10,20,30,40,50])

# Şartlı seçim
print(arr[arr > 25])   # [30 40 50]

# Şartlı değiştirme
arr[arr > 25] = 99
print(arr)   # [10 20 99 99 99]
```

---

# 🔹 10. NumPy ile Rastgelelik (random)

```python
np.random.seed(42)   # Tekrar üretilebilirlik için
print(np.random.rand(3))         # [0.37 0.95 0.73]
print(np.random.randint(1,10,5)) # [7 4 8 5 7]

# Normal dağılımdan 1000 sayı
data = np.random.randn(1000)
print(np.mean(data), np.std(data))
```

---

# 🔹 11. NumPy ile Dosya İşlemleri

```python
arr = np.array([[1,2,3],[4,5,6]])

# Kaydetme
np.save("my_array.npy", arr)

# Yükleme
loaded = np.load("my_array.npy")
print(loaded)

# TXT / CSV
np.savetxt("data.csv", arr, delimiter=",")
print(np.loadtxt("data.csv", delimiter=","))
```

---

# 🔹 12. Gerçek Dünya Kullanımı

* **ML modellerinde veri hazırlama**: Pandas arka planda NumPy kullanır.
* **Görüntü işleme**: Bir resim, aslında $H \times W \times 3$ boyutlu NumPy dizisidir.
* **Matematik**: PCA, SVD, lineer regresyon, hepsi NumPy fonksiyonlarıyla yapılabilir.
* **NLP**: Kelime vektörleri NumPy array’leri şeklinde tutulur.

---

# 📝 Özet

* NumPy diziler → Python listelerinden çok daha hızlı ve güçlü.
* Matris, vektör, lineer cebir, istatistik işlemleri → tek satırda yapılabiliyor.
* ML’de veri temsilinin *standart dili* NumPy’dır.

---

Pandas, veri analizi dünyasında NumPy’ın üstüne kurulan en güçlü araçlardan biri. Eğer NumPy “matematiksel motor” ise, Pandas da “kullanıcı dostu kokpit” diyebiliriz. Çünkü veriyi tablo halinde düzenler, sütunlara isimler verir, eksik değerlerle uğraşmamızı kolaylaştırır. Şimdi adım adım, **özellikleri + fonksiyonları + kod örnekleri** ile derinlemesine anlatacağım.

---

# 🔹 Pandas Nedir?

* Python’da **veri manipülasyonu ve analiz** için kullanılan kütüphane.
* NumPy dizilerini **DataFrame** (tablo) ve **Series** (tek sütun) yapılarıyla daha okunabilir hale getirir.
* Excel, CSV, SQL gibi kaynaklardan veri okumayı/yazmayı kolaylaştırır.
* ML projelerinde veri ön işleme aşamasının %70’i Pandas ile yapılır.

---

# 🔹 1. Temel Veri Yapıları

## Series

Tek boyutlu etiketli dizi.

```python
import pandas as pd

s = pd.Series([10, 20, 30, 40], index=['a','b','c','d'])
print(s)
# a    10
# b    20
# c    30
# d    40
```

Erişim:

```python
print(s['b'])     # 20
print(s[1])       # 20
```

## DataFrame

İki boyutlu tablo, en çok kullanılan yapı.

```python
data = {
    "isim": ["Ayşe", "Mehmet", "Ali"],
    "yaş": [25, 30, 22],
    "şehir": ["Ankara", "İstanbul", "İzmir"]
}

df = pd.DataFrame(data)
print(df)
```

```
     isim  yaş    şehir
0    Ayşe   25   Ankara
1  Mehmet   30 İstanbul
2     Ali   22    İzmir
```

---

# 🔹 2. Veri Okuma & Yazma

```python
# CSV dosyası
df = pd.read_csv("veri.csv")

# Excel
df = pd.read_excel("veri.xlsx")

# SQL
# df = pd.read_sql(query, connection)

# Kaydetme
df.to_csv("out.csv", index=False)
df.to_excel("out.xlsx", index=False)
```

---

# 🔹 3. Temel Bilgiler

```python
print(df.head())       # İlk 5 satır
print(df.tail(3))      # Son 3 satır
print(df.info())       # Tip, null sayısı
print(df.describe())   # İstatistik özet
print(df.shape)        # (satır, sütun)
print(df.columns)      # Sütun isimleri
print(df.index)        # Satır indexleri
```

---

# 🔹 4. Sütun ve Satırlara Erişim

```python
# Tek sütun
print(df["isim"])

# Birden fazla sütun
print(df[["isim","şehir"]])

# Satır seçme (iloc = index, loc = label)
print(df.iloc[0])         # İlk satır
print(df.loc[1])          # Index = 1 olan satır
```

---

# 🔹 5. Filtreleme ve Koşullar

```python
# Yaşı 25'ten büyük olanlar
print(df[df["yaş"] > 25])

# Şehri Ankara olanlar
print(df[df["şehir"] == "Ankara"])

# Koşul birleştirme
print(df[(df["yaş"] > 20) & (df["şehir"] == "İzmir")])
```

---

# 🔹 6. Veri Temizleme

## Eksik Değerler

```python
df.isnull().sum()          # Hangi sütunda kaç tane NaN
df.dropna(inplace=True)    # Eksik satırları sil
df.fillna(0, inplace=True) # NaN yerine 0 yaz
```

## Sütun İsimlerini Düzenleme

```python
df.rename(columns={"isim":"ad"}, inplace=True)
```

## Veri Tipi Dönüştürme

```python
df["yaş"] = df["yaş"].astype(float)
```

---

# 🔹 7. Yeni Sütunlar & Dönüşümler

```python
# Yeni sütun ekleme
df["yaş_2kat"] = df["yaş"] * 2

# Apply fonksiyonu
df["isim_uzunluk"] = df["isim"].apply(len)
```

---

# 🔹 8. Gruplama ve Toplama

```python
print(df.groupby("şehir")["yaş"].mean())
```

Çıktı:

```
şehir
Ankara      25.0
İstanbul    30.0
İzmir       22.0
Name: yaş, dtype: float64
```

Diğer fonksiyonlar:

```python
df.groupby("şehir").agg({
    "yaş": ["mean","max","min"],
    "isim": "count"
})
```

---

# 🔹 9. Birleştirme (Merge/Join/Concat)

```python
df1 = pd.DataFrame({"id":[1,2,3],"isim":["Ali","Ayşe","Mehmet"]})
df2 = pd.DataFrame({"id":[1,2,4],"yaş":[22,25,30]})

# SQL tarzı merge
merged = pd.merge(df1, df2, on="id", how="inner")
print(merged)

# Concat (dikey/yatay ekleme)
pd.concat([df1, df2], axis=0)   # alt alta
pd.concat([df1, df2], axis=1)   # yan yana
```

---

# 🔹 10. Pivot & Crosstab

```python
data = {
    "şehir":["Ankara","Ankara","İstanbul","İstanbul"],
    "yıl":[2020,2021,2020,2021],
    "satış":[100,150,200,250]
}
df = pd.DataFrame(data)

# Pivot tablo
print(df.pivot(index="şehir", columns="yıl", values="satış"))

# Crosstab
print(pd.crosstab(df["şehir"], df["yıl"]))
```

---

# 🔹 11. Zaman Serileri

```python
dates = pd.date_range("2023-01-01", periods=5, freq="D")
ts = pd.Series([10,20,30,40,50], index=dates)

print(ts["2023-01-03"])
print(ts["2023-01-01":"2023-01-04"])
```

---

# 🔹 12. İstatistiksel ve Faydalı Fonksiyonlar

```python
print(df["yaş"].mean())   # Ortalama
print(df["yaş"].median()) # Medyan
print(df["yaş"].std())    # Standart sapma
print(df.sort_values("yaş", ascending=False))  # Sıralama
print(df["isim"].unique())  # Tekil değerler
print(df["isim"].value_counts())  # Frekans
```

---

# 🔹 13. Görselleştirme (Pandas + Matplotlib)

```python
import matplotlib.pyplot as plt

df["yaş"].hist()
plt.show()

df.groupby("şehir")["yaş"].mean().plot(kind="bar")
plt.show()
```

---

# 🔹 14. Gerçek Dünya Kullanımı

* **Veri temizleme:** Eksik, hatalı değerler Pandas ile düzeltilir.
* **EDA (Exploratory Data Analysis):** Ortalama, dağılım, korelasyon kolayca incelenir.
* **Feature Engineering:** Yeni özellikler türetme.
* **Model hazırlığı:** ML modellerine girdi olarak DataFrame’den NumPy array’e dönüştürme (`df.values`).
* **Büyük veri:** Dask veya PySpark öğrenmeden önce orta ölçekli veri için Pandas en iyi araçtır.

---

# 📝 Özet

* **Series** = tek boyutlu dizi, **DataFrame** = tablo.
* Veri okuma, temizleme, dönüştürme → Pandas’ın asıl gücü.
* Gruplama, pivot, merge → tablo manipülasyonu için kritik.
* ML’de ilk aşama = veriyi Pandas ile hazırlamak.

---
Matplotlib, Python’da veri görselleştirmenin en köklü ve en güçlü kütüphanesi. NumPy matematiksel işlemleri, Pandas veriyi düzenlemeyi sağlarken; Matplotlib bize o veriyi görsel hale getirip **anlamayı ve anlatmayı** sağlar. Makine öğrenmesi yolculuğunda da grafik olmadan veri analizi yapmak neredeyse imkânsızdır. Şimdi en temelden başlayarak tüm özelliklerini uzun uzun açıklayacağım.

---

# 🔹 Matplotlib Nedir?

* **Matplotlib.pyplot** modülü, MATLAB benzeri grafik çizim arayüzü sunar.
* 2D görselleştirmelerde en çok kullanılan kütüphane.
* Pandas ve NumPy ile uyumludur.
* Basit grafiklerden profesyonel görsellere kadar geniş imkan sağlar.

```python
import matplotlib.pyplot as plt
import numpy as np
```

---

# 🔹 1. Temel Grafik Çizimi

```python
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

plt.plot(x, y)
plt.show()
```

* `plt.plot` → çizgi grafiği çizer.
* `plt.show()` → grafiği ekranda gösterir.

---

# 🔹 2. Grafik Özelleştirme

```python
plt.plot(x, y, color="red", linestyle="--", marker="o", label="Doğrusal ilişki")
plt.title("Basit Çizgi Grafiği")
plt.xlabel("X ekseni")
plt.ylabel("Y ekseni")
plt.legend()
plt.grid(True)
plt.show()
```

Burada:

* `color`, `linestyle`, `marker` → görünümü ayarlar.
* `label` ve `legend` → açıklama ekler.
* `grid(True)` → ızgara ekler.

---

# 🔹 3. Grafik Türleri

## Çizgi Grafiği

```python
plt.plot(x, y)
```

## Scatter (Dağılım Grafiği)

```python
x = np.random.rand(50)
y = np.random.rand(50)
plt.scatter(x, y, color="purple")
plt.show()
```

## Bar (Sütun Grafiği)

```python
kategoriler = ["A", "B", "C"]
değerler = [10, 20, 15]
plt.bar(kategoriler, değerler, color="orange")
plt.show()
```

## Histogram

```python
data = np.random.randn(1000)
plt.hist(data, bins=30, color="green", alpha=0.7)
plt.show()
```

## Pie (Pasta Grafiği)

```python
labels = ["Elma", "Armut", "Muz", "Karpuz"]
values = [25, 30, 20, 25]
plt.pie(values, labels=labels, autopct="%1.1f%%")
plt.show()
```

---

# 🔹 4. Subplots (Birden Fazla Grafik)

```python
x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.cos(x)

fig, axes = plt.subplots(2, 1)  # 2 satır, 1 sütun
axes[0].plot(x, y1, label="sin")
axes[1].plot(x, y2, label="cos", color="red")

axes[0].legend()
axes[1].legend()
plt.show()
```

---

# 🔹 5. Stil ve Tasarım

Matplotlib’de hazır temalar var:

```python
plt.style.use("ggplot")   # ggplot tarzı
plt.plot(x, y)
plt.show()
```

Diğer stiller: `"seaborn"`, `"classic"`, `"fivethirtyeight"`, `"dark_background"`

---

# 🔹 6. Özelleştirilmiş Grafikler

## Renkler ve İşaretçiler

```python
plt.plot(x, y, "bo--")   # mavi (blue), daire marker (o), kesikli çizgi (--).
```

## Eksen Limitleri

```python
plt.plot(x, y)
plt.xlim(0, 6)
plt.ylim(0, 12)
plt.show()
```

## Annotation (Not ekleme)

```python
plt.plot(x, y)
plt.annotate("Önemli nokta", xy=(2,4), xytext=(3,8),
             arrowprops=dict(facecolor="black", arrowstyle="->"))
plt.show()
```

---

# 🔹 7. İleri Seviye Kullanımlar

## Çoklu Eksen (Twin Axes)

```python
x = np.arange(0,10,1)
y1 = x**2
y2 = np.sqrt(x)

fig, ax1 = plt.subplots()
ax2 = ax1.twinx()

ax1.plot(x, y1, "g-")
ax2.plot(x, y2, "b-")

plt.show()
```

## 3D Grafikler

```python
from mpl_toolkits.mplot3d import Axes3D

fig = plt.figure()
ax = fig.add_subplot(111, projection="3d")
x = np.random.rand(100)
y = np.random.rand(100)
z = np.random.rand(100)

ax.scatter(x, y, z, c="red", marker="o")
plt.show()
```

---

# 🔹 8. Pandas + Matplotlib Birlikte

Pandas DataFrame doğrudan Matplotlib ile uyumludur.

```python
import pandas as pd

df = pd.DataFrame({
    "yıl":[2018,2019,2020,2021],
    "satış":[100,150,200,250]
})

df.plot(x="yıl", y="satış", kind="line", marker="o")
plt.show()
```

---

# 🔹 9. Gerçek Dünya Kullanımı

* **EDA (Keşifsel Veri Analizi):** Histogram, scatter → veri dağılımını anlama.
* **Model değerlendirme:** ROC eğrisi, confusion matrix görselleştirme.
* **Zaman serisi:** Trendleri çizmek.
* **Araştırma raporları:** Grafiklerle desteklenen bulgular.

---

# 📝 Özet

* `plt.plot` → çizgi, `plt.scatter` → dağılım, `plt.bar` → sütun, `plt.hist` → histogram, `plt.pie` → pasta.
* `plt.title`, `xlabel`, `ylabel`, `legend`, `grid` ile grafik özelleştirilir.
* Subplots → birden fazla grafik aynı ekranda.
* İleri seviye: 3D grafikler, çift eksen, stiller.

---
Seaborn, Matplotlib’in üzerine inşa edilmiş, ama çok daha **estetik, hazır temalı ve istatistik odaklı** bir görselleştirme kütüphanesi. Eğer Matplotlib “ana motor” ise, Seaborn da “tasarımcı elinden çıkmış gösterge paneli” gibi düşünülebilir. Veri analizi yaparken çok daha az kodla şık ve açıklayıcı grafikler üretmemizi sağlar.

Şimdi en baştan, tüm özellikleriyle ve kod örnekleriyle anlatacağım.

---

# 🔹 Seaborn Nedir?

* Matplotlib’in üzerine kurulu, ama daha kolay ve şık görseller sağlar.
* Özellikle **istatistiksel grafikler** için geliştirilmiştir.
* Pandas DataFrame’lerle mükemmel uyumludur.
* Grafikler varsayılan olarak daha estetik (renkler, gridler, fontlar hazır ayarlanmıştır).

```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

# Örnek dataset yükleyelim
df = sns.load_dataset("tips")  # Restoran bahşiş verileri
print(df.head())
```

---

# 🔹 1. Temel Grafikler

## Çizgi Grafik

```python
sns.lineplot(x="total_bill", y="tip", data=df)
plt.show()
```

## Scatter (Dağılım Grafiği)

```python
sns.scatterplot(x="total_bill", y="tip", data=df, hue="sex", style="time")
plt.show()
```

* `hue` → renklendirme için kategori
* `style` → işaretçi şekli

## Barplot

```python
sns.barplot(x="day", y="total_bill", data=df)
plt.show()
```

Varsayılan olarak ortalama değerleri gösterir, hata çubukları ekler.

---

# 🔹 2. Kategorik Grafikler

## Countplot (Frekans Grafiği)

```python
sns.countplot(x="day", data=df, palette="pastel")
plt.show()
```

Her kategoride kaç tane gözlem olduğunu gösterir.

## Boxplot (Kutu Grafiği)

```python
sns.boxplot(x="day", y="total_bill", data=df, palette="Set2")
plt.show()
```

Veri dağılımı, medyan, çeyrekler ve aykırı değerleri gösterir.

## Violinplot

```python
sns.violinplot(x="day", y="total_bill", data=df, palette="muted")
plt.show()
```

Boxplot + Kernel Density (yoğunluk eğrisi) birleşimi.

---

# 🔹 3. İstatistiksel Grafikler

## Histogram & KDE (Yoğunluk Grafiği)

```python
sns.histplot(df["total_bill"], bins=20, kde=True, color="skyblue")
plt.show()
```

## Jointplot (İki Değişken İlişkisi)

```python
sns.jointplot(x="total_bill", y="tip", data=df, kind="scatter")
sns.jointplot(x="total_bill", y="tip", data=df, kind="hex")
```

## Pairplot (Çoklu Değişken İlişkisi)

```python
sns.pairplot(df[["total_bill","tip","size","sex"]], hue="sex")
plt.show()
```

Birden fazla değişkenin scatter ve histogram kombinasyonunu çıkarır.

---

# 🔹 4. Korelasyon ve Isı Haritası

```python
corr = df.corr(numeric_only=True)
sns.heatmap(corr, annot=True, cmap="coolwarm", linewidths=0.5)
plt.show()
```

* Değişkenler arasındaki korelasyonu renklerle gösterir.
* ML projelerinde **özellik seçimi** yaparken çok kullanılır.

---

# 🔹 5. Stil ve Tema

Seaborn varsayılan olarak güzel grafikler sunar ama temaları değiştirmek mümkün:

```python
sns.set_style("darkgrid")   # ["darkgrid","whitegrid","dark","white","ticks"]
sns.set_context("talk")     # ["paper","notebook","talk","poster"]
```

Renk paletleri:

```python
sns.set_palette("pastel")
sns.set_palette("husl")
sns.set_palette("coolwarm")
```

---

# 🔹 6. İleri Seviye Grafikler

## FacetGrid (Çoklu Grafik)

```python
g = sns.FacetGrid(df, col="sex", row="smoker")
g.map_dataframe(sns.scatterplot, x="total_bill", y="tip")
plt.show()
```

Her alt gruba göre ayrı grafikler üretir.

## Regression Plot

```python
sns.lmplot(x="total_bill", y="tip", data=df, hue="sex")
plt.show()
```

Scatter + doğrusal regresyon çizgisi.

---

# 🔹 7. Pandas ile Birlikte

Seaborn, Pandas DataFrame’lerle direkt çalışır. Örneğin:

```python
iris = sns.load_dataset("iris")
sns.pairplot(iris, hue="species")
plt.show()
```

Bu tek satır kodla Iris veri setindeki üç türü (setosa, versicolor, virginica) ayırt eden grafikler çıkarır.

---

# 🔹 8. Gerçek Dünya Kullanımı

* **EDA (Keşifsel Veri Analizi):** Histogram, boxplot, scatterplot → veri dağılımını anlamak.
* **Korelasyon Analizi:** Heatmap → hangi değişkenler ilişkili.
* **Model Görselleştirme:** Regresyon çizgileri, sınıf dağılımları.
* **Raporlama:** Profesyonel görünümlü grafiklerle sonuçları sunmak.

---

# 📝 Özet

* Matplotlib → temel grafik motoru.
* Seaborn → estetik + istatistiksel görselleştirme.
* `lineplot`, `scatterplot`, `barplot`, `countplot`, `boxplot`, `violinplot`, `heatmap`, `pairplot` → en sık kullanılan fonksiyonlar.
* Özellikle ML’de **EDA aşamasında vazgeçilmez**.

---