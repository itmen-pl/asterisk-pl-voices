# 🇵🇱 Asterisk Polish Sounds (Multi-Voice Edition) / Polskie Komunikaty Głosowe dla Asterisk PBX

[![License: Dual MIT / CPML](https://img.shields.io/badge/License-Dual%20MIT%20%2F%20CPML-blue.svg)](LICENSE)
[![Asterisk](https://img.shields.io/badge/Asterisk-Compatible-orange.svg)](https://www.asterisk.org/)
[![Codecs](https://img.shields.io/badge/Codecs-ALAW%20%7C%20G.722%20%7C%20WAV-brightgreen.svg)]()
[![Voices](https://img.shields.io/badge/Voices-5%20Variants-purple.svg)]()
[![Use](https://img.shields.io/badge/Audio%20Usage-Non--Commercial-yellow.svg)](LICENSE)

[🇵🇱 Polski](#-polski) | [🇬🇧 English](#-english)

---

<a name="-polski"></a>
## 🇵🇱 POLSKI

Nowoczesny zestaw polskich komunikatów głosowych dla centrali **Asterisk PBX** oraz systemów pokrewnych (**FreePBX, Issabel, PBX In A Flash, VoIP**).

Projekt powstał w celu zastąpienia przestarzałych nagrań wysokiej jakości komunikatami wygenerowanymi przez neuronowe modele syntezy mowy (**Coqui XTTS v2**). Wszystkie komunikaty posiadają poprawioną fonetykę akronimów (`PIN`, `IVR`, `PBX`, `ID`) oraz naturalne, biznesowe brzmienie przygotowane przy wsparciu modeli językowych.

Repozytorium udostępnia architekturę **Multi-Voice** – do wyboru jest **5 wariantów lektorskich** (męskie, damskie oraz stylizowany robot AI).

### 🎙️ Dostępne głosy

| Głos | Model / Źródło | Barwa / Charakterystyka | Rekomendowane zastosowanie |
| :--- | :--- | :--- | :--- |
| **`darek`** *(domyślny)* | **XTTS v2** (własny lektor) | Naturalny, męski, pewny siebie i zdecydowany | Centrale biurowe, działy techniczne, B2B |
| **`bernard`** | **XTTS v2** (własny lektor) | Niski, głęboki, ciepły i elegancki bas radiowy | Finanse, kancelarie, prestiżowe infolinie |
| **`carla`** | **XTTS v2** (syntetyk hybrydowy) | Nowoczesny, melodyjny i ciepły damski lektor | Obsługa klienta, infolinie, recepcje |
| **`tomek`** | **XTTS v2** (syntetyk hybrydowy) | Przyjazny, radiowy i dynamiczny głos męski | Dział handlowy, wsparcie techniczne |
| **`cyborg`** | **DSP Modulator** (baza: Tomek) | Krystaliczny, nowoczesny syntezator robota / AI | Helpdesk IT, technologie, systemy automatyczne |

---

### 💎 Formaty audio – Zero Transcoding

Dla każdego z 716 komunikatów przygotowano równolegle 3 natywne formaty:
* **`.alaw`** (PCMA 8 kHz mono) – europejski standard telefonii stacjonarnej i komórkowej (PSTN, SIP G.711a).
* **`.g722`** (HD Voice 16 kHz mono) – szerokopasmowy dźwięk wysokiej wierności dla telefonów VoIP (Yealink, Cisco, Gigaset, Snom, Grandstream).
* **`.wav`** (PCM 8 kHz 16-bit mono) – bezstratny format referencyjny.

Dzięki obecności wszystkich trzech formatów centrala Asterisk automatycznie dobiera plik odpowiadający kodekowi używanemu przez rozmówcę, **całkowicie eliminując transkodowanie w procesorze (zero CPU overhead) i zapewniając krystalicznie czysty dźwięk**.

---

### ✨ Poprawki językowe i fonetyczne

* **Wymowa akronimów:** `PIN` wymawiany naturalnie jako *"pin"*, `PIN-u` -> *"pinu"*, `ID` -> *"identyfikator"*, `IVR` -> *"menu głosowe"*, `PBX` -> *"centrala telefoniczna"*, `IP` -> *"aj-pi"*.
* **Naturalne zwroty:** Wyeliminowano sztywne formułki (np. *„Dołączyłeś do pokoju jako pierwszy. Za chwilę rozpocznie się połączenie.”*, *„Wprowadź kod pin i zatwierdź krzyżykiem.”*, *„Jesteś pierwszy w kolejce. Twoje połączenie zostanie za chwilę odebrane.”*).
* **Czysty koniec fraz:** Wyeliminowano typowe dla modeli AI halucynacje końcowe (*tzw. „ponci/penti”*).
* Pełne porównanie starych i poprawionych fraz znajduje się w pliku [`poprawione-teksty-pl.txt`](poprawione-teksty-pl.txt).

---

### 🛠️ Wykorzystane narzędzia i technologie

Do stworzenia tego zestawu wykorzystano:
* **Ollama (LLM)** – korekta językowa i fonetyczna tekstów, przygotowanie naturalnych polskich tłumaczeń komunikatów.
* **Coqui XTTS v2** – neuronowa synteza mowy oparta o przygotowane, autorskie próbki głosów lektorskich (`darek`, `bernard`, `carla`, `tomek`).
* **FFmpeg / SoX** – cyfrowa obróbka dźwięku, filtry efektowe (głos `cyborg`) oraz bezstratne kodowanie do natywnych formatów telefonicznych (`.alaw`, `.g722`, `.wav`).

---

### 📁 Struktura plików

```text
asterisk-pl-voices/
├── voices/
│   ├── bernard/                  # Głos Bernard (2178 plików: alaw, g722, wav)
│   ├── carla/                    # Głos Carla (2178 plików: alaw, g722, wav)
│   ├── cyborg/                   # Głos Cyborg (2178 plików: alaw, g722, wav)
│   ├── darek/                    # Głos Darek (2178 plików: alaw, g722, wav) [DOMYŚLNY]
│   └── tomek/                    # Głos Tomek (2178 plików: alaw, g722, wav)
├── wszystkie-teksty-komunikatow.txt # Spis 730 fraz wraz z transkrypcją
├── poprawione-teksty-pl.txt      # Wykaz wprowadzonych poprawek językowych
├── core-sounds-pl.txt            # Słownik Asterisk (plik: treść)
├── LICENSE                       # Licencja projektu
└── README.md                     # Dokumentacja
```

---

### 📄 Licencja

Projekt stosuje podwójne licencjonowanie (**Dual-Licensing**):

1. **Pliki audio (`voices/`):**  
   Wygenerowane przy użyciu modelu **Coqui XTTS v2** na licencji **Coqui Public Model License (CPML) – wyłącznie do użytku niekomercyjnego (Non-Commercial)**.
   * ✅ **Dozwolone:** Użytek prywatny, homelab, centrale domowe, projekty edukacyjne, badawcze i hobbystyczne.
   * ❌ **Zabronione:** Odsprzedaż, bezpośrednie komercyjne wykorzystanie lub użycie w płatnych usługach komercyjnych bez licencji od właścicieli praw do modelu bazowego.

2. **Teksty i dokumentacja:**  
   Wszystkie listy tekstowe (`core-sounds-pl.txt`, `wszystkie-teksty-komunikatow.txt`, `poprawione-teksty-pl.txt`) oraz dokumentacja podlegają otwartej licencji **[MIT](LICENSE)**.

---
---

<a name="-english"></a>
## 🇬🇧 ENGLISH

A modern Polish sound prompt collection (**Asterisk Core Sounds PL**) for **Asterisk PBX**, **FreePBX**, **Issabel**, and other VoIP telephone systems.

Generated using neural speech synthesis (**Coqui XTTS v2**), this collection features natural Polish phonetics, corrected acronym pronunciations (such as PIN, PBX, IVR, IP), and natural business phrasing.

The project features a **Multi-Voice architecture** offering **5 distinct voice models** (male, female, and a futuristic sci-fi robot).

### 🎙️ Available Voice Packs

| Voice | Engine / Origin | Tone / Character | Recommended Use Case |
| :--- | :--- | :--- | :--- |
| **`darek`** *(default)* | **XTTS v2** (custom voice) | Confident, mature, authoritative male voice | Business PBX, technical support, B2B |
| **`bernard`** | **XTTS v2** (custom voice) | Deep, resonant, warm radio broadcast bass | Law firms, finance, VIP customer lines |
| **`carla`** | **XTTS v2** (hybrid synthetic) | Melodic, modern, welcoming female voice | Customer service, call centers, reception |
| **`tomek`** | **XTTS v2** (hybrid synthetic) | Friendly, engaging, broadcast male voice | Commercial support, sales lines |
| **`cyborg`** | **DSP Modulator** (Tomek base) | Crisp, metallic sci-fi robot synthesizer | IT helpdesk, gaming, automated systems |

---

### 💎 Audio Formats (Zero Transcoding)

All 716 prompts are encoded in 3 native telephone formats:
* **`.alaw`** (PCMA 8 kHz mono) – European PSTN, ISDN, and standard G.711a SIP calling.
* **`.g722`** (HD Voice 16 kHz mono) – Wideband high-definition audio for modern VoIP desk phones (Yealink, Cisco, Polycom, Grandstream, Snom).
* **`.wav`** (PCM 8 kHz 16-bit mono) – Uncompressed base audio format.

Asterisk automatically matches the caller's negotiated codec, **eliminating CPU transcoding overhead and ensuring optimal sound clarity**.

---

### 🛠️ Tools & Technologies Used

This sound pack was created using:
* **Ollama (LLM)** – linguistic and phonetic optimization of prompt transcripts, providing natural Polish phrasing.
* **Coqui XTTS v2** – advanced neural speech synthesis utilizing custom voice samples (`darek`, `bernard`, `carla`, `tomek`).
* **FFmpeg / SoX** – audio post-processing, DSP effects (`cyborg` voice), and conversion into native telephony formats (`.alaw`, `.g722`, `.wav`).

---

### 📁 Repository Structure

```text
asterisk-pl-voices/
├── voices/
│   ├── bernard/                  # Voice Bernard (2178 files: alaw, g722, wav)
│   ├── carla/                    # Voice Carla (2178 files: alaw, g722, wav)
│   ├── cyborg/                   # Voice Cyborg (2178 files: alaw, g722, wav)
│   ├── darek/                    # Voice Darek (2178 files: alaw, g722, wav) [DEFAULT]
│   └── tomek/                    # Voice Tomek (2178 files: alaw, g722, wav)
├── wszystkie-teksty-komunikatow.txt # Complete prompt list with transcripts (730 entries)
├── poprawione-teksty-pl.txt      # Phonetic and phrasing improvement list
├── core-sounds-pl.txt            # Dictionary source (filename: text)
├── LICENSE                       # License information
└── README.md                     # Bilingual Documentation
```

---

### 📄 License

This repository operates under a **Dual-Licensing model**:

1. **Audio Prompts (`voices/`):**  
   Synthesized using **Coqui XTTS v2** under the **Coqui Public Model License (CPML) – Non-Commercial Use Only**.
   * ✅ **Permitted:** Personal use, homelabs, private PBX systems, educational, research, and hobbyist projects.
   * ❌ **Prohibited:** Direct commercial exploitation, resale, or deployment in paid commercial services without authorization from the base model rights holders.

2. **Transcripts & Documentation:**  
   All textual lists (`core-sounds-pl.txt`, `wszystkie-teksty-komunikatow.txt`, `poprawione-teksty-pl.txt`) and documentation are released under the **[MIT License](LICENSE)**.
