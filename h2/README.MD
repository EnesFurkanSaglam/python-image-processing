# README

## Code Functionality (English)

This project demonstrates basic image processing techniques using OpenCV, NumPy, and Matplotlib. The code performs the following steps:

- **Image Reading:** Reads the image file (`cat.jpg`) in grayscale mode using OpenCV.
- **Channel Extraction:** Divides the grayscale image vertically into three equal parts, simulating the Blue (B), Green (G), and Red (R) channels.
- **Channel Visualization:** Displays each channel separately with Matplotlib using distinct colormaps:
  - Blue channel with the `Blues` colormap,
  - Green channel with the `Greens` colormap,
  - Red channel with the `Reds` colormap.
- **Channel Merging:** Combines pairs of channels (R+B, G+B, R+G) to illustrate different color blends.
- **Final Image Reconstruction:** Merges all three channels to recreate the full-color image.

## Kodun İşlevi (Türkçe)

Bu proje, OpenCV, NumPy ve Matplotlib kullanarak temel görüntü işleme tekniklerini göstermektedir. Kod aşağıdaki adımları uygular:

- **Görüntü Okuma:** OpenCV kullanılarak `cat.jpg` dosyasından görüntü gri tonlarda okunur.
- **Kanal Ayrımı:** Gri tonlardaki görüntü, dikey olarak üç eşit parçaya bölünerek Mavi (B), Yeşil (G) ve Kırmızı (R) kanalları simüle edilir.
- **Kanal Görselleştirme:** Matplotlib kullanılarak her kanal, farklı renk haritalarıyla görselleştirilir:
  - Mavi kanal için `Blues` renk haritası,
  - Yeşil kanal için `Greens` renk haritası,
  - Kırmızı kanal için `Reds` renk haritası.
- **Kanal Birleştirme:** Farklı renk karışımlarını göstermek amacıyla, kanal çiftleri (R+B, G+B, R+G) birleştirilir.
- **Nihai Görüntü Oluşturma:** Son olarak, üç kanal birleştirilerek tam renkli görüntü yeniden oluşturulur.
