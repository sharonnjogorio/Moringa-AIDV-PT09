# BPM Song Tempo Classifier

A Python project that detects the BPM of an audio file and classifies it into a genre-based tempo category using the Librosa library.

---

## Requirements

- Python 3.8+
- Google Colab or any local Python environment

---

## Installation

```bash
pip install librosa numpy
```

---

## How to Run

**Colab:** Open `bpm_classifier.ipynb` and run all cells top to bottom.

**Local:**
```bash
git clone https://github.com/sharonnjogorio/Moringa-AIDV-PT09.git
cd bpm_classifier
pip install librosa numpy
python bpm_classifier.py
```

---

## Genre Categories

| Category          | BPM Range | Examples                       |
|-------------------|-----------|--------------------------------|
| Slow / Ballad     | Below 80  | Lo-fi, Gospel, Slow Jams       |
| Pop / R&B         | 80 – 119  | Afropop, R&B, Reggae           |
| Dance / Hip-hop   | 120 – 149 | Hip-hop, Dancehall, House      |
| EDM / High Energy | 150+      | EDM, Drum & Bass, Amapiano     |

---

## Expected Output

```
  BPM Classifier Result
  Audio file   : nutcracker
  Detected BPM : 108
  Genre        : Pop / R&B — Afropop, R&B, Reggae
```

---

## Project Structure

```
bpm_classifier/
├── bpm_classifier.ipynb   ← Colab notebook
├── README.md              ← This file
└── toolkit.md             ← Capstone Toolkit Document
```
