#Note

2026-07-27

Tags: [[CV]], [[Bewerbung]], [[Post Bachelor]], [[Finn Hertsch]], [[Research Experience]]
#post-bachelor #cv #research #publications

---

# Curriculum Vitae – Finn Hertsch

**Wangen im Allgäu, Germany** | f.hertsch@gmx.de | +49 179 9374616 | [finn-hertsch.de](https://finn-hertsch.de) | [ORCID 0009-0004-1692-8134](https://orcid.org/0009-0004-1692-8134)

**Research Interests:** Representation learning & retrieval, numerically robust online learning, computer vision for planetary science, high-performance vector engines.

---

## Education

### B.Sc. Data Science and Artificial Intelligence (210 ECTS)
**DHBW Ravensburg**, Germany | *10/2024 – 2026 (expected)*
* **GPA:** 2.3 | Cooperative (dual) program combining rigorous academic coursework with applied industry practice.
* **Focus Areas:** Advanced programming & systems engineering, machine learning, MLOps, distributed database architectures.
* **Capstone Project:** Hybrid article recommendation system for a regional media group, deployed on Google Cloud Platform (**Score: 97/100**).

### Abitur (General University Entrance Qualification)
**Edith-Stein-Schule Ravensburg**, Germany | *2021 – 2024*
* **Focus Subject:** Biotechnology | **Final Grade:** 2.0
* **Bioinformatics Coursework:** Sequence alignment and database search using BLAST and FASTA algorithms.
* **Practicals:** GFP reporter-gene transformation in *E. coli*; fermentative citric acid biosynthesis in a bench-scale bioreactor.

---

## Research Experience

### Luna — Planetary-Scale Lunar Pit Detection
*Independent research collaboration with Prof. Dr.-Ing. Mark Schutera, DHBW Ravensburg* | *2026 – ongoing*
* **Model Architecture:** Designed and trained **HOLE**, a DINOv3 ViT-S/16 backbone with a LoRA adapter and a custom Matryoshka DIVE loss for lunar surface representation learning.
* **Coverage Optimization Solver:** Built a coverage-optimization solver selecting a minimal set of LROC NAC images for ≥99% global lunar surface coverage across 7 latitude bands, processing over 20,000 images end-to-end.
* **Vector Database Engine (Pithos):** Designed and implemented **Pithos**, a GraalVM-native, CUDA-accelerated vector database serving as the retrieval backend, indexing over 125 million vectors at ~5.1 MB/product.
* **Planetary Pipeline:** Set up planetary image-processing infrastructure (ISIS3) and a full annotation/dataset pipeline for lunar surface segmentation, maintained as a public Hugging Face dataset.

### Kairos — Numerically Robust News Recommendation under Item Cold-Start
**DHBW Ravensburg**, Germany | *2026*
* **Numerical Stability:** Proposed a Cholesky-factor-based LinUCB update as a numerically stable alternative to Sherman–Morrison inversion for contextual bandits under sparse, high-churn data.
* **Adaptive Latency Retrieval:** Integrated Matryoshka Representation Learning for adaptive-latency candidate retrieval, achieving a **4.78× inference speedup** at <3.2% approximation error.
* **Live Deployment:** Validated the framework on live data from the Tagesschau API.

---

## Publications

* **F. Hertsch**, *“Kairos: Numerisch robuste News Recommendation unter Item-Cold-Start mit Cholesky-basiertem LinUCB.”* Submitted to SKILL 2026 (under review).

---

## Professional Experience

### Founder & Managing Director
**Hertsch Technologies UG (haftungsbeschränkt)**, Germany | *since 02/2026*
* Founded and lead a software company focused on automated data-processing pipelines and professional maintenance infrastructure.

### Dual-Study Practical Partner
**Waldner Holding**, Wangen, Germany | *2026 – 09/2027*
* Applied data science and software engineering work as part of the DHBW cooperative study program.

### Dual-Study Practical Partner
**Schwäbischer Verlag GmbH & Co. KG**, Ravensburg, Germany | *10/2024 – 06/2026*
* Developed a hybrid recommendation system (NCF & CBF) on Google Cloud Platform, deployed on Vertex AI.
* Built data pipelines processing user interaction data with BigQuery.
* Prototyped a multi-armed contextual bandit over high-dimensional article embeddings.

---

## Technical Skills

* **Programming:** Python, Java, SQL, C++/CUDA concepts.
* **ML & Data Science:** PyTorch (DINOv3, LoRA), MLOps (DASC-PM), Matryoshka Representation Learning, Contextual Bandits, Vector Search / ANN.
* **Cloud & Infrastructure:** Google Cloud Platform (Vertex AI, BigQuery), GraalVM, CUDA, FastAPI, PowerBI, ISIS3.

---

## Languages

* **German:** Native
* **English:** Professional / Academic (B2/C1)
* **Spanish:** Intermediate (B1)
