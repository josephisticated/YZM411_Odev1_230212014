# YZM 411 — Renk, Aydınlatma ve Örnekleme

Bu çalışma, aynı masaüstü sahnesinin farklı aydınlatma koşullarında nasıl
değiştiğini ve görüntü küçültmenin ayrıntı kaybına etkisini inceler.

## İçerik

- Görüntünün sayısal yapısının incelenmesi
- BGR ve RGB kanal sıralarının karşılaştırılması
- Sabit RGB ve HSV eşikleriyle renk maskesi oluşturma
- Normal ışık, gölge ve farklı lamba koşullarının karşılaştırılması
- Parlaklık kaydırması ve gama dönüşümü
- `1/4` oranında küçültme ve yeniden büyütme
- Ölçüm tabloları ve deney sonuçlarının yorumlanması

## Dosya

- [`YZM411_Odev1_Renk_Aydinlatma_Ornekleme_duzenlenmis.ipynb`](./YZM411_Odev1_Renk_Aydinlatma_Ornekleme_duzenlenmis.ipynb)

## Gereksinimler

- Python 3.9 veya üzeri
- Jupyter Notebook veya Google Colab
- NumPy
- OpenCV
- Matplotlib
- Pandas
- IPython

Kurulum:

```bash
pip install numpy opencv-python matplotlib pandas ipython jupyter
```

## Veri hazırlama

Notebook üç fotoğraf bekler:

```text
normal.jpg
golge.jpg
lamba.jpg
```

Dosya yolları notebook’un ilk kod hücresindeki `IMAGE_PATHS` sözlüğünden
değiştirilebilir:

```python
IMAGE_PATHS = {
    "normal": Path("normal.jpg"),
    "golge": Path("golge.jpg"),
    "lamba": Path("lamba.jpg"),
}
```

Fotoğraflar hazırlanırken:

1. Aynı nesne ve kamera konumu korunmalıdır.
2. Bir fotoğraf normal ışıkta, biri gölgede, biri farklı bir lamba altında
   çekilmelidir.
3. Renkli bir nesne, beyaz veya gri bir yüzey ve yazı/çizgi dokusu aynı sahnede
   bulunmalıdır.
4. Otomatik pozlama veya beyaz dengesi kullanılıyorsa raporda belirtilmelidir.
5. Fotoğraflarda tanınabilir kişiler bulunmamalıdır.

## Çalıştırma

Notebook hücrelerini yukarıdan aşağıya sırayla çalıştırın.

Çalıştırmadan önce aşağıdaki alanları kendi verinize göre güncelleyin:

- `IMAGE_PATHS`
- `SAMPLE_POINTS`
- `RGB_LOWER` ve `RGB_UPPER`
- `HSV_LOWER` ve `HSV_UPPER`

Renk eşikleri yalnızca normal ışık görüntüsünde belirlenmeli, daha sonra üç
koşul için değiştirilmemelidir. Böylece aydınlatma koşulları adil biçimde
karşılaştırılır.

## Deneyler

### 1. Sayısal görüntü yapısı

Her görüntü için aşağıdaki bilgiler raporlanır:

- Boyut: `H × W × C`
- Veri tipi
- Minimum ve maksimum piksel değeri
- Seçilen koordinatlardaki RGB değerleri
- NumPy’de `image[y, x, kanal]` erişimi
- OpenCV’nin BGR sırası ile RGB sırası arasındaki fark

### 2. RGB ve HSV maskeleri

Sabit eşikler üç görüntüye de uygulanır. Her koşul için:

- RGB maskesi
- HSV maskesi
- Seçilen piksel sayısı
- Maske alan oranı

hesaplanır.

> Maske alan oranı bir doğruluk ölçütü değildir. Sadece belirli eşiklerin
> görüntüde kaç piksel seçtiğini gösterir.

### 3. Parlaklık ve gama

Normal ışık görüntüsüne şu dönüşümler uygulanır:

```text
Parlaklık: J = clip(I + 40, 0, 255)
Gama 0.5:  J = 255 × (I / 255)^0.5
Gama 2.0:  J = 255 × (I / 255)^2.0
```

Her dönüşümden önce ortalama değerin nasıl değişeceği tahmin edilir ve
ölçümle karşılaştırılır.

### 4. Örnekleme

Görüntü genişlik ve yükseklik yönünde `1/4` oranına küçültülür:

- `cv2.INTER_NEAREST`
- `cv2.INTER_AREA`

Küçültülen görüntüler `INTER_NEAREST` ile tekrar büyütülür. Böylece yazı ve
ince çizgi gibi bilgilerin neden geri getirilemediği görsel ve sayısal olarak
incelenir.

## Raporlama

Rapor için aşağıdaki noktaları açıklayın:

- Her deneyden önce yapılan tahmin
- Tahmin ile ölçüm arasındaki fark
- “Ne gördüm, neden olabilir, nasıl kontrol ederim?” soruları
- En az bir tahminin neden tutmadığı
- Sarı bir arka planın neden hedef gibi seçilebileceği
- Büyütmenin kaybolan yazıyı neden geri getiremediği
- Otomatik pozlama ve beyaz dengesinin sınırlılıkları

Teslim paketinde tercihen şu dosyalar bulunmalıdır:

```text
YZM411_Odev1_OgrenciNo/
├── YZM411_Odev1_Renk_Aydinlatma_Ornekleme_duzenlenmis.ipynb
├── rapor.pdf
├── sonuc_tablosu.csv
└── README.md
```

## Yapay zekâ beyanı

Bu notebook’un düzenlenmesi ve açıklamalarının oluşturulması sırasında
Copilot kullanılmıştır. Kod hücreleri Python sözdizimi açısından kontrol
edilmiş, sonuçlar ise kullanıcının kendi fotoğraflarıyla yeniden
çalıştırılarak doğrulanmalıdır.

## Lisans ve kullanım

Bu çalışma eğitim amacıyla hazırlanmıştır. Kod ve açıklamalar, YZM 411
ödevi kapsamında kişisel deney sonuçlarıyla birlikte kullanılmalıdır.
