
# 🏔️ Görüntü Piramitleri

Bu çalışmada, bir görüntünün farklı boyutlara küçültülerek analiz edilmesini sağlayan **görüntü piramitleri (image pyramids)** konusuna giriş yaptık. Bu yöntem, özellikle görüntünün hem genel yapısını hem de küçük detaylarını ayrı ayrı incelememizi sağlar.

---

## 🎯 Amaç Neydi?

Amacımız, görüntüleri farklı çözünürlüklerde işleyebilmenin mantığını kavramaktı. Çünkü bazı işlemler büyük resimde, bazıları küçük detaylarda daha iyi çalışır. Bu nedenle görüntüyü farklı “katmanlara” bölmek faydalıdır.

---

## 🛠️ Neler Yaptık?

Notebook’ta şu işlemleri yaptık:

- 🖼️ `resim.jpg` adlı görüntüyü OpenCV ile içeri aldık.
- 🎨 Renk formatını `cv2.COLOR_BGR2RGB` ile doğru hale getirdik.
- 🔄 `img.copy()` ile resmi bozmadan bir kopyasını aldık.
- 🧱 Bu görüntüden **piramidin ilk katmanını** oluşturduk (ilerleyen hücrelerde muhtemelen `cv2.pyrDown()` gibi fonksiyonlarla devam edilmiştir).

---

## ✅ Sonuç Ne Oldu?

- Görüntünün çözünürlüğünü kademeli olarak azaltarak farklı seviyelerde temsil ettik.
- Böylece hem detay hem de genel yapı farklı katmanlarda incelenebilir hale geldi.
- Bu yaklaşım, çok katmanlı analizlerde oldukça kullanışlıdır.

---

## 📌 Bu Nerede İşine Yarar?

- **Yüz tanıma**, **nesne takibi** ve **ölçek bağımsız analizlerde**.
- Görüntüleri hem büyük ölçekte (ne var?) hem de küçük ölçekte (tam olarak nerede?) işlemek için.
- Laplacian pyramids ile görüntü sıkıştırma ve yeniden yapılandırma işlemlerinde.

---

Bu çalışma, görüntü işleme dünyasında çözünürlük odaklı düşünmenin kapısını açıyor. Görüntü piramitleri sayesinde hem genel hem de detaylı analiz mümkün! 🧠📷
