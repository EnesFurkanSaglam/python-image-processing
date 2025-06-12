# Görüntü İşleme: Segmentasyon Teknikleri ve Uygulamaları

## 1. Görüntü Segmentasyonu Nedir?

Görüntü segmentasyonu, dijital bir görüntüyü birden çok parçaya (segment) veya nesneye bölme işlemidir. Temel amaç, bir görüntünün temsilini daha anlamlı ve analiz edilmesi daha kolay bir şeye basitleştirmek veya değiştirmektir.

* [cite_start]**Hedef:** Pikselleri, ait oldukları nesnelere veya bölgelere göre gruplamaktır. Örneğin, bir kaplan fotoğrafında, kaplanı çim arka planından ayırmak bir segmentasyon işlemidir.
* [cite_start]**"Superpixels" (Süper Pikseller):** Görüntüyü, benzer özelliklere sahip küçük piksel gruplarına ayırarak daha ileri işlemler için verimlilik sağlayan bir ön işleme adımıdır. Bu, pikseller yerine daha anlamlı küçük bölgelerle çalışmamızı sağlar.

## 2. Gestalt Psikolojisi ve Algısal Gruplama

Segmentasyon algoritmaları, aslında insan görsel sisteminin nesneleri nasıl grupladığını taklit etmeye çalışır. [cite_start]Gestalt psikolojisi, bu gruplama eğilimlerini açıklayan bir dizi ilke ortaya koymuştur.

* [cite_start]**Proximity (Yakınlık):** Birbirine yakın olan nesneler bir grup olarak algılanır.
* [cite_start]**Similarity (Benzerlik):** Renk, şekil, doku gibi özellikleri benzer olan nesneler birlikte gruplanır.
* [cite_start]**Continuity (Süreklilik):** Gözümüz, ani ve keskin değişiklikler yerine yumuşak ve sürekli hatları takip etme eğilimindedir.
* **Closure (Kapanma):** Beynimiz, eksik parçaları olan şekilleri tamamlama eğilimindedir. [cite_start]Örneğin, üçgen gibi görünmesi için yerleştirilmiş üç Pac-Man şekli, aslında orada olmayan bir üçgeni algılamamıza neden olur.
* [cite_start]**Common Fate (Ortak Kader):** Aynı yönde ve hızda hareket eden nesneler bir grup olarak algılanır. Bu ilke genellikle video analizinde kullanılır.
* [cite_start]**Symmetry (Simetri):** Simetrik nesneler, çevresindeki karmaşıklıktan daha kolay ayırt edilir ve bir bütün olarak algılanır.
* [cite_start]**Familiarity (Aşinalık):** Bir şekil veya desen, bize tanıdık bir nesneyi (örneğin bir yüz) hatırlatıyorsa, onu bir bütün olarak algılarız.

Bu ilkeler, neden bazı segmentasyon algoritmalarının belirli özelliklere (renk, konum vb.) odaklandığını anlamak için temel bir çerçeve sunar.

## 3. Temel Segmentasyon Teknikleri

### a. Arka Plan Çıkarma (Background Subtraction)

[cite_start]Bu teknik, özellikle video gözetim gibi uygulamalarda, sabit bir arka planda hareket eden nesneleri tespit etmek için kullanılır.

* **Nasıl Çalışır?**
    1.  Videonun birkaç karesi veya belirli bir süre boyunca bir "arka plan modeli" oluşturulur (genellikle piksellerin ortalaması veya medyanı alınır).
    2.  Gelen her yeni kare, bu arka plan modelinden çıkarılır.
    3.  Farkın mutlak değeri belirli bir eşiğin üzerindeyse, o pikseller "ön plan" (hareketli nesne) olarak kabul edilir.
* **Kullanım Alanları:** Güvenlik kameralarında insan tespiti, trafik akışı izleme.
* **Zorluklar:** Işık değişiklikleri, arka plana yeni bir nesnenin gelip durması (örneğin park eden bir araba) modelin güncellenmesini gerektirir.

### b. Histogram Tabanlı Segmentasyon

Bu, en basit segmentasyon yöntemlerinden biridir. Görüntünün yoğunluk (grayscale) histogramını analiz ederek çalışır.

* **Nasıl Çalışır?**
    1.  [cite_start]Görüntünün yoğunluk histogramı oluşturulur. Histogram, her bir yoğunluk seviyesinde (0-255 arası) kaç piksel olduğunu gösterir.
    2.  Histogramda belirgin "tepeler" ve "vadiler" aranır. [cite_start]Her tepe, görüntüdeki bir nesne grubunun (örneğin, koyu nesneler, gri nesneler, açık arka plan) yoğunluk dağılımını temsil eder.
    3.  Vadiler, bu grupları ayırmak için ideal eşik değerleri olarak seçilir.
* **Ne İşe Yarar?** Görüntüde birbirinden net bir şekilde ayrılan yoğunluklara sahip nesneler varsa (örneğin, siyah bir arka plan üzerinde beyaz bir metin) çok etkilidir.
* [cite_start]**Sınırlılıkları:** Eğer nesnelerin yoğunluk dağılımları iç içe geçmişse (histogramdaki tepeler net değilse), doğru eşik değerlerini bulmak imkansızlaşır. Bu durum, bizi daha gelişmiş yöntemler olan kümelemeye yönlendirir.

## 4. Kümeleme Tabanlı Segmentasyon (Clustering)

[cite_start]Segmentasyon, bir "kümeleme" problemi olarak formüle edilebilir. Buradaki amaç, pikselleri özelliklerine göre gruplara (kümelere) ayırmaktır.

### a. K-Means Kümeleme (K-Means Clustering)

K-Means, en popüler ve yaygın kullanılan kümeleme algoritmalarından biridir.

* [cite_start]**Algoritma Adımları:** 
    1.  [cite_start]**Başlatma:** Kaç küme (`K`) istediğinizi belirlersiniz ve `K` adet küme merkezini rastgele başlatırsınız.
    2.  **Atama:** Her pikseli, kendisine en yakın olan küme merkezine atarsınız. [cite_start]Böylece her merkez, bir grup pikselin "sahibi" olur.
    3.  [cite_start]**Güncelleme:** Her küme merkezinin konumunu, o kümedeki tüm piksellerin özelliklerinin ortalamasını alarak yeniden hesaplarsınız.
    4.  **Tekrarlama:** Küme merkezleri artık değişmeyene (veya çok az değişene) kadar 2. ve 3. adımları tekrarlarsınız.

* **`K` Değerinin Rolü:** `K`, görüntüde kaç farklı segment (renk, doku vb.) bulmak istediğinizi belirtir.
* [cite_start]**Avantajları:** Basit, hızlı ve uygulaması kolaydır.
* [cite_start]**Dezavantajları:** 
    * `K` değerinin önceden bilinmesi gerekir.
    * Rastgele başlangıç ​​noktalarına duyarlıdır, bu da farklı denemelerde farklı sonuçlar verebilir.
    * Aykırı (outlier) piksellerden etkilenir.
    * Genellikle küresel (yuvarlak) kümeleri iyi bulur, ancak uzun veya düzensiz şekilli kümelerde zorlanabilir.

### b. Hiyerarşik Kümeleme (Hierarchical Clustering)

* [cite_start]**Birleştirmeli (Agglomerative):** Her pikselin kendi kümesiyle başladığı ve her adımda en benzer iki kümenin birleştirildiği aşağıdan yukarıya bir yaklaşımdır. [cite_start]Bu süreç, tek bir küme kalana kadar devam eder ve bir "dendrogram"  ile görselleştirilir.
* [cite_start]**Bölmeli (Divisive):** Tüm piksellerin tek bir kümede başladığı ve her adımda en uygun kümenin ikiye bölündüğü yukarıdan aşağıya bir yaklaşımdır.

## 5. Özellik Uzayının Seçimi (Feature Space)

K-Means'in gücü, hangi **özelliklere** göre kümeleme yaptığınıza bağlıdır. Pikselleri farklı özellik uzaylarında temsil ederek çok farklı segmentasyon sonuçları elde edebiliriz.

### a. Yoğunluk (Intensity) Özellik Uzayı

* **Özellik Vektörü:** Her piksel için tek boyutlu bir vektördür: `[yoğunluk]`.
* [cite_start]**Sonuç:** Görüntüyü `K` farklı parlaklık seviyesine ayırır. Siyah-beyaz bir görüntüde nesneleri parlaklıklarına göre gruplar.

### b. Renk (Color) Özellik Uzayı

* **Özellik Vektörü:** Her piksel için 3 boyutlu bir vektördür: `[R, G, B]` (Kırmızı, Yeşil, Mavi).
* [cite_start]**Sonuç:** Görüntüdeki pikselleri renk benzerliğine göre `K` gruba ayırır. Bu, genellikle sadece yoğunluğa göre segmentasyondan daha iyi sonuçlar verir. Ancak, aynı renkteki ama farklı konumlardaki nesneleri ayıramaz.

### c. Renk + Konum (Color + Position) Özellik Uzayı

Bu, hem renk benzerliğini hem de Gestalt'ın **Yakınlık (Proximity)** ilkesini hesaba katmanın zekice bir yoludur.

* **Özellik Vektörü:** Her piksel için 5 boyutlu bir vektördür: `[R, G, B, x, y]`. Burada `x` ve `y` pikselin koordinatlarıdır.
* [cite_start]**Sonuç:** Sadece rengi benzer olanları değil, aynı zamanda birbirine **yakın** olan ve rengi benzer olan pikselleri gruplamaya çalışır. Bu, genellikle çok daha tutarlı ve nesneye benzer segmentler üretir. [cite_start]Örneğin, bir pandanın siyah gözü ile siyah bacağını, konumları farklı olduğu için ayrı segmentler olarak ayırabilir.

### d. Doku (Texture) Özellik Uzayı

Doku, bir bölgedeki yoğunluk değişimlerinin desenidir. Örneğin, çim, ağaç kabuğu veya bir kumaşın kendine has dokuları vardır.

* **Nasıl Çalışır?**
    1.  Görüntüye bir dizi filtre (filtre bankası) uygulanır. [cite_start]Bu filtreler kenarları, köşeleri, belirli yönelimleri vb. tespit eder.
    2.  Her piksel için, bu filtrelerden gelen yanıtlar bir özellik vektörü oluşturur.
    3.  Bu yüksek boyutlu doku vektörleri üzerinde K-Means gibi bir kümeleme algoritması çalıştırılır.
* [cite_start]**"Texton"lar:** Doku özellik vektörleri kümelendiğinde, her küme merkezine bir "texton" (temel doku birimi) denir. Segmentasyon, görüntüyü bu texton haritasına göre bölgelere ayırır.
* [cite_start]**Sonuç:** Renkleri benzer olsa bile dokuları farklı olan bölgeleri (örneğin, bir zebranın siyah-beyaz çizgileri ile kuru otların dokusu) birbirinden ayırabilir.