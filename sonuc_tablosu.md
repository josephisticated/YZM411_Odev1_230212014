# YZM 411 Bilgisayarlı Görü - Ödev 1: Deney Sonuçları ve Veri Tablosu

Bu belge, deney boyunca kullanılan tüm parametrelerin ve elde edilen ham ölçüm değerlerinin özetini içermektedir.

## 1. Piksel İncelemesi (Koordinat: x=1500, y=2100)

| Aydınlatma Koşulu | Orijinal BGR Değerleri | Dönüştürülmüş RGB Değerleri |
| :--- | :--- | :--- |
| **Normal Işık** | [180, 197, 200] | [200, 197, 180] |
| **Gölge** | [183, 196, 198] | [198, 196, 183] |
| **Lamba (2700K)** | [143, 182, 210] | [210, 182, 143] |

## 2. Renk Eşikleri (Thresholds)

Hedef nesne (muz figürü) üzerinden belirlenen ve tüm fotoğraflara sabit olarak uygulanan sınır değerleri:

*   **RGB Alt Sınır:** `[36, 157, 207]`
*   **RGB Üst Sınır:** `[119, 230, 255]`
*   **HSV Alt Sınır:** `[95, 136, 207]`
*   **HSV Üst Sınır:** `[99, 211, 255]`

## 3. Maske Alan Oranları (%)

Yukarıdaki sabit eşikler uygulandığında hedef rengin tespit edildiği piksel sayısının toplam alana oranları:

| Aydınlatma Koşulu | RGB Maske Alanı Oranı | HSV Maske Alanı Oranı |
| :--- | :--- | :--- |
| **Normal Işık** | %1.01 | %0.03 |
| **Gölge** | %0.17 | %0.01 |
| **Lamba (2700K)** | %1.41 | %0.07 |

## 4. Uygulanan Dönüşüm ve Örnekleme Parametreleri

| İşlem Türü | Kullanılan Parametreler ve Yöntemler |
| :--- | :--- |
| **Parlaklık Kaydırması** | `b = +40`, `np.clip(img + 40, 0, 255)` (Float dönüşümü ile) |
| **Kırpılan Pikseller** | `(img_isik_float + 40) > 255`, Magenta `[255, 0, 255]` rengi ile işaretlendi. |
| **Gama Dönüşümü 1** | $\gamma = 0.5$ (Değerleri büyütüp parlattı) |
| **Gama Dönüşümü 2** | $\gamma = 2.0$ (Değerleri küçültüp kararttı) |
| **1/4 Küçültme (Alt Örnekleme)** | `fx=0.25`, `fy=0.25`, Interpolasyon: `cv2.INTER_NEAREST` ve `cv2.INTER_AREA` |
| **Yeniden Büyütme** | Hedef boyut: Orijinal `(W, H)`, Interpolasyon: `cv2.INTER_NEAREST` |
