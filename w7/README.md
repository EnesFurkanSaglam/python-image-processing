
# ✂️ Kenar Bulma Algoritmaları

Bu çalışmada, bir görüntüdeki nesnelerin sınırlarını bulmak için kullanılan **kenar tespit algoritmalarını** denedik. Görselin neresi nereden ayrılıyor, nerede geçişler var bunu anlamaya çalıştık. Bu işlemler, bilgisayarın görüntü içindeki şekilleri ve nesneleri tanımasında çok önemli.

---

## 🎯 Amaç Neydi?

Amacımız, bir görüntüdeki **geçiş noktalarını**, yani kenarları farklı yöntemlerle bulmaktı. Çünkü kenarlar:
- Nesnelerin sınırlarını belirtir.
- Görüntüdeki yapının temelini oluşturur.
- Tanıma sistemleri için başlangıç verisi sağlar.

---

## 🛠️ Neler Yaptık?

Notebook’ta uygulanan işlemler:

- 🖼️ Görseli gri tonlamalı olarak içeri aktardık.
- 🔍 4 farklı kenar bulma yöntemi denedik:
  - **Sobel X**: Yatay kenarları bulur.
  - **Sobel Y**: Dikey kenarları bulur.
  - **Laplacian**: Kenarların tamamını birden bulmaya çalışır.
  - **Canny**: En gelişmiş olanı. Gürültüyü filtreler, güçlü kenarları seçer.

---

## ✅ Sonuç Ne Oldu?

- Her algoritma farklı şekilde kenarları ortaya çıkardı.
- Laplacian yöntemi daha genel çalışırken, Sobel yöntemleri yönlü çalıştı.
- Canny algoritması net, belirgin ve sade kenarlar verdi.
- Görüntünün hangi bölümlerinde detay olduğunu daha net görebildik.

---

## 📌 Bu Nerede İşine Yarar?

- Yüz tanıma, plaka okuma gibi görevlerde ilk adım olarak kullanılır.
- Robotik ve otonom sistemlerde nesne sınırlarını tanımada.
- Görüntü segmentasyonu ve haritalama işlemlerinde.
- Medikal görüntülemede tümör, damar gibi yapıların sınırlarını çıkarmada.

---

Bu çalışmayla, görüntü işlemede “kenar”ın ne kadar önemli olduğunu ve nasıl tespit edildiğini öğrenmiş olduk. Görselliği matematiksel olarak anlamaya bir adım daha attık! 🧠📷
