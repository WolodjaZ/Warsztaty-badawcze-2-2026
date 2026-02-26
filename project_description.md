# 🛠️ Research Project Descriptions (2025/2026)

---

## 🔍 Project 1: Analyzing "Blind Spots" in Vision Models

**Goal:** Identify "hard" image pairs that fool a specific model (Base Model) into seeing them as identical, while other models (Support Models) correctly identify them as distinct. You will then use Vision Language Models (VLMs) to explain these differences.

### 🛰️ Phase 1: Configuration & Research

* **Environment Setup:** Initialize a repository using `uv`, `ruff`, `ty/mypy/pyright`, and `pyproject.toml`.
* **Methodology:** Document your proposed algorithm for finding "blind spot" pairs.
* **Bonus (+2 pts):** Find and present a scientific paper employing a similar evaluation approach.

### 🧪 Phase 2: Vision Model Verification

* **Pipeline:** Build an analytical pipeline that compares image embeddings.
* **Comparative Analysis:** Show results for the **Base Model** vs. **Support Models**.
* **Cross-Exchange:** Swap roles (e.g., make Group A's base model the support model) and show which pairs are "invisible" to each specific architecture.

### ✍️ Phase 3: Textual Difference Descriptions (VLM)

* **VLM Integration:** Use a VLM to generate text describing the differences between the identified pairs.
* **Plan B:** If Phase 2 fails to yield high-quality pairs, use the [MMVP Dataset](https://huggingface.co/datasets/MMVP/MMVP).

### 📚 Tech Stack & Resources

* **Reference:**
* [Learning Transferable Visual Models From Natural Language Supervision](https://arxiv.org/abs/2103.00020).
* [DINOv2: Learning Robust Visual Features without Supervision](https://arxiv.org/abs/2304.07193).
* [BLIP-2: Bootstrapping Language-Image Pre-training with Frozen Image Encoders and Large Language Models](https://arxiv.org/abs/2301.12597).
* [Blog: CLIP Vs DINOv2 in image similarity](https://medium.com/aimonks/clip-vs-dinov2-in-image-similarity-6fa5aa7ed8c6).

* **Datasets:**
* **Preferred:** `ILSVRC/imagenet-1k` + `pixparse/cc3m-wds` + `Caltech101`
* **Backup:** `timm/imagenet-22k-wds`

**Models:**

| Category | Group A | Group B |
| :--- | :--- | :--- |
| **Phase 2 Models** | `openai/clip-vit-base-patch16` | `facebook/dinov2-base` |
| | `google/siglip-base-patch16-224` | `facebook/dinov3-vitb16-pretrain-lvd1689m` |
| | `facebook/dinov2-base` | `facebook/vit-mae-base` |
| **Phase 3 (VLM)** | `Salesforce/blip2-opt-2.7b` | `meta-llama/Llama-3.2-3B-Instruct` |

---

## 📈 Project 2: Impact of Data Ranking on Training Dynamics

**Goal:** Investigate how data "importance" (calculated via specific ranking methods) affects the efficiency and performance of model training. You will compare the ranking consistency across different architectures.

### 🛰️ Phase 1: Configuration & Theory

* **Repository Setup:** `uv`, `ruff`, `ty/mypy/pyright`, `pyproject.toml`.
* **Theoretical Analysis:** Study the assigned paper and explain the mathematical logic behind the ranking (e.g., gradient-based or feature-based).
* **Bonus (+2 pts):** Locate and present the original source code from the publication's authors.

### 🏗️ Phase 2: Implementation & Baseline

* **Training Pipeline:** Compare training on the full dataset vs. subsets selected by your ranking method.
* **Comparison:** Test both **Frozen** (Linear Probe) and **Unfrozen** (Fine-tuning) base models.
* **Base Model:** `torchvision.models.resnet50` (ResNet50_Weights.IMAGENET1K_V2)

### 🔄 Phase 3: Transfer & Universality

* **Architecture Swap:** Repeat experiments on a modern transformer-based or conv-based architecture to see if the data "importance" remains consistent.
* **Base Model:** `torchvision.models.convnext_base` (ConvNeXt_Base_Weights.IMAGENET1K_V1)

### 📚 Methods by Group

* **Dataset:** `frgfm/imagenette` (A smaller, faster subset of ImageNet).

#### Group A: Representation-Based Ranking

* **Paper:** [What makes for a "good" Data Augmentation?](https://arxiv.org/abs/2405.15613)
* **Logic:** Ranking based on feature space density/distances using `DINOv2-ViT-L/14`.

#### Group B: Gradient-Based Ranking

* **Paper:** [Deep Learning on a Data Diet](https://arxiv.org/abs/2008.11600)
* **Logic:** Ranking calculated based on gradient norms during the early stages of training (Linear Probe vs. Full Model).

### 📚 Tech Stack & Resources

* **Reference:**
* [PyTorch Fine-tuning Tutorial](https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html)
* [Fine-tuning vs Linear Probing](https://openreview.net/pdf?id=UYneFzXSJWh)

---
