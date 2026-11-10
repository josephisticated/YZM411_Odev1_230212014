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

- [`YZM411_Odev1_Renk_Aydinlatma_Ornekleme_duzenlenmis.ipynb`](./YZM411_Odev1_Renk_Aydinlatma_Ornekleme.ipynb)

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



```text
YZM411_Odev1_OgrenciNo/
├── YZM411_Odev1_Renk_Aydinlatma_Ornekleme_duzenlenmis.ipynb
├── rapor.pdf
├── sonuc_tablosu.csv
└── README.md
```

## Yapay zekâ beyanı

Bu notebook’un düzenlenmesi ve açıklamalarının oluşturulması sırasında
Copilot kullanılmıştır.
