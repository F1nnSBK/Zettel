#Note

2026-07-27

Tags: [[CV]], [[Bewerbung]], [[Post Bachelor]], [[Finn Hertsch]], [[Research Experience]], [[Julia]], [[Bandits]]
#post-bachelor #cv #research #publications #julia

---

# Curriculum Vitae – Finn Hertsch

**Wangen im Allgäu, Germany** | f.hertsch@gmx.de | +49 179 9374616 | [finn-hertsch.de](https://finn-hertsch.de) | [ORCID 0009-0004-1692-8134](https://orcid.org/0009-0004-1692-8134)

**Research Interests:** Representation learning & retrieval, numerically robust online learning, computer vision for planetary science, high-performance model-isomorphic database engines.

---

## Education

### B.Sc. Data Science and Artificial Intelligence (210 ECTS)
**DHBW Ravensburg**, Germany | *10/2024 – 09/2027 (expected)*
* **Current GPA:** 2.3 (CS Core Systems GPA: **1.5**) | Cooperative (dual) study program combining academic coursework with applied industry practice.
* **Focus Areas:** Advanced programming, theoretical computer science, machine learning, distributed architectures.
* **Project Work I (Projektarbeit 1):** Hybrid article recommendation microservice on Google Cloud Platform (**Grade: 1.0 / Score: 97/100**).
* *(Bachelor Thesis scheduled for 2027)*

### Abitur (General University Entrance Qualification)
**Edith-Stein-Schule Ravensburg**, Germany | *2021 – 2024*
* **Focus Subject:** Biotechnology | **Final Grade:** 2.0
* **Bioinformatics Coursework:** Sequence alignment and database search using BLAST and FASTA algorithms.
* **Practicals:** GFP reporter-gene transformation in *E. coli*; fermentative citric acid biosynthesis in a bench-scale bioreactor.

---

## Publication

**F. Hertsch** (2026): *"Kairos: Numerically Robust News Recommendation under Item Cold-Start via Cholesky-based LinUCB."*
arXiv preprint [arXiv:2607.26832](https://arxiv.org/abs/2607.26832) [cs.LG].
German version peer-reviewed and accepted at **SKILL 2026** (16. Studierendenkonferenz Informatik), Lecture Notes in Informatics (LNI), Gesellschaft für Informatik. Presented at INFORMATIK 2026, TU Dresden, September 2026. LNI proceedings & DOI forthcoming.

---

## Research Experience & Engineering Projects

### Kairos — Numerically Robust News Recommendation under Item Cold-Start (Julia)
**DHBW Ravensburg**, Germany | *2026* | **Published: [arXiv:2607.26832](https://arxiv.org/abs/2607.26832) | Accepted: SKILL 2026 (LNI)**
* **Numerical Stability & Cholesky Updates:** Developed **Kairos** in **Julia**, substituting error-prone Sherman-Morrison matrix inversion with direct rank-1 updates of Cholesky factors (`cholupdate`) in contextual Linear Upper Confidence Bound (LinUCB) bandits, preserving SPD matrix structure and preventing condition number divergence under sparse item cold-start settings (TTL < 48h).
* **Monte Carlo Stability Verification:** Validated numerical resilience across 1,000 Monte Carlo simulation runs, proving zero error variance in Cholesky updates compared to explosive divergence in traditional inversion.
* **Adaptive MRL Retrieval Subspace:** Integrated Matryoshka Representation Learning (MRL) for Maximum Inner Product Search (MIPS) candidate retrieval, reducing embedding dimensionality from 768d to 128d to achieve a **4.78x inference speedup** (0.065 ms / 100 items vs 0.312 ms) with an MAE of 0.032 (retaining >96.8% semantic structure).
* **Live Streaming Validation:** Deployed and benchmarked using live data from the Tagesschau API.

### Production-Grade Hybrid Recommendation Microservice (Project Work I)
**DHBW Ravensburg / Schwäbisch Media** | *2025* | **Grade: 1.0 (Score: 97/100)**
* **Cloud-Native Microservice Architecture:** Engineered an asynchronous FastAPI (ASGI) microservice on Google Cloud Platform orchestrating parallel prediction pipelines across Vertex AI Vector Search (3072d embeddings, MIPS) and Neural Collaborative Filtering (NCF / MLP).
* **Bayesian Hyperparameter Optimization:** Implemented a Tree-structured Parzen Estimator (Optuna TPE) search across 515,000 candidate evaluations (515 trials over 1,000 users), identifying an optimal 0.7226 / 0.2774 CBF-CF score-fusion equilibrium.
* **Rigorously Unbiased Evaluation:** Evaluated performance under a Leave-Last-Out Full-Catalog Ranking protocol over 2.3M users and 104k items (<0.005% matrix density), proving a **5.4x nDCG@10 improvement** over baseline models at a 95th-percentile latency of 1562 ms (SLO < 2000 ms).

### Planetary Remote Sensing Representation Learning (Ongoing Research)
*Research collaboration with Prof. Dr.-Ing. Mark Schutera, DHBW Ravensburg* | *2026 – ongoing*
* **Domain Exploration:** Investigating self-supervised representation learning and compact vector embeddings for planetary surface imagery (Lunar Reconnaissance Orbiter / LROC NAC data).
* **Data Processing Pipeline:** Developing ingestion and preprocessing workflows using USGS ISIS3 and PyTorch to support multi-resolution planetary imagery analysis.

---

## Professional Experience

### Founder & Managing Director
**Hertsch Technologies UG (haftungsbeschraenkt)**, Germany | *since 02/2026*
* Founded and lead a software company focused on automated data-processing pipelines and professional maintenance infrastructure.

### Dual-Study Industry Partner
**Waldner Holding**, Wangen, Germany | *2026 – 09/2027*
* Applied data science and software engineering work as part of the DHBW cooperative study program.

### Dual-Study Industry Partner
**Schwäbisch Media (Schwäbischer Verlag)**, Ravensburg, Germany | *10/2024 – 06/2026*
* Developed and deployed a hybrid recommendation microservice (NCF & CBF) on Google Cloud Platform (Vertex AI, BigQuery).
* Designed data ingestion pipelines processing high-volume user interaction logs with BigQuery.

---

## Technical Skills

* **Programming:** Julia, Python, Java, SQL, C/C++.
* **ML & Scientific Computing:** Contextual Bandits (LinUCB), Matryoshka Representation Learning (MRL), Neural Collaborative Filtering (NCF), PyTorch, Optuna (TPE), Vector Search (Vertex AI Vector Search), Julia Scientific Computing (`BenchmarkTools.jl`).
* **Cloud & Systems Engineering:** Google Cloud Platform (Vertex AI, BigQuery), FastAPI (ASGI), Docker, Linux, Git, USGS ISIS3.

---

## Languages

* **German:** Native
* **English:** Professional / Academic (B2/C1)
* **Spanish:** Intermediate (B1)
