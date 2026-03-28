# Tum Acik Kaynak Muzik/Uretim Modelleri

## Tam Liste (Deneme Icin)

### Music Generation (Metin/Melodi -> Muzik)

| Model | Kaynak | Kalite | Sure | Real-time | Lisans |
|-------|-------|-------|------|---------|-------|
| **MusicGen** | Meta/AudioCraft | Yuksek | ~60s | Hayir | CC |
| **MusicGen2** | Meta | Yuksek | ~60s | Hayir | CC |
| **Stable Audio Open** | Stability AI | Yuksek | 47s | Hayir | MIT |
| **YuE** | - | Cok Yuksek | Tam sarki | Hayir | - |
| **Magenta RealTime** | Google | Orta | Surekli | **EVET** | Apache |
| **Riffusion** | - | Orta | Surekli | **EVET** | - |
| **Jukebox** | OpenAI | Orta | 4dk | Hayir | MIT |
| **DiffRhythm** | - | Orta | - | Hayir | - |
| **MusicLDM** | - | Orta | - | Hayir | - |
| **SoundStorm** | Google | Yuksek | - | - | - |
| **VoiceBox** | Meta | Ses | - | - | - |
| **Moûsai** | - | Orta | - | - | - |

### Stem Separation (Sarki -> Parcalar)

| Model | Kaynak | Kalite | Stems | Lisans |
|-------|-------|-------|------|-------|
| **Demucs** | Facebook | **En Iyi** | 4/6 | MIT |
| **Demucs 4** | - | Cok Iyi | 4 | MIT |
| **Spleeter** | Deezer | Iyi | 4/5 | MIT |
| **Open-Unmix** | - | Orta | 4 | - |
| **SepFormer** | - | Iyi | 4 | - |

### Text-to-Audio (Metin -> Ses/SFX)

| Model | Kaynak | Kullanim | Lisans |
|-------|-------|---------|-------|
| **ACE-Step** | - | SFX/Ses | - |
| **AudioLCM** | - | SFX | - |
| **Amphion** | - | Coklu | - |
| **KittenTTS** | - | TTS | - |

### Vocal/Ses/Speech Synthesis

| Model | Kaynak | Kullanim | Lisans |
|-------|-------|---------|-------|
| **Coqui TTS** | - | TTS | - |
| **Orpheus-TTS** | - | TTS | - |
| **VibeVoice** | Microsoft | TTS | - |
| **Parler-TTS** | - | TTS | - |
| **RVC** | - | Ses donusturme | - |
| **RVC v2** | - | Ses donusturme | - |

### Audio Editing

| Model | Kaynak | Kullanim |
|-------|-------|---------|
| **ClearerVoice-Studio** | - | Gürültü azaltma |
| **GACELA** | - | Düzenleme |
| **Audio Inpainting Diffusion** | - | Doldurma |

### Audio Codec (Altyapi)

| Model | Kaynak | Lisans |
|-------|-------|-------|
| **EnCodec** | Meta | - |
| **SoundStream** | Google | - |

---

## Deneme Oncelik Sirasi

### 1. Real-time (Aninda sonuc)
1. Magenta RealTime (DAW eklentisi)
2. Riffusion

### 2. Hizli Uretim (< 2 dk)
1. MusicGen (Meta)
2. Stable Audio Open

### 3. Yuksek Kalite Uretim
1. YuE (Tam sarki)
2. MusicGen2

### 4. Stem Separation (Zaten var)
1. Demucs (en iyi)
2. Spleeter (kolay)

---

## Notlar

- **MusicGen** en yaygin kullanilan (AudioCraft ile)
- **Demucs** stem separation'da standart
- **Magenta RealTime** tek Gercek zamanli secenek
- **YuE** en yeni ve Suno'ya benziyor