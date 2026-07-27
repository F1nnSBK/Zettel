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
**DHBW Ravensburg**, Germany | *10/2024 – 2026 (expected)*
* **GPA:** 2.3 | Cooperative (dual) program combining academic coursework with applied industry practice.
* **Focus Areas:** Advanced programming & systems engineering, machine learning, MLOps, distributed database architectures.
* **Capstone Project:** Hybrid article recommendation system on Google Cloud Platform (**Score: 97/100**).

### Abitur (General University Entrance Qualification)
**Edith-Stein-Schule Ravensburg**, Germany | *2021 – 2024*
* **Focus Subject:** Biotechnology | **Final Grade:** 2.0
* **Bioinformatics Coursework:** Sequence alignment and database search using BLAST and FASTA algorithms.
* **Practicals:** GFP reporter-gene transformation in *E. coli*; fermentative citric acid biosynthesis in a bench-scale bioreactor.

---

## Research Experience & Engineering Projects

### The Lunar Surface as Continuous Latent Manifold (Lunar Embedding Dataset V1)
*Independent research collaboration with Prof. Dr.-Ing. Mark Schutera, DHBW Ravensburg* | *2026 – ongoing*
* **Planet-Scale Representation Learning:** Designed and trained **HOLE**, a self-supervised Vision Transformer (DINOv3 ViT-S/16) backbone specialized via Low-Rank Adaptation (LoRA) for extreme albedo variations and lunar geomorphology, indexing **326.43 million terrain vectors** across **57,265 LROC NAC products** for **99.1% global sub-meter moon coverage**.
* **Nested Multi-Branch Loss (MatryoshkaDIVELoss):** Formulated a joint loss combining a 384-dimensional primary Hinge Triplet Loss with sub-dimensional heads (64d, 128d, 256d) under head-wise NT-Xent contrastive loss, yielding **94.8% multi-query recall** upon dimensional truncation.
* **Model-Isomorphic Storage & 85.2x Compression (Pithos):** Implemented **Pithos**, an off-heap database layer aligning physical disk storage with nested embedding boundaries via zero-copy demand paging (`mmap`). Reduced raw 1,824 GB (1.82 TB) Float32 memory footprint down to a **21.4 GB offline SSD directory** (98.82% reduction) while keeping host RAM overhead **<8.5 GB** on a 128 GB LPDDR5x system.
* **Hardware Benchmark & Throughput:** Benchmark on an NVIDIA DGX Spark desktop AI platform (NVIDIA GB10 Grace Blackwell Superchip, 20-core Arm CPU, 128 GB LPDDR5x) demonstrated an end-to-end ingest throughput of **181.71 scenes/hour** (6.3x faster than ESSA baseline) with **1.42 ms mean retrieval latency**. Successfully reproduced confirmed structural collapses across Aristillus and Marius Hills configurations.

### Kairos — Numerically Robust News Recommendation under Item Cold-Start (Julia)
**DHBW Ravensburg**, Germany | *2026*
* **Numerical Stability & Cholesky Updates:** Developed **Kairos** in **Julia**, substituting error-prone Sherman-Morrison matrix inversion with direct rank-1 updates of Cholesky factors (`cholupdate`) in contextual Linear Upper Confidence Bound (LinUCB) bandits, preserving SPD matrix structure and preventing catastrophic condition number ($\kappa$) divergence under sparse data (TTL < 48h).
* **Monte Carlo Stability Verification:** Validated numerical resilience across 1,000 Monte Carlo simulation runs, proving zero error variance in Cholesky updates compared to explosive divergence in traditional inversion.
* **Adaptive MRL Retrieval Subspace:** Integrated Matryoshka Representation Learning (MRL) for Maximum Inner Product Search (MIPS) candidate retrieval, reducing embedding dimensionality from 768d to 128d to achieve a **4.78× inference speedup** (0.065 ms / 100 items vs 0.312 ms) with an MAE of 0.032 (retaining >96.8% semantic structure).
* **Live Streaming Validation:** Deployed and benchmarked using live data from the Tagesschau API.

### Production-Grade Hybrid Recommendation Microservice (Project Work I)
**DHBW Ravensburg / GCP Infrastructure** | *2025*
* **Cloud-Native Microservice Architecture:** Engineered an asynchronous FastAPI (ASGI) microservice on Google Cloud Platform orchestrating parallel prediction pipelines across Vertex AI Vector Search (3072d embeddings, MIPS) and Neural Collaborative Filtering (NCF / MLP).
* **Bayesian Hyperparameter Optimization:** Implemented a Tree-structured Parzen Estimator (Optuna TPE) search across 515,000 candidate evaluations (515 trials over 1,000 users), identifying an optimal 0.7226 / 0.2774 CBF-CF score-fusion equilibrium.
* **Rigorously Unbiased Evaluation:** Evaluated performance under a Leave-Last-Out Full-Catalog Ranking protocol over 2.3M users and 104k items (<0.005% matrix density), proving a **5.4× nDCG@10 improvement** over baseline models at a 95th-percentile latency of 1562 ms (SLO < 2000 ms).

---

## Publications & Manuscripts

* **F. Hertsch**, M. Schutera, *"The Lunar Surface as Continuous Latent Manifold."* Manuscript in preparation (2026).
* **F. Hertsch**, *"Kairos: Numerisch robuste News Recommendation unter Item-Cold-Start mit Cholesky-basiertem LinUCB."* Submitted to SKILL 2026 (under review).

---

## Professional Experience

### Founder & Managing Director
**Hertsch Technologies UG (haftungsbeschränkt)**, Germany | *since 02/2026*
* Founded and lead a software company focused on automated data-processing pipelines and professional maintenance infrastructure.

### Dual-Study Industry Partner
**Waldner Holding**, Wangen, Germany | *2026 – 09/2027*
* Applied data science and software engineering work as part of the DHBW cooperative study program.

### Dual-Study Industry Partner
**Media Publishing Partner**, Ravensburg, Germany | *10/2024 – 06/2026*
* Developed and deployed a hybrid recommendation microservice (NCF & CBF) on Google Cloud Platform (Vertex AI, BigQuery).
* Designed data ingestion pipelines processing high-volume user interaction logs with BigQuery.

---

## Technical Skills

* **Programming:** Julia, Python, Java, SQL, C++/CUDA.
* **ML & Data Science:** PyTorch (DINOv3, LoRA), Contextual Bandits (LinUCB), Matryoshka Representation Learning (MRL/DIVE), Neural Collaborative Filtering (NCF), MLOps (DASC-PM, Optuna TPE), Vector Search / MIPS (Vertex AI Vector Search).
* **Cloud & Systems:** Google Cloud Platform (Vertex AI, BigQuery), GraalVM, CUDA, NVIDIA GB10 Grace Blackwell, Julia High-Performance Scientific Computing (`BenchmarkTools.jl`), FastAPI (ASGI), PowerBI, ISIS3.

---

## Languages

* **German:** Native
* **English:** Professional / Academic (B2/C1)
* **Spanish:** Intermediate (B1)
