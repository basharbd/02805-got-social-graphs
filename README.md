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
