# BPM Song Tempo Classifier — Getting Started with Librosa in Python

**Course:** Moringa School — Gen AI for Developers, 2026

---

## What the program does

Loads a built-in audio sample, detects its BPM using Librosa's beat tracking algorithm and classifies it into a genre-based tempo category. No external music files needed.

| Category          | BPM Range    | Genre Examples                 |
|-------------------|--------------|--------------------------------|
| Slow / Ballad     | Below 80     | Lo-fi, Gospel, Slow Jams       |
| Pop / R&B         | 80 – 119     | Afropop, R&B, Reggae           |
| Dance / Hip-hop   | 120 – 149    | Hip-hop, Dancehall, House      |
| EDM / High Energy | 150+         | EDM, Drum & Bass, Amapiano     |

---

## Requirements

- Python 3.8+
- Google Colab (recommended) or any local Python environment

---

## Setup & Installation

**Colab:** Run in the first cell:
```python
!pip install librosa
```

**Local:**
```bash
pip install librosa numpy
```

---

## How to Run

**Colab:** Open `bpm_classifier.ipynb`, run all cells top to bottom.

**Local:**
```bash
git clone https://github.com/YOUR-USERNAME/bpm-classifier.git
cd bpm-classifier
pip install librosa numpy
python bpm_classifier.py
```

---

## Expected Output

```

  BPM Classifier Result
  Audio file   : nutcracker
  Detected BPM : 108
  Genre        : Pop / R&B — Afropop, R&B, Reggae

```

> BPM values may vary slightly by Librosa version (the beat tracker is an estimator, not a precise counter)

---

## AI Prompt Journal

Built using **Claude (Anthropic)** at [claude.ai](https://claude.ai).

---

**Prompt 1**
> *"I am a junior software developer taking a Gen AI for Developers short course at Moringa School. I want to build a capstone project in Python that relates to machine learning. I am interested in music. Is there a Python library I can use to detect and categorise songs based on their BPM, and if so, what would a simple project using it look like?"*

**Response summary:** Claude identified Librosa as the best fit — a Python library purpose-built for music and audio analysis. It compared it against a simpler Pandas-based approach (classifying a pre-made BPM dataset from a CSV) and recommended Librosa because it involves real audio processing, qualifies as new technology under the capstone brief, and uses built-in audio samples so no external files are needed.

**Reflection:** Before this prompt I had no idea Librosa existed. The comparison between two options was helpful because it let me make an informed choice rather than just accepting the first suggestion. I chose Librosa because it felt closer to real ML work — actually analysing audio rather than filtering a spreadsheet.

---

**Prompt 2**
> *"Before you write anything, help me fully understand what the capstone project requires. Here are the full instructions from the student portal. Walk me through every section I need to submit and what each one actually means in practice"*

**Response summary:** Claude broke down the Toolkit Document section by section in plain language, translated the five marking criteria into practical terms, and clarified that the full submission is just three files, a Python script, a README and the Toolkit Document. It also flagged the AI Prompt Journal as the most commonly underestimated section and explained that the current conversation could itself be logged as evidence of AI-assisted learning.

**Reflection:** This prompt saved me a lot of confusion. Reading the brief alone I wasn't sure how detailed each section needed to be. Understanding the rubric before writing any code helped me focus.

---

**Prompt 3**
> *"I use Google Colab for Python. Please share the code in a format that works cell by cell in Colab, I want to type it out myself rather than copy-paste, so I can write my own comments. Also generate the help me draft out the README and Toolkit Documents."*

**Response summary:** Claude structured the code across seven Colab cells with a clear explanation of what each cell does. It then generated a draft README and Toolkit Document covering all eight required sections from the capstone brief.

**Reflection:** Asking for cell-by-cell formatting rather than one big script made a real difference. Typing each cell out and running it one at a time helped me understand the flow, especially seeing the intermediate output after the BPM detection step before the classification ran.

---

**Prompt 4**
> *"I want the genre categories to feel more descriptive and music-focused, instead of labels like 'Moderate' or 'Upbeat', can we use genre-based labels that also give examples of the types of music that fall in each BPM range? Ideally something relevant to the kind of music people listen to in East Africa."*

**Response summary:** Claude updated the `classify_tempo()` function to return genre-based labels with regional examples, for instance "Pop / R&B — Afropop, R&B, Reggae" and "EDM / High Energy — EDM, Drum & Bass, Amapiano", and updated all associated files to match.

**Reflection:** This was a good example of using AI to refine rather than just generate. The first version worked but felt generic. Asking for culturally relevant examples made the output feel like mine. It also demonstrated that prompting is iterative — small refinements to what you ask lead to meaningfully different results.

---

**Prompt 5**
> *"I ran Cell 4 and got this warning: DeprecationWarning: Conversion of an array with ndim > 0 to a scalar is deprecated, and will error in future. Ensure you extract a single element from your array before performing this operation. The BPM still printed as 108, is this a problem, and how do I fix it?"*

**Response summary:** Claude explained that newer versions of Librosa return `tempo` as a one-element NumPy array rather than a plain scalar, so calling `float(tempo)` directly triggers the warning. The fix is to index into the array first: `float(tempo[0])`. The same change applies to `tempo2` in Cell 7. Claude also suggested logging this as a Prompt Journal entry since it demonstrates real testing and iteration.

**Reflection:** The code still ran,108 BPM printed correctly, but understanding *why* the warning appeared taught me something about how NumPy arrays work that I wouldn't have learned if I had just ignored it. The fix was a single character (`[0]`) but the understanding behind it was more valuable than the fix itself.

---

## Common Issues & Fixes

**`ModuleNotFoundError: No module named 'librosa'`**
Run `!pip install librosa` and restart the Colab runtime via Runtime → Restart runtime.

**DeprecationWarning on `float(tempo)`**
```python
bpm = round(float(tempo[0]))   # use tempo[0], not tempo
```

**BPM output is 0 or unexpectedly low**
Try a different built-in sample — `'brahms'`, `'choice'`, or `'fishin'`.

**Colab session disconnects**
Re-run the install cell first, then all cells from the top. Variables reset when a session ends.

---

## Limitations

BPM alone does not determine genre. This classifier uses tempo as a proxy for genre-typical BPM ranges — a song at 125 BPM could be hip-hop, house, or afrobeats. In a production system, additional features like MFCCs, spectral centroid, and rhythm patterns would be used alongside BPM for more accurate classification.

---

## References

- [Librosa documentation](https://librosa.org/doc/latest/index.html)
- [librosa.beat.beat_track() reference](https://librosa.org/doc/latest/generated/librosa.beat.beat_track.html)
- [Music and Audio Analysis in Python — Real Python](https://realpython.com/python-music-analysis-librosa/)

---

## Project Structure

```
bpm-classifier/
├── bpm_classifier.ipynb   ← Colab notebook
├── README.md              ← This file
└── toolkit.md             ← Capstone Toolkit Document
```

