# Açık Kaynak Ses Stem Ayrıştırma (Music Source Separation) Araçları

> Araştırma tarihi: Mart 2026

---

## 1. Demucs

**Geliştiren:** Facebook Research (Meta) → Şu an forks olarak sürdürülüyor  
**GitHub:** [facebookresearch/demucs](https://github.com/facebookresearch/demucs) (9.9k⭐)  
**Fork:** [adefossez/demucs](https://github.com/adefossez/demucs) (2.5k⭐)  
**Lisans:** MIT

### Ne Yapar?
Ses stem'lerini (vokal, davul, bas, enstrüman) waveform domain'de işleyerek ayırır. Hybrid spectrogram + waveform yaklaşımı kullanır.

### Güçlü Yönleri
- **En yüksek kalite:** 2024-2025'te açık kaynak arasında en iyi sonuç
- **Aktif geliştirme:** Facebook durdurdu ama topluluk fork'ları devam ediyor
- **Birden fazla stem:** 4 stem (vocals, drums, bass, other) + isteğe bağlı 2 stem daha
- **HTDemucs variant:** daha yüksek kalite için

### Dezavantajları
- **Yüksek donanım gereksinimi:** GPU önerilir, CPU çok yavaş
- **Büyük modeller:** ~1GB VRAM
- **Karmaşık kurulum:** TensorFlow/PyTorch bağımlılıkları

---

## 2. Spleeter (Deezer)

**Geliştiren:** Deezer Research  
**GitHub:** [deezer/spleeter](https://github.com/deezer/spleeter) (28k⭐!)  
**Lisans:** MIT

### Ne Yapar?
Deezer'in 2019'da yayınladığı, TensorFlow tabanlı source separation kütüphanesi. Pretrained modeller ile gelir (2 stem, 4 stem, 5 stem seçenekleri).

### Güçlü Yönleri
- **Kurulumu kolay:** `pip install spleeter` tek komut
- **Hızlı:** GPU ile gerçek zamanlı yakın performans
- **Çok popüler:** 28k yıldız, geniş topluluk
- **Dokümantasyon:** Wiki, örnekler, tutorial bol

### Dezavantajları
- **Eskimiş:** 2022'den beri aktif geliştirme yok
- **Kalite:** Demucs'a göre daha düşük kalite
- **TensorFlow:** PyTorch'a göre daha az esnek
- **Artefaktlar:** Vokal kalıntısı (bleeding) sorunu

> **Durum:** 2026'da artık "deprecated" kabul ediliyor. Geliştirme durdu.

---

## 3. Open-Unmix

**Geliştiren:** SigSep (Araştırma grubu)  
**GitHub:** [sigsep/open-unmix-pytorch](https://github.com/sigsep/open-unmix-pytorch) (1.5k⭐)  
**Lisans:** MIT

### Ne Yapar?
PyTorch tabanlı, müzik source separation için referans implementasyon. STEMS dataset'i üzerinde eğitilmiş.

### Güçlü Yönleri
- **PyTorch:** Modern derin öğrenme framework
- **Modüler:** Kendi modelini eklemek kolay
- **Araştırma odaklı:** SiSEC benchmark sonuçları yayınlanmış
- **Hızlı:** CPU'da bile kabul edilebilir

### Dezavantajları
- **Geliştirme:** Aktif ama yavaş
- **Stem sayısı:** Sadece 4 stem (vocals, drums, bass, other)
- **Kalite:** Demucs'ın gerisinde

---

## 4. Diğer Açık Kaynak Alternatifler

| Araç | Açıklama | Durum |
|------|----------|-------|
| **MDX-Net** | Demucs benzeri, spectrogram tabanlı | Aktif |
| **Wave-U-Net** | Waveform domain U-Net | Geliştirme durmuş |
| **SSAST** | Self-supervised audio source separation | Araştırma aşamasında |
| **DCCRN** | Convolutional recurrent network | Sınırlı stem desteği |

---

## Karşılaştırma Özeti

| Özellik | Demucs | Spleeter | Open-Unmix |
|---------|--------|----------|------------|
| **Kalite** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Hız** | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Kurulum** | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Geliştirme** | Topluluk | Durdu | Aktif |
| **Son güncelleme** | 2024 | 2022 | 2024 |

---

## Öneri

- **En iyi kalite için:** `adefossez/demucs` fork'u (HTDemucs modeli)
- **Kolay başlangıç için:** Spleeter (ama kalite düşük)
- **Araştırma için:** Open-Unmix (PyTorch, modüler)

**2026'da en popüler ve önerilen:** Demucs (HTDemucs 6 stem). Spleeter artık kullanılmıyor denebilir — kalite açığını kapatmak için geliştirme durdu.

---

## Kaynaklar

- https://github.com/facebookresearch/demucs
- https://github.com/deezer/spleeter
- https://github.com/sigsep/open-unmix-pytorch
- https://stemsplitter.github.io/demucs-vs-spleeter/