## Project 1: Analyzing "Blind Spots" in Vision Models and Generating Difference Descriptions

**Project Description:** The goal is to identify pairs of images that are visually distinct (as confirmed by **support models**) but appear identical or highly similar to a **base model**. In the final stage, students will use Vision Language Models (VLMs) to generate textual descriptions of the differences between these images.

### Phase 1: Configuration & Research

* **Environment Setup:** Initialize a repository using `uv`, `ruff`, `ty` (e.g., mypy/pyright), and `pyproject.toml`.
* **Methodology:** Document the proposed method for identifying these "blind spot" pairs.
* **Bonus (+2 pts):** Find and present a scientific paper that employs a similar approach.

### Phase 2: Vision Model Verification

* Build and demonstrate an analytical pipeline.
* Present comparative results for the **base model** versus both **support models**.
* **Exchange** base models with support models and show for each model the pairs that are visually distinct but appear similar to it.

### Phase 3: Textual Difference Descriptions (VLM)

* Extend the pipeline with models capable of describing images and present the generated text results.
* **Plan B:** If the group fails to generate suitable pairs in Phase 2, use the pre-existing **MMVP** dataset (HuggingFace).

### Resources

* **Phase 3 Reference:** [arXiv:2312.02974](https://www.google.com/search?q=https://arxiv.org/pdf/2312.02974)

**Datasets:**

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

## Project 2: Impact of Data Ranking Methods on the Training Process

**Project Description:** Students will analyze how a specific data importance ranking method (Method A or B) affects model training across different data subsets. The project requires comparing two approaches: training with a **frozen base model** (linear probe) and an **unfrozen base model**. In Phase 3, the experiment is repeated on a different architecture to test universality.

### Phase 1: Configuration & Theory

* **Repository Setup:** `uv`, `ruff`, `ty`, `pyproject.toml`.
* **Theoretical Analysis:** Study the assigned scientific paper and explain the mechanics of the ranking method.
* **Bonus (+2 pts):** Locate and present the original source code from the publication's authors.

### Phase 2: Implementation & First Architecture

* Build the training pipeline.
* Present results and analyze the rank similarity (correlation) between the two resulting datasets.
* **Base Model:** `torchvision.models.resnet50` (ResNet50_Weights.IMAGENET1K_V2)

### Phase 3: Transfer to New Architecture

* Repeat Phase 2 experiments to verify the method's consistency.
* **Base Model:** `torchvision.models.convnext_base` (ConvNeXt_Base_Weights.IMAGENET1K_V1)

### Resources

* **Dataset:** `frgfm/imagenette`

**Methods by Group:**

* **Group A**
* **Paper:** [arXiv:2405.15613](https://arxiv.org/pdf/2405.15613)
* **Ranking Logic:** Rank calculated based on the base model or a model from the DINOv2 family (`facebookresearch/dinov2` -> `dinov2_vitl14`).


* **Group B**
* **Paper:** [arXiv:2008.11600](https://arxiv.org/pdf/2008.11600)
* **Ranking Logic:** Rank calculated based on gradients during linear probe training or gradients of the entire model (base + linear probe).

---