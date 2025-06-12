
# 📊 Fourier Dönüşümü ile Görüntü Analizi

Bu çalışmada, bir görüntünün sadece nasıl göründüğüne değil, **nasıl oluştuğuna** yani frekans bileşenlerine baktık. Bunun için **Fourier dönüşümü** kullandık. Bu teknik, görüntüyü pikseller yerine "dalga bileşenleri" şeklinde analiz etmemizi sağlar.

---

## 🎯 Amaç Neydi?

Amaç, görüntülerin içindeki **frekans bilgilerini** keşfetmekti. Özellikle bulanıklık, keskinlik gibi özellikler bu bilgilerle ilgilidir. Fourier dönüşümü sayesinde:
- Görüntüde yüksek frekans (kenarlar, detaylar)
- Düşük frekans (genel yapı, gölgeler)

gibi özellikleri ayrı ayrı inceleyebildik.

---

## 🛠️ Neler Yaptık?

Notebook’ta şu adımları izledik:

- 🖼️ `resim.jpg` görselini gri tonlamalı olarak içeri aldık.
- 🔄 `np.fft.fft2()` ile 2D Fourier dönüşümünü uyguladık.
- 🎯 `np.fft.fftshift()` ile sıfır frekans bileşenini merkeze kaydırdık (görsel analiz için daha uygun).
- 🔍 Frekans spektrumunu `log` ölçeğiyle büyüklük olarak gösterdik.
- 🎨 Hem orijinal görüntüyü hem de spektrumu görselleştirdik.

---

## ✅ Sonuç Ne Oldu?

- Görüntünün hangi frekanslarda ne kadar bilgi taşıdığı ortaya çıktı.
- Fourier spektrumunda merkeze yakın bölgeler düşük frekansları, dış kısımlar yüksek frekansları temsil etti.
- Bu dönüşüm sayesinde görüntünün detaylı yapısını başka bir boyutta analiz edebildik.

---

## 📌 Bu Nerede İşine Yarar?

- Görüntü sıkıştırma (JPEG gibi) ve filtreleme algoritmalarında.
- Gürültü azaltma veya detay artırma işlemlerinde.
- Tıbbi görüntüleme, yüz tanıma ve sinyal işleme gibi alanlarda.

---

Fourier dönüşümü, görüntüyü anlamanın bambaşka bir yoludur. Bu örnekle, onun ne kadar güçlü bir araç olduğunu ilk adımda deneyimledik! 📈🧠
