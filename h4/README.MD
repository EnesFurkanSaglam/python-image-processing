# 🧪 Hibrit Görüntü Oluşturma / Hybrid Image Creation

## 📌 Açıklama | Description

Bu proje, iki farklı görüntüyü frekans alanında birleştirerek **hibrit bir görüntü** oluşturmayı amaçlamaktadır. Görsel işlemelerde düşük frekans (bulanıklık) ve yüksek frekans (detaylar) filtreleme teknikleri kullanılarak, her iki görüntünün belirli özellikleri harmanlanır.

This project aims to create a **hybrid image** by combining two different images in the frequency domain. Using low-pass (blur) and high-pass (detail) filtering techniques, selected features of both images are merged.

---

## 🔧 Kullanılan Teknolojiler | Technologies Used

- Python 3.x
- OpenCV
- NumPy
- Matplotlib
- Jupyter Notebook (`.ipynb`)

---

## 📂 Proje Adımları | Project Steps

1. İki farklı görsel yüklenir (örnek: `kedi.jpg` ve `kopek.jpg`).
2. `image1` için **low-pass** (Gaussian blur) filtresi uygulanır.
3. `image2` için **high-pass** filtre uygulanır (orijinal - blur farkı).
4. İki işlem sonucu görsel birleştirilerek **hibrit görüntü** elde edilir.
5. Hibrit görüntü farklı ölçeklerde gösterilir.
6. Tüm adımlar grafiklerle gösterilir.

