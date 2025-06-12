# Görüntü İşleme: İleri Seviye Segmentasyon Teknikleri

Bu proje, "12-segmentation-part2.pdf" sunumunda işlenen ileri seviye segmentasyon yöntemlerini uygulamalı olarak açıklamaktadır. Bu bölümde, küme sayısını otomatik bulan **Mean-Shift** ve pikseller arası ilişkileri bir graf olarak modelleyen **Grafik-Tabanlı Yöntemler (Normalized Cuts, GrabCut)** üzerine odaklanılmıştır.

Bu `README` dosyası, `ileri_seviye_segmentasyon.py` betiğinde kullanılan algoritmaların teorik altyapısını açıklamaktadır.

## 1. Mean-Shift Segmentasyonu

Mean-Shift, K-Means'ten farklı olarak küme sayısını (`K`) önceden belirtmenizi gerektirmeyen, yoğunluk tabanlı bir kümeleme algoritmasıdır. Özellik uzayındaki yoğunluk tepelerini (modları) bularak çalışır.

**Nasıl Çalışır?**
1.  Her veri noktası için bir arama penceresi (search window) başlatılır.
2.  Pencere içindeki noktaların ortalaması (merkezi) hesaplanır.
3.  Arama penceresi, hesaplanan bu yeni merkeze kaydırılır (mean shift).
4.  Bu kaydırma işlemi, pencere bir yoğunluk tepesine (mode) yakınsayana kadar tekrarlanır.
5.  Aynı tepe noktasına yakınsayan tüm başlangıç noktaları, aynı kümeye (segmente) ait kabul edilir.

**Avantajları ve Dezavantajları:**
* **Artıları:** Küme sayısını otomatik bulur, küme şekilleri için varsayımda bulunmaz (sadece küresel değil) ve aykırı değerlere karşı daha dayanıklıdır.
* **Eksileri:** Tek parametresi olan pencere boyutuna (`bandwidth`) duyarlıdır, hesaplama maliyeti yüksektir ve özellik uzayının boyutu arttıkça verimliliği düşer.

## 2. Grafik-Tabanlı (Graph-Based) Segmentasyon

Bu yaklaşımda, görüntü bir **graf** olarak temsil edilir:
* **Düğümler (Nodes):** Görüntüdeki her bir piksel bir düğümdür.
* **Kenarlar (Edges):** Birbirine komşu olan düğümler arasında bir kenar bulunur.
* **Ağırlıklar (Weights):** Her kenarın bir ağırlığı vardır ve bu ağırlık, iki düğümün ne kadar "benzer" olduğunu temsil eder.

Segmentasyon, bu grafiği anlamlı alt gruplara **bölme (partitioning)** problemine dönüşür.

### a. Minimum Cut (Min-Cut)
Grafiği ikiye bölmek için kesilmesi gereken kenarların toplam ağırlığını minimize etmeyi hedefler. Ancak bu yöntem, genellikle ideal olmayan küçük ve izole bölgeler oluşturma eğilimindedir, çünkü tek bir pikseli ayırmanın maliyeti çok düşüktür.

### b. Normalized Cuts (N-Cut)
Min-Cut'ın bu sorununu çözmek için geliştirilmiştir. Sadece kesilen kenarların ağırlığını değil, aynı zamanda oluşan parçaların kendi içlerindeki toplam bağlantılarını da hesaba katarak bir "normalizasyon" yapar. Bu, küçük parçaları ayırmayı cezalandırır ve daha dengeli bölmeler üretir.

N-Cut, problemi bir özdeğer (eigenvalue) problemine dönüştürerek çözer. En küçük ikinci özdeğere karşılık gelen özvektör, grafiği ikiye bölmek için en iyi yolu gösterir.

## 3. Etkileşimli Segmentasyon (Interactive Segmentation) - GrabCut

Bu yöntem, kullanıcının sürece dahil olduğu bir segmentasyon türüdür. Kullanıcı, fırça darbeleriyle veya segment edilecek nesnenin etrafına bir dikdörtgen çizerek ön plan ve arka plan hakkında ipuçları verir.

GrabCut algoritması, bu ipuçlarını kullanarak bir grafik oluşturur ve ön planı arka plandan ayırmak için optimize edilmiş bir **min-cut** algoritması çalıştırır. Bu, belirli bir nesneyi arka plandan hassas bir şekilde ayırmak için çok güçlü bir tekniktir.

## 4. Yukarıdan-Aşağıya (Top-Down) Segmentasyon

Bu yaklaşım, segmentasyon sürecini yönlendirmek için nesneye özgü ön bilgileri (örneğin bir atın veya bir insanın genel şekli) kullanan gelişmiş bir yöntemdir. Aşağıdan-yukarıya (bottom-up) sinyalleri (renk, doku vb.) yukarıdan-aşağıya (top-down) bir modelle birleştirir. Bu, genellikle özel olarak eğitilmiş makine öğrenmesi modelleri gerektiren bir araştırma alanıdır.