# 01 — TF-IDF Anatomisi: Temelden Limitlerine

TF-IDF'i sıfırdan ele alan, hem saf Python ile hem de `scikit-learn` ile uygulayan; ardından yöntemin gerçek dünyadaki sınırlarını (anlamsal körlük, kelime sırası kaybı, seyreklik, boyut laneti) somut örneklerle gösteren bölüm. Örnekler ağırlıklı olarak sistem/log verileri üzerinden kurgulanmıştır.

## İçerik

Script adım adım ilerler:

1. **Kütüphanelerin yüklenmesi** – Gerekli importlar.
2. **Temel Python uygulaması** – TF, IDF ve TF-IDF'in elle, kütüphanesiz hesaplanması.
3. **Scikit-learn ile TF-IDF** – `TfidfVectorizer` ile aynı işin yapılması ve sonuçların `DataFrame` üzerinde gösterilmesi.
4. **Görselleştirme** – TF-IDF matrisinin ısı haritası (heatmap).
5. **TF-IDF'in limitleri ve sektörel analiz**
   - 5.1 Anlamsal ilişki eksikliği (eş anlamlı kelimeler)
   - 5.2 Bağlam ve kelime sırası problemi
   - 5.3 Kısmi çözüm: N-Gram (Bigram) kullanımı
   - 5.4 Boyutlanabilirlik ve seyreklik (sparsity)
   - 5.5 Boyut laneti (curse of dimensionality)
6. **Yoğun vektör (dense embedding) ile karşılaştırma** – TF-IDF → SVD ile boyut indirgeme.
7. **Tüm limitlerin özeti ve çözüm yolları** – Hangi durumda TF-IDF, hangi durumda daha gelişmiş yöntemler.

> Bu bölümün 5. ve 7. kısımları, repodaki bir sonraki konu olan **kelime vektörlerine** (Word2Vec, GloVe, FastText) neden ihtiyaç duyulduğunu gösterir.

## Çalıştırma

Dosya Google Colab'dan dışa aktarılmıştır ve `display()` gibi notebook fonksiyonları içerir, bu yüzden bir **Jupyter / Colab** ortamında çalıştırılması önerilir.

Düz Python betiği olarak çalıştırmak isterseniz `display(...)` satırlarını `print(...)` ile değiştirmeniz yeterlidir:

```bash
python tf_idf_anatomy.py
```

> Not: 5. bölüm 10.000 satırlık bir log havuzu simüle eder; bu adım ve grafik çizimleri birkaç saniye sürebilir.

## Gereksinimler

Kök dizindeki `requirements.txt` bu bölüm için yeterlidir: `numpy`, `pandas`, `scikit-learn`, `scipy`, `matplotlib`, `seaborn`, `ipython`.
