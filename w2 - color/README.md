
# 🎨 Görüntü Renk Uzayları

Bu çalışmada, bir resmi bilgisayarın nasıl gördüğünü anlamak için renk uzayları üzerinde çalıştık. "resim.jpg" adlı bir görüntüyü farklı şekillerde temsil ederek, görüntü işleme dünyasında sıkça kullanılan dönüşümleri gözlemledik.

---

## 🎯 Amaç Neydi?

Görüntü işleme uygulamalarında bir resmi işlerken, bazen onun sadece renklerini değil, farklı **özelliklerini** anlamamız gerekir. Bu yüzden resmi RGB, HSV ve gri tonlamaya çevirerek, farklı renk uzaylarının bize nasıl bilgi verdiğini keşfetmek istedik.

---

## 🛠️ Neler Yaptık?

Notebook’ta şu işlemleri göreceksin:

- 🧱 OpenCV (`cv2`) ve `matplotlib.pyplot` kütüphanelerini kullandık.
- 📸 `resim.jpg` adlı resmi `cv2.imread()` ile içeri aktardık.
- 🔁 Bu resmi 3 farklı formata çevirdik:
  - `RGB`: İnsan gözüne yakın gösterim.
  - `HSV`: Renk tonu, doygunluk ve parlaklık bilgisi.
  - `Grayscale`: Sadece parlaklık bilgisi (siyah-beyaz).
- 🖼️ `matplotlib` ile bu görüntüleri görselleştirdik.

---

## ✅ Sonuç Ne Oldu?

- Aynı resmin farklı renk uzaylarında nasıl göründüğünü karşılaştırdık.
- HSV uzayı ile objelerin renklerini daha doğru analiz edebileceğimizi gördük.
- Gri tonlama sayesinde, şekil ve kenar gibi özellikleri daha iyi çıkarabileceğimizi öğrendik.

---

## 📌 Bu Nerede İşine Yarar?

- **HSV**, özellikle nesne takibi ve cilt tonu tespiti gibi uygulamalarda kullanılır.
- **Gri tonlama**, yüz tanıma, kenar bulma gibi işlemlerde temel bir adımdır.
- Bu dönüşümler, daha sonra uygulanacak filtreler, segmentasyonlar ve makine öğrenmesi modelleri için birer ön adımdır.

---

Görüntü işleme temelleri için harika bir başlangıç! 🎯
