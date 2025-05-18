
# 🔄 Görüntü Negatifi Oluşturma

Bu çalışmada, bir görüntünün **negatifini** nasıl oluşturabileceğimizi öğrendik. Aslında çok basit bir matematiksel işlemle, görseli ters çevirmiş olduk. Peki neden böyle bir şeye ihtiyaç duyarız? Hemen bakalım.

---

## 🎯 Amaç Neydi?

Görüntülerin negatifleri, özellikle eski tıbbi görüntülerde ve film şeritlerinde sıkça kullanılır. Ayrıca bazı durumlarda orijinal görselde fark edemediğimiz detaylar negatifinde daha net ortaya çıkabilir. Biz de bunu pratikte görmek istedik.

---

## 🛠️ Neler Yaptık?

Notebook’ta şu adımları izledik:

- 📥 `resim.jpg` adlı görseli **gri tonlamalı** olarak içeri aktardık.
- ❌ Her pikselin değerini `255 - piksel_değeri` formülüyle ters çevirdik. Bu işleme **negatif görüntü** denir.
- 🎨 `matplotlib` ile hem orijinal hem de negatif görüntüyü görselleştirdik.

---

## ✅ Sonuç Ne Oldu?

- Görselin siyah olan yerleri beyaza, açık gri olanlar koyu griye dönüştü.
- Negatif görüntü sayesinde bazı detaylar daha görünür hale geldi.
- Görüntü işleme işlemlerinin aslında basit matematiksel mantıklara dayandığını gördük.

---

## 📌 Bu Nerede İşine Yarar?

- Eski röntgen veya film şeritlerinin dijitalleştirilmesinde.
- Görsel kontrastı artırmak ve detayları daha net görmek istediğimizde.
- Bazı bilgisayarla görme algoritmalarında, veri çeşitliliğini artırmak için.

---

Bu çalışmayla birlikte, görüntü işlemede çok sık karşılaşacağımız basit ama etkili bir yöntemi öğrenmiş olduk. 👍
