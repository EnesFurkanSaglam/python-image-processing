
# 🧪 Görüntü Filtreleri ve Kenar Bulma

Bu çalışmada bir görüntünün üzerine farklı filtreler uyguladık ve ardından kenar bulma işlemlerini gerçekleştirdik. Amaç, bir görüntünün nasıl "temizlenip" işlenebileceğini ve kenarların nasıl ortaya çıkarılabileceğini gözlemlemekti.

---

## 🎯 Amaç Neydi?

Görüntüler bazen çok gürültülü olabilir veya detayları net bir şekilde seçilemeyebilir. Bu yüzden:
- Filtrelerle resmi yumuşatarak parazitlerden arındırdık.
- Kenar bulma işlemleriyle görüntüdeki nesnelerin sınırlarını tespit ettik.

---

## 🛠️ Neler Yaptık?

Notebook’ta yaptığımız işlemler:

- 📥 `resim.jpg` adlı görseli gri tonlamalı olarak içeri aktardık.
- 🔽 Filtreler uyguladık:
  - **Ortalama (Blur)**: Komşu piksellerin ortalamasını alır, basit bir yumuşatma sağlar.
  - **Gaussian Blur**: Daha doğal ve gerçekçi bir bulanıklaştırma.
  - **Median Blur**: Gürültülü görüntülerde etkili, ortanca değeri alır.
- ✂️ Kenar bulma algoritmaları uyguladık:
  - **Sobel X/Y**: Yatay ve dikey kenarları bulur. İkisini birleştirdik.
  - **Laplacian**: Tüm kenarları bir anda tespit etmeye çalışır.
- 🎨 Tüm filtrelerin sonuçlarını yan yana görselleştirdik.

---

## ✅ Sonuç Ne Oldu?

- Farklı filtrelerin görüntüde nasıl etkiler bıraktığını net bir şekilde gözlemledik.
- Kenar bulma algoritmaları sayesinde görüntüdeki şekil ve hatları ortaya çıkardık.
- Farklı senaryolarda hangi filtrenin daha uygun olabileceğini karşılaştırmalı olarak görmüş olduk.

---

## 📌 Bu Nerede İşine Yarar?

- Gürültülü kamera görüntülerini düzeltmede.
- Yüz, araç, nesne tanıma gibi görevlerde kenar tespiti yaparken.
- Görüntüleri yapay zeka algoritmalarına **hazırlarken ön işleme (preprocessing)** adımlarında.

---

Görüntü işleme dünyasında bu filtreler temel araçlardır. Bu deneyimle birlikte, daha büyük görüntüler ve gerçek dünya verileriyle çalışmaya bir adım daha yaklaştık! 🔍📷
