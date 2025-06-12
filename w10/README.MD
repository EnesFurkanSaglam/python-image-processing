# Görüntü Eşleştirme için Özellik Tabanlı Yöntemler

Bu proje, "13-Featurebased_Image_Matching.pdf" sunumunda işlenen, bilgisayarlı görüdeki temel konulardan biri olan özellik tabanlı görüntü eşleştirme yöntemlerini açıklamak ve Python'da pratik uygulamalarını sunmak için hazırlanmıştır.

## 1. Giriş: Görüntü Eşleştirme Nedir?

[cite_start]Görüntü eşleştirme, farklı açılardan, farklı ışık koşullarında veya farklı ölçeklerde çekilmiş olsalar bile, aynı nesneyi veya sahneyi içeren iki veya daha fazla görüntüyü tanıma ve aralarındaki ilişkiyi bulma işlemidir. [cite_start]Bu, nesne tanıma, görüntü birleştirme (panorama), 3D rekonstrüksiyon ve artırılmış gerçeklik gibi birçok uygulamanın temelini oluşturur.

## 2. "Özellik" (Feature) Kavramı

[cite_start]Bir "özellik", bir görüntünün belirli bir bölgesindeki, hesaplama görevi için anlamlı ve ayırt edici olan bilgi parçasıdır. Görüntünün tamamını piksel piksel karşılaştırmak yerine, bu ayırt edici "özellikleri" karşılaştırmak çok daha verimli ve sağlamdır.

* **Keypoint (Anahtar Nokta):** Görüntüdeki köşe gibi, konumu belirgin olan ve farklı açılardan bakıldığında bile takip edilebilen noktalardır.
* **Descriptor (Tanımlayıcı):** Anahtar noktanın etrafındaki lokal bölgeyi tanımlayan sayısal bir vektördür. [cite_start]Bu vektör, o bölgenin "parmak izi" gibidir ve döndürme, ölçekleme gibi değişimlere karşı dayanıklı olacak şekilde tasarlanır.

## 3. Temel Görüntü Eşleştirme Adımları

Özellik tabanlı eşleştirme genellikle 3 adımdan oluşur:

1.  **Detect (Tespit Et):** Her iki görüntüde de potansiyel anahtar noktaları (keypoints) bul.
2.  **Describe (Tanımla):** Her anahtar noktanın etrafındaki bölge için bir özellik tanımlayıcı (descriptor) vektörü hesapla.
3.  **Match (Eşleştir):** Birinci görüntüdeki tanımlayıcıları, ikinci görüntüdeki tanımlayıcılarla karşılaştırarak en benzer olanları bul.

## 4. Özellik Çıkarıcılar: SIFT ve SURF

### a. SIFT (Scale-Invariant Feature Transform)

[cite_start]SIFT, görüntü eşleştirme alanında bir devrim yaratmış, ölçek ve döndürme değişimlerine karşı çok dayanıklı bir algoritmadır.

* **Scale-Space (Ölçek Uzayı):** Görüntünün farklı ölçeklerdeki versiyonlarını (Gauss piramidi) oluşturur ve bu uzayda en kararlı olan (lokal ekstremum) noktaları anahtar nokta olarak seçer. [cite_start]Bu sayede, nesneye yaklaşıp uzaklaşsanız bile aynı anahtar noktalar bulunur.
* **Orientation Assignment (Yönelim Atama):** Her anahtar noktaya, etrafındaki gradyan yönelimlerinin histogramını çıkararak baskın bir yönelim atar. [cite_start]Tanımlayıcıyı bu yöne göre hizalayarak döndürmeye karşı değişmezlik sağlar.
* **Descriptor (Tanımlayıcı):** Anahtar noktanın etrafındaki 16x16'lık bir pencereyi 4x4'lük alt bölgelere ayırır. Her bir alt bölge için 8 yönlü gradyan histogramı oluşturur. [cite_start]Bu 16 bölgenin 8'er binlik histogramları birleştirilerek 128 boyutlu benzersiz bir tanımlayıcı vektör elde edilir.

### b. SURF (Speeded Up Robust Features)

[cite_start]SURF, SIFT'in başarımına yakın sonuçlar verirken ondan çok daha hızlı çalışacak şekilde tasarlanmış bir alternatiftir. Hızlanmayı sağlamak için integral görüntüler gibi teknikler kullanır. [cite_start]Tanımlayıcısı, gradyanlar yerine Haar dalgacık yanıtlarının toplamına dayanır.

## 5. Geometrik Doğrulama: RANSAC

Tanımlayıcıları eşleştirdiğimizde (genellikle en yakın komşu yöntemiyle), gürültü veya benzer bölgeler nedeniyle her zaman yanlış eşleşmeler (outliers) olacaktır. [cite_start]RANSAC (RANdom SAmple Consensus), bu yanlış eşleşmeleri ayıklayıp sadece geometrik olarak tutarlı olan doğru eşleşmeleri (inliers) bulmak için kullanılan çok güçlü bir yöntemdir.

[cite_start]**Nasıl Çalışır?** 
1.  **Örneklem (Sample):** Eşleşmeler arasından rastgele küçük bir alt küme seçilir (örneğin, iki görüntü arasındaki geometrik dönüşümü -Homografi- bulmak için 4 nokta).
2.  **Model Hesapla (Solve):** Bu küçük küme kullanılarak geometrik model (örneğin homografi matrisi) hesaplanır.
3.  **Doğrula (Score):** Hesaplanan model, tüm eşleşmelere uygulanır. Modelin tahmin ettiği nokta ile gerçekte eşleşen nokta arasındaki mesafe belirli bir eşikten (`epsilon`) küçükse, bu eşleşme bir "inlier" olarak kabul edilir. [cite_start]Toplam inlier sayısı modelin skoru olur.
4.  [cite_start]**Tekrarla:** Bu işlem birçok kez tekrarlanır ve en fazla inlier sayısına sahip olan model "en iyi model" olarak seçilir.

## 6. Görüntü Temsili: Bag of Visual Words (BoVW)

Bir görüntüyü, içindeki yüzlerce özelliğin tamamıyla temsil etmek yerine, daha kompakt ve sabit boyutlu bir vektörle nasıl temsil edebiliriz? [cite_start]Bag of Visual Words (Görsel Kelime Çantası) bu soruna bir çözümdür ve metin analizindeki "Bag of Words" yaklaşımından esinlenmiştir. [cite_start]Fikir, bir görüntüyü, içinde hangi "görsel kelimelerin" kaç kez geçtiğini sayan bir histogram olarak temsil etmektir.

**BoVW İşlem Adımları:**
1.  [cite_start]**Özellik Çıkarma:** Büyük bir eğitim veri setindeki (binlerce resim) tüm görüntülerden SIFT gibi bir yöntemle milyonlarca özellik tanımlayıcısı çıkarılır.
2.  **Sözlük (Vocabulary) Oluşturma:** Bu milyonlarca tanımlayıcı, K-Means gibi bir kümeleme algoritması kullanılarak `K` adet gruba ayrılır. Her bir kümenin merkezi (centroid), bir "görsel kelime" olarak kabul edilir. [cite_start]Bu `K` adet görsel kelime, bizim "görsel sözlüğümüzü" (codebook) oluşturur.
3.  **Görüntüyü Histogram Olarak Temsil Etme:** Yeni bir görüntüyü temsil etmek için:
    * Önce o görüntüdeki tüm SIFT tanımlayıcıları çıkarılır.
    * Her bir tanımlayıcının, sözlükteki hangi "görsel kelimeye" en yakın olduğu bulunur.
    * [cite_start]`K` boyutlu bir histogram oluşturulur ve görüntüde her bir görsel kelimenin kaç kez geçtiği sayılır. Bu histogram, artık o görüntünün sabit boyutlu ve kompakt bir temsilidir.

[cite_start]Bu histogramlar, iki görüntünün ne kadar benzer olduğunu (örneğin, histogram kesişimi veya Öklid mesafesi ile) çok hızlı bir şekilde hesaplamak için kullanılabilir.

## 7. İleri Düzey Global Tanımlayıcılar (Teorik)

* **Vocabulary Trees (Sözlük Ağaçları):** BoVW'nin hiyerarşik bir versiyonudur. K-Means'i katmanlı bir şekilde uygulayarak bir ağaç yapısı oluşturur. [cite_start]Bu, on binlerce veya milyonlarca görsel kelime içeren çok büyük sözlüklerle verimli bir şekilde çalışmayı sağlar.
* **Fisher Vector:** BoVW'den daha güçlü bir temsil yöntemidir. [cite_start]Sadece hangi kelimenin geçtiğini saymakla kalmaz, aynı zamanda bir özelliğin en yakın olduğu kelime merkezinden ne kadar uzakta olduğu gibi daha zengin istatistiksel bilgileri de kodlar. Bu, genellikle daha iyi arama sonuçları verir.

[cite_start]Bu iki yöntem, özellikle milyonlarca görüntülük veri setlerinde görsel arama yapmak için kullanılır ve MPEG CDVS gibi standartların temelini oluşturur.