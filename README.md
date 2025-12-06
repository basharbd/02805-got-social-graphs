# Network, Language, and Sentiment in *Game of Thrones* Season 1

This repository contains the full code, data processing pipeline, and report for my final project in the DTU course **02805 Social Graphs and Interactions**.

The goal of the project is to show how **social network analysis** and **classical NLP** can be combined to study the narrative structure and emotional tone of **Game of Thrones – Season 1** using the official script.

---

## 1. Project Overview

We build an **undirected, weighted character interaction network** from a public Season 1 script dataset:

- **Nodes** = characters (speakers).
- **Edges** = two characters speak in the same scene (weight = number of co-speaking events).
- We analyze:
  - Global structure (size, density, degree distribution, connectivity),
  - Centralities (degree, betweenness, eigenvector),
  - Louvain communities and their narrative interpretation,
  - Community-level **lexical themes** (TF–IDF) and
  - Community-level **sentiment** using the **LabMT happiness lexicon**.

The main research finding is that:

> **Network structure, word usage, and sentiment are tightly aligned with the narrative factions of Season 1**  
> (Starks in the North, King’s Landing politics, Night’s Watch at the Wall, and Daenerys’ Dothraki storyline).

---

## 2. Repository Structure

The repository is organized as follows:

```text
got-social-graphs/
├── dataset/
│   ├── Game_of_Thrones_Script.csv          # Raw Kaggle script data (Season 1–8)
│   ├── got_season1_script_clean.csv        # Cleaned Season 1 subset (generated)
│   └── LabMT_english.csv                   # LabMT happiness lexicon
│
├── notebook/
│   └── got_s1_network_text_sentiment.ipynb # Main analysis notebook
│
├── report/
│   ├── got_social_graphs_report.tex        # LaTeX source (PNAS template)
│   ├── got_social_graphs_report.pdf        # Final 5-page report
│   ├── fig_network.pdf                     # Figure 1: Season 1 network with communities
│   ├── fig_centralities.pdf                # Figure 2: Centrality rankings
│   ├── fig_wordclouds.pdf                  # Figure 3: Community wordclouds
│   └── fig_sentiment.pdf                   # Figure 4: LabMT sentiment per community
│
├── requirements.txt                        # Python dependencies
└── README.md                               # This file




---

## 3. Data

### 3.1 Script data (Kaggle)

The raw script data is from the Kaggle dataset:

> **“Game Of Thrones TV Series script data” by G. Gopinath**

Link: [https://www.kaggle.com/datasets/gokulnath007/game-of-thrones-tv-series-script-data](https://www.kaggle.com/datasets/gokulnath007/game-of-thrones-tv-series-script-data)

In this project we only use **Season 1**. If `Game_of_Thrones_Script.csv` is not present in `dataset/`, please download it from Kaggle and place it there.

### 3.2 LabMT sentiment lexicon

The **LabMT** happiness lexicon by Dodds et al. is provided as:

* `dataset/LabMT_english.csv`

Each word is assigned a happiness score in the range **1–9**, where:

* Around **5** ≈ neutral,
* > 5 ≈ more positive,
* < 5 ≈ more negative.

We drop neutral words (between 4 and 6) and compute mean **shifted** scores per community.

---

## 4. Installation

You can run the notebook in a fresh Python 3 environment.

### 4.1 Create and activate environment (optional)

```bash
python -m venv venv
source venv/bin/activate        # On macOS / Linux
# .\venv\Scripts\activate       # On Windows
```

### 4.2 Install dependencies

If `requirements.txt` is present:

```bash
pip install -r requirements.txt
```

Otherwise, you mainly need:

```bash
pip install networkx numpy pandas matplotlib nltk scikit-learn wordcloud
```

Plus any additional packages you normally use for plotting or Jupyter.

---

## 5. Reproducing the Analysis

1. **Clone or download** this repository.

2. Ensure the following files exist in `dataset/`:

   * `Game_of_Thrones_Script.csv`
   * `LabMT_english.csv`

3. Open the main notebook:

   ```text
   notebook/got_s1_network_text_sentiment.ipynb
   ```

4. Run all cells **from top to bottom**.
   The notebook will:

   * Clean the raw script,
   * Build the Season 1 network,
   * Compute centralities and Louvain communities,
   * Aggregate text per community and compute TF–IDF,
   * Compute LabMT sentiment per community,
   * Generate and save the figures listed below.

5. The figures saved to `report/` are:

   * `fig_network.pdf`
   * `fig_centralities.pdf`
   * `fig_wordclouds.pdf`
   * `fig_sentiment.pdf`

These are the figures used in the final report.





