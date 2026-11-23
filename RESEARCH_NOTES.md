# MSAI6330 Computer Vision: Project Paper Selection Notes

Last updated: 2026-11-23

Legend: **[V]** = verified by web search this session. **[M]** = from memory / not confirmed, check before relying on it. **[!] DISCLAIMER** = I am not sure about the resource needs; test before committing.

---

## 1. Project brief (from `MSAI6330_project.pdf`, the official source)

Individual work, CVPR paper template.

| Item | Requirement |
|------|-------------|
| Paper | CVPR / ICCV / ECCV, published **2022-2026**, focused method that can be extended, feasible within the project period |
| Task | Critically review the paper, propose a modification/extension, implement it, evaluate against a baseline |
| Baseline | Official code or reproduced implementation. Official pretrained weights + adapted setup are OK if full reproduction is infeasible. Deviations must be documented |
| Hypothesis | At least one **measurable** research hypothesis |
| Results | Need not beat the original. Negative/inconclusive results are fine if rigorous |
| AI use | Must declare tool name + version, purpose, extent, and how outputs were verified |
| Submission | Code, configs, and results with the final report (reproducibility) |

**Deadlines**

| Date | Deliverable |
|------|-------------|
| **13 Dec 2026** | Stage 1: 1-page extended abstract (title/authors/venue/year, problem + motivation, main idea + contributions, initial limitations, initial modification idea) |
| 3 Jan 2027 | Stage 2: 5-page critical review (problem, method, critical analysis, research gap, proposed modification, experimental plan) |
| 9 Jan 2027 | Stage 3: 10-min milestone presentation |
| 30 Jan 2027 | Stage 4: 8-page report + code + 10-min presentation |

**Grading**: critical analysis 20%, gap/originality 20%, report 20%, presentations 20%, implementation + evaluation 15%, proposal 5%.

Course outline (`../MSAI6330_Outline_1261.pdf`) weights: Research Paper Analyses 15%, Project 35%, Assignments 20%, Final Exam 30%. Older Lecture-1 notes said project 20%; the outline's 35% is the official figure. How the project PDF's stages map onto the 15% / 35% split is not stated (see below), so confirm with the instructor. Follow the project PDF for deliverables and dates.  Professor's compute guidance: lightweight models, Colab-friendly, no training from scratch, pretrained inference/evaluation is fine.

## 1b. Requirements from the lectures (Notion, read 2026-11-23)

Sources: Lecture 1 (project and paper review), Lecture 5 (baselines and project guidance), Lecture 7 (project structure and schedule). Lectures 2, 3, 4 and 6 had no project instructions. Lecture 1 was only searched for project/paper-review content, not read in full.

**Research paper analysis (15%)**
- Pick one paper from CVPR / ICCV / ECCV (last 5 years preferred). Write a summary and a critical review: methodology, strengths, weaknesses, improvements. May include a class presentation. The same paper may be used for the project if done thoroughly (Lecture 1).
- From my own Notion to-do list: check whether the authors hid flaws, whether they really solved the claimed problem, and whether they showed only the good results. Read the reference papers and the code. Look for a review template (OpenReview / ICLR). The professor did not clearly name a template.

**Project**
- Paper with available code, light enough for Colab. One of: reproduce, re-evaluate with modifications, or apply a novel idea as an extension (Lecture 1). Training from scratch is **not** required; pretrained inference or fine-tuning is fine.
- **Baselines (Lecture 5)**: a **KNN baseline and a random baseline will be explicitly asked for**. The model must beat both; a model worse than random is unacceptable.
- **Vision-focused contribution (Lecture 5)**: image captioning is allowed only if the vision component is clear, not purely NLP evaluation.
- **Good contribution (Lecture 5)**: a motivated hypothesis, then an experiment, then validation. Not random tweaks. Valid types: reproduce and extend, combine two ideas, improve evaluation of under-studied work, propose a new task.
- **Experiments have two parts (Lecture 7)**: (1) hyperparameter analysis on pretrained models, (2) model design modifications. Failed experiments are welcome in the presentations.
- **Schedule (Lecture 7)**: choose the paper and idea within about 3 weeks of 21 Nov (about 12 Dec), then about 3 weeks to implement and experiment. Presentation 1 is 5 pages (idea and paper analysis); Presentation 2 is 8 pages, structured like a paper (abstract, introduction, methodology, results). Resources: single GPU / free Colab, pretrained models. Read about 3 papers a week.
- **Open conflict**: "3 weeks to implement" is shorter than the project PDF's 3 Jan to 30 Jan window (about 4 weeks after the milestone). Follow the PDF dates, but confirm with the instructor.
- Lecture 7 also asks me to rephrase any AI-written comparison text in Assignment 2. This lines up with the PDF's AI-use declaration.

**How each topic fits these lecture requirements**: see the "Fit with lecture requirements" line in each ranked entry below.

## 2. My constraints

- MacBook Pro M1 Pro, **16 GB RAM** (PyTorch MPS backend, no CUDA) **or** Google Colab free tier (T4-class GPU, limited session time).
- Individual project, about 10 weeks to final submission.
- Selection criteria: simple to understand, interesting, official code, public dataset, no heavy training.

---

## 3. Ranked topics (highest to lowest)

Ranking criteria: simple to understand, interesting, fits M1 16 GB / free Colab, official code + public dataset, room for a real extension. "Code improvement feasibility" is my estimate **before reading the repos** (I have not opened the code yet), so treat it as a hypothesis to check in the first feasibility run.

Summary:

| Rank | Topic | Paper(s) | Resource fit | Improvement feasibility |
|------|-------|----------|--------------|-------------------------|
| 1 | Test-time adaptation of CLIP | **TDA** (CVPR 2024) | Best | High |
| 2 | Training-free open-vocab segmentation | **ClearCLIP / SCLIP** (ECCV 2024, confirm venue) | Good [!] | Medium-high |
| 3 | Industrial anomaly detection | **PatchCore** (CVPR 2022) | Uncertain [!] | Medium-high |
| 4 | Retrieval-augmented / zero-shot captioning | **SmallCap / ConZIC** (CVPR 2023) | Uncertain [!] | Medium |
| 5 | Training-free few-shot CLIP adaptation | **Tip-Adapter** (ECCV 2022) | Best | Low-medium |
| 6 | Monocular depth estimation | **Depth Anything** (CVPR 2024) | Inference fine [!] | Unclear |

---

## Time and effort per topic (based on the PDF's stages and deadlines)

**Caveat**: the PDF fixes the deliverables and dates, not the hours. The hour figures below are **my own rough estimates** (not from the professor and not measured), so treat them as planning ranges to correct after the first feasibility run.

**Time available (from today, 2026-11-23)**: about 20 days to the proposal (13 Dec), about 6 weeks to the 5-page review (3 Jan), about 6.5 weeks to the milestone talk (9 Jan), and about 9.5 weeks to the final submission (30 Jan).

**Fixed workload, the same for every topic (about 55-65 h total)**

| PDF stage | Due | What it demands | Est. hours |
|-----------|-----|-----------------|-----------|
| 1. Proposal | 13 Dec | 1-page abstract: problem, idea, limitations, initial modification | 8-10 |
| 2. Critical review | 3 Jan | 5-page report: methodology, strengths/weaknesses, gap, proposed modification, experimental plan (hypothesis, baseline, datasets, metrics) | 15-20 |
| 3. Milestone talk | 9 Jan | 10-min talk + Q&A | 4-6 |
| 4. Final report + talk | 30 Jan | 8-page report (CVPR template), code + configs submitted, 10-min talk | 25-30 |

**Topic-specific workload (setup + baseline + implementation + experiments), estimated**

| Rank | Topic | Setup + baseline reproduction | Implement the modification | Experiments + ablations | Topic total | **Overall total** (with fixed ~60 h) | Effort level | Main schedule risk |
|------|-------|------|------|------|------|------|------|------|
| 1 | TDA | 6-10 h | 10-15 h | 10-15 h | 26-40 h | **~85-100 h** | Low-medium | Python 3.7 env on M1; ImageNet-scale runs (use a subset) |
| 2 | ClearCLIP / SCLIP | 8-15 h | 8-12 h | 10-20 h | 26-47 h | **~85-107 h** | Medium | Segmentation eval framework setup; large-resolution benchmarks |
| 3 | PatchCore | 8-20 h | 10-15 h | 12-25 h | 30-60 h | **~90-120 h** | Medium-high | CUDA-oriented code on M1; RAM for memory bank; 15 categories |
| 4 | SmallCap / ConZIC | 10-20 h | 10-20 h | 15-30 h | 35-70 h | **~95-130 h** | High | Datastore download size; slow sampling; metric tooling |
| 5 | Tip-Adapter | 4-8 h | 8-12 h | 8-12 h | 20-32 h | **~80-92 h** | Low | Less time on code, but more on justifying an original gap |
| 6 | Depth Anything | 4-8 h | 10-25 h | 10-25 h | 24-58 h | **~85-118 h** | Medium (wide range) | Unclear modification; evaluation data prep |

Spread over about 9.5 weeks, roughly 85-100 h is about **9-10 h/week** (TDA) and 120-130 h is about **13 h/week** (the heaviest options). Of the topics, TDA and Tip-Adapter leave the most slack for debugging and for the negative or inconclusive results the PDF explicitly allows.

**Suggested phasing against the PDF stages (TDA example; other topics shift hours between the first two rows)**

| Window | Work |
|--------|------|
| 23 Nov - 13 Dec | Read paper, run baseline on one small dataset, confirm venue, choose gap, write the 1-page abstract |
| 14 Dec - 3 Jan | Reproduce baseline on 2-3 datasets, read the code, write the 5-page critical review with the experimental plan |
| 4 - 9 Jan | Build the milestone talk, prototype the modification |
| 10 - 25 Jan | Implement the modification, run experiments and ablations, collect results |
| 26 - 30 Jan | Write the 8-page report, clean the code and configs, add the AI-use declaration, prepare the final talk |

---

### Rank 1. Test-time adaptation of vision-language models: TDA (CVPR 2024) **[V]**

**What it is**: Karmanov et al. keep a small key-value cache of confident test-image features with pseudo-labels (positive cache, plus a negative cache) and blend cache predictions with CLIP zero-shot logits. No gradients, frozen CLIP.

**What needs to be done**
1. Clone the official repo, set up the env (README targets Python 3.7 **[V]**, so expect dependency updates on M1).
2. Prepare 1-2 small datasets (Pets, Caltech101, Flowers, DTD, EuroSAT) following the repo's dataset instructions.
3. Reproduce zero-shot CLIP vs. TDA numbers on those datasets (baseline).
4. Pick one gap, state a measurable hypothesis, implement, run ablations, compare with the baseline.

**Strengths**
- Inference only, so it is the cheapest option here; fits M1 and free Colab.
- Very easy to explain (a cache of confident samples).
- Standard public datasets, official code, project page.
- Many natural gaps: eviction rule, class-imbalanced streams, thresholds, corruption robustness, latency and memory.

**Time / effort: about 26-40 h topic-specific, about 85-100 h overall (low-medium).** Setup 6-10 h, modification 10-15 h, experiments 10-15 h. Fits comfortably in the PDF timeline with slack. Estimate, not verified.

**Fit with lecture requirements: strong.** Random baseline is 1/num_classes and zero-shot CLIP is the natural reference. A KNN baseline (nearest-neighbour on CLIP image features with a few labelled samples) is easy to add and compares naturally to TDA's cache. The two-part experiment structure maps directly: (1) sweep cache size and thresholds, (2) change the eviction or fusion logic. Clearly vision-focused.

**Code improvement feasibility: High (to verify)**
- The change point is likely small and isolated (cache insert/update/eviction and the logit-fusion step), so modifications are cheap to implement and test.
- Hypothesis candidates: entropy- or confidence-aware eviction; behaviour under class-imbalanced / ordered test streams.
- **[!] DISCLAIMER**: ImageNet-scale runs are heavier; use a subset. I have not run the code, and I don't know the per-dataset runtime on MPS.

**References / links**
- Code (official): https://github.com/kdiAAA/TDA (Gitee copy is only a mirror)
- Project page: https://kdiaaa.github.io/tda
- Paper: https://openaccess.thecvf.com/content/CVPR2024/html/Karmanov_Efficient_Test-Time_Adaptation_of_Vision-Language_Models_CVPR_2024_paper.html
- arXiv: https://arxiv.org/abs/2403.18293
- Not eligible, same topic: BoostAdapter is NeurIPS 2024 (https://proceedings.neurips.cc/paper_files/paper/2024/hash/7d60bfd8458b67acbbaf18b892338d00-Abstract.html). DMN/DPE venues unverified.

---

### Rank 2. Training-free open-vocabulary semantic segmentation: ClearCLIP / SCLIP (ECCV 2024 **[M]**)

**What it is**: CLIP gives noisy dense (patch-level) predictions. ClearCLIP removes the residual connection and FFN and uses self-self attention in the last layer **[V]**; SCLIP replaces the last self-attention with correlative self-attention **[V]**. No training.

**What needs to be done**
1. Confirm the ECCV 2024 listing for the chosen paper first.
2. Clone the repo, install, run on PASCAL VOC (small) with a ViT-B/16 CLIP.
3. Reproduce mIoU for the baseline CLIP and the method.
4. Implement the extension, test on 2-3 benchmarks, analyse failures (small objects, background class).

**Strengths**
- Simple, visual (segmentation masks are great for slides), no training.
- Public benchmarks, official code for both papers.
- Two closely related methods give a ready-made baseline comparison.

**Time / effort: about 26-47 h topic-specific, about 85-107 h overall (medium).** Setup 8-15 h (segmentation evaluation framework), modification 8-12 h, experiments 10-20 h. Experiments scale with the number of benchmarks, so limit to VOC plus one more. Estimate, not verified.

**Fit with lecture requirements: good.** Vision-focused. Hyperparameter analysis is natural (layer choice, resolution, window size) and so is a design change (last-layer attention variant). The weak spot is baselines: a random baseline is trivial (random class per pixel) and a KNN baseline over patch features is awkward but possible (labelled patch features from a few images). **Check with the instructor what counts as KNN and random baselines for segmentation.**

**Code improvement feasibility: Medium-high (to verify)**
- The change is confined to the last transformer layer, so variants (combining both, multi-scale, windowed, different layers) are easy to prototype.
- Evaluation harness may be built on a heavy segmentation framework (e.g. mmsegmentation), which could complicate setup on M1. I have not checked this.
- **[!] DISCLAIMER**: memory/time at ADE20K/Cityscapes resolution and sliding-window inference on 16 GB or free Colab is unverified. Start with VOC.

**References / links**
- ClearCLIP code: https://github.com/mc-lan/ClearCLIP, arXiv https://arxiv.org/abs/2407.12442
- SCLIP code: https://github.com/wangf3014/SCLIP, arXiv https://arxiv.org/abs/2312.01597

---

### Rank 3. Industrial anomaly detection: PatchCore (CVPR 2022) **[V]**

**What it is**: Roth et al. extract mid-level patch features from a pretrained WideResNet-50, store normal-image patches in a memory bank reduced by coreset subsampling, and score test patches by nearest-neighbour distance.

**What needs to be done**
1. Clone the official repo, download MVTec AD (~5 GB **[M]**).
2. Run one category (e.g. `bottle`) to measure time and RAM on M1 / Colab. **Do this before committing.**
3. Reproduce image-level AUROC on a handful of categories.
4. Implement the extension (e.g. different coreset ratio, lighter backbone, better scoring), compare to baseline.

**Strengths**
- Very simple concept, strong results (image AUROC up to 99.6% in the CVPR version **[V]**).
- No backbone training; MVTec AD is a standard public dataset.
- Clear, measurable metrics (AUROC, pixel AUROC), good for hypotheses.
- Interesting real-world application.

**Time / effort: about 30-60 h topic-specific, about 90-120 h overall (medium-high).** Setup 8-20 h (wide range because of the possible CUDA to M1 port), modification 10-15 h, experiments 12-25 h (15 MVTec categories; use a subset). Plan to run the `bottle` test in week 1 to decide Colab vs. M1. Estimate, not verified.

**Fit with lecture requirements: good.** PatchCore is itself a nearest-neighbour method, so the KNN baseline question is partly built in (compare k, coreset ratio, no coreset). Random baseline is 50% AUROC. Hyperparameter analysis (coreset ratio, backbone layers, neighbourhood size) and design modification fit the two-part structure well. Vision-focused.

**Code improvement feasibility: Medium-high (to verify)**
- Natural knobs: coreset ratio, backbone, layer choice, neighbour scoring; each is a contained change.
- The repo is likely CUDA-oriented, so porting to MPS/CPU may take work (unverified).
- **[!] DISCLAIMER**: RAM use of the memory bank at full resolution on 16 GB is unknown. Colab is the fallback.
- Backup in the same topic: WinCLIP (CVPR 2023) has no official code **[V]** (only third-party `anomalib`), so it is not recommended as the main paper.

**References / links**
- Code (official): https://github.com/amazon-research/patchcore-inspection
- Paper: https://openaccess.thecvf.com/content/CVPR2022/html/Roth_Towards_Total_Recall_in_Industrial_Anomaly_Detection_CVPR_2022_paper.html
- arXiv: https://arxiv.org/abs/2106.08265
- WinCLIP: https://openaccess.thecvf.com/content/CVPR2023/html/Jeong_WinCLIP_Zero-Few-Shot_Anomaly_Classification_and_Segmentation_CVPR_2023_paper.html

---

### Rank 4. Image captioning: SmallCap / ConZIC (CVPR 2023) **[V]**

**What it is**: SmallCap prompts a GPT-2 decoder with retrieved captions and trains only ~7M cross-attention params over frozen CLIP + GPT-2. ConZIC is zero-shot, sampling-based (Gibbs) caption polishing with CLIP + BERT.

**What needs to be done**
1. Pick one paper. SmallCap: download the COCO retrieval datastore/index and the `Yova/SmallCap7M` checkpoint; ConZIC: run the demo/Colab first.
2. Evaluate on a COCO subset (CIDEr/BLEU; CLIPScore as a metric only).
3. Implement an extension (e.g. changing the retrieval set or number of retrieved captions for SmallCap; sampling schedule for ConZIC) and compare.

**Strengths**
- Works as a shared CV + NLP topic with a partner on the NLP side.
- Pretrained checkpoint (SmallCap) and demo notebooks/HF Space exist.
- Retrieval ablations are cheap and measurable.

**Time / effort: about 35-70 h topic-specific, about 95-130 h overall (high).** Setup 10-20 h (datastore, metrics tooling), modification 10-20 h, experiments 15-30 h (slow generation, so subset evaluation). Heaviest option, and the tightest against the 30 Jan deadline. Estimate, not verified.

**Fit with lecture requirements: mixed.** Lecture 5 explicitly mentions KNN for captioning (retrieve the nearest image and reuse its caption), and SmallCap's retrieval is close to that, so a KNN-caption baseline is natural. Random baseline: random caption from the datastore. The risk is the **vision-focus rule**: the contribution must not be purely NLP-evaluated. A retrieval/image-encoder-side change would count; a decoding or language change would not. ConZIC is more NLP-heavy (BERT sampling), so it is the weaker of the two.

**Code improvement feasibility: Medium (to verify)**
- SmallCap: retrieval datastore and prompt construction are modular, so retrieval-side ideas are cheap. Training changes are not.
- ConZIC: iterative sampling is a natural place to experiment but is slow.
- **[!] DISCLAIMER**: SmallCap datastore size is unknown. ConZIC may be too slow on M1 for full-COCO evaluation, so expect a subset. Evaluation tooling (COCO caption metrics) may require extra Java-based setup, unverified.

**References / links**
- SmallCap code: https://github.com/RitaRamo/smallcap, paper: https://openaccess.thecvf.com/content/CVPR2023/papers/Ramos_SmallCap_Lightweight_Image_Captioning_Prompted_With_Retrieval_Augmentation_CVPR_2023_paper.pdf, arXiv https://arxiv.org/abs/2209.15323
- ConZIC code: https://github.com/joeyz0z/ConZIC, paper: https://openaccess.thecvf.com/content/CVPR2023/html/Zeng_ConZIC_Controllable_Zero-Shot_Image_Captioning_by_Sampling-Based_Polishing_CVPR_2023_paper.html, arXiv https://arxiv.org/abs/2303.02437
- Not eligible: ClipCap (arXiv only), I-Tuning (ICASSP), CLIPScore (EMNLP, use as a metric only).

---

### Rank 5. Training-free few-shot CLIP adaptation: Tip-Adapter (ECCV 2022) **[V]**

**What it is**: Zhang et al. build a key-value cache from the few-shot training set and combine its predictions with CLIP's, with an optional fine-tuned variant (Tip-Adapter-F).

**What needs to be done**
1. Clone the repo, prepare datasets following the CoOp setup (11 few-shot datasets **[V]**).
2. Reproduce training-free results at k = 1, 2, 4, 8, 16 shots on small datasets.
3. Implement an extension and compare.

**Strengths**
- Easiest to reproduce, very light, official code.
- Direct conceptual relative of TDA, so it doubles as a baseline if TDA is chosen.

**Time / effort: about 20-32 h topic-specific, about 80-92 h overall (low).** Setup 4-8 h, modification 8-12 h, experiments 8-12 h. Least coding, but expect extra time to find and defend an original research gap (20% of the grade). Estimate, not verified.

**Fit with lecture requirements: strong.** Same classification setting as TDA, and Tip-Adapter's cache is literally a learned nearest-neighbour classifier, so KNN and random baselines are trivial. Hyperparameter analysis (shots, alpha, beta) is built in. The weakness is still originality of the gap, not the requirements.

**Code improvement feasibility: Low-medium**
- Simple code, easy to modify, but the method is old and heavily studied, so originality of a gap (20% of grade) is harder to argue.

**References / links**
- Code: https://github.com/gaopengcuhk/Tip-Adapter
- Paper: https://www.ecva.net/papers/eccv_2022/papers_ECCV/html/154_ECCV_2022_paper.php, arXiv https://arxiv.org/abs/2207.09519

---

### Rank 6. Monocular depth estimation: Depth Anything (CVPR 2024) **[V]**

**What it is**: Yang et al. train a depth foundation model on large-scale unlabeled data; a small ViT-S model (24.8M params) with pretrained weights is available **[V]**.

**What needs to be done**
1. Run inference with the small model (repo or HuggingFace `LiheYoung/depth-anything-small-hf`).
2. Define an evaluation (e.g. NYUv2 subset, robustness to corruptions or low light).
3. Propose a training-free or lightweight extension and test it.

**Strengths**
- Trivial inference, very visual results, pretrained weights, active ecosystem.

**Time / effort: about 24-58 h topic-specific, about 85-118 h overall (medium, wide range).** Setup 4-8 h, modification 10-25 h (depends on what the modification turns out to be), experiments 10-25 h. The uncertainty is the gap definition, not the compute. Estimate, not verified.

**Fit with lecture requirements: weak.** KNN and random baselines do not map naturally onto dense depth estimation (a constant-depth or mean-depth baseline would be the closest analogue, which the instructor may or may not accept). Hyperparameter analysis is limited for a pretrained model. This lowers it further as a backup.

**Code improvement feasibility: Unclear**
- It is not obvious what to modify without training. Evaluation-style projects (robustness analysis) are feasible, but "originality" is harder.
- **[!] DISCLAIMER**: fine-tuning or large-benchmark evaluation may exceed M1/Colab. I'm unsure about the dataset sizes/preprocessing needed for evaluation.
- Depth Anything V2 (small model) is the stronger newer option, but verify that V2 is still within the allowed venue/year before using it.

**References / links**
- Code: https://github.com/LiheYoung/Depth-Anything, V2: https://github.com/DepthAnything/Depth-Anything-V2
- Paper: https://openaccess.thecvf.com/content/CVPR2024/html/Yang_Depth_Anything_Unleashing_the_Power_of_Large-Scale_Unlabeled_Data_CVPR_2024_paper.html, arXiv https://arxiv.org/abs/2401.10891

---

### Considered but rejected
- BoostAdapter: NeurIPS 2024. HILTTA (TMLR), ATTA (ICLR 2024): wrong venue.
- ITTA (CVPR 2023): needs a single V100.
- MCM (CLIP OOD detection): I believe NeurIPS 2022 **[M]**. GL-MCM (https://github.com/AtsuMiyai/GL-MCM) appears to be a journal paper, venue unconfirmed. Likely ineligible.
- E²VPT (ICCV 2023, https://github.com/chenghan111/e2vpt): needs prompt training and a ViT-B/16 checkpoint, so medium compute.
- CaFo: code and venue could not be verified.

## 4. Extension ideas (summary) (hypotheses to refine, not yet tested)

**TDA**
- Cache eviction by entropy/confidence instead of simple replacement rules.
- Class-imbalanced or non-i.i.d. (ordered/clustered) test streams. Hypothesis: TDA's gain over zero-shot CLIP shrinks under imbalanced streams, and a modified cache recovers it.
- Sensitivity to cache size and thresholds; are gains concentrated on a few datasets?
- Robustness on corrupted/OOD inputs; latency and memory cost of the cache.

**ClearCLIP/SCLIP**
- Combine the two last-layer modifications, or test them across CLIP backbones/resolutions.
- Hypothesis: gains drop for small objects, and a multi-scale or windowed variant helps.

**PatchCore**
- Coreset sampling ratio vs. accuracy and memory; lightweight backbone (e.g. ResNet-18) to fit M1.
- Compare texture-type vs. object-type categories.

## 5. Action plan to the 13 Dec proposal

- [ ] Clone TDA, set up the env on M1 (or Colab), run one small dataset (Pets or Caltech101) end to end and record time and memory.
- [ ] In parallel, run a quick feasibility test of one backup (ClearCLIP on VOC, or PatchCore on MVTec `bottle`).
- [ ] Open the final paper on openaccess.thecvf.com and confirm venue/year.
- [ ] Skim key references (for TDA: CLIP, TPT, CoOp, Tip-Adapter).
- [ ] Pick one gap and write one measurable hypothesis. Plan the two experiment parts (hyperparameter analysis, then design modification) and the KNN and random baselines the lectures require.
- [ ] Ask the instructor: (a) what KNN / random baselines mean outside classification, (b) whether the 15% paper analysis is the Stage 2/3 deliverables, (c) which schedule applies (Lecture 7's 3+3 weeks or the PDF dates), (d) whether a review template is expected.
- [ ] Write the 1-page abstract (due 13 Dec). Keep track of AI-tool use for the required declaration in later reports.
- [ ] Mirror the final choice into the Notion course page.
- [ ] Record dataset paths, seeds, and environment in a README once code is added.

## 6. Sources

- Project brief: `MSAI6330_project.pdf`; course outline: `../MSAI6330_Outline_1261.pdf`
- Lecture notes: course Notion page (Lectures 1, 5, 7 for project guidance)
- TDA: https://github.com/kdiAAA/TDA, https://kdiaaa.github.io/tda, https://openaccess.thecvf.com/content/CVPR2024/html/Karmanov_Efficient_Test-Time_Adaptation_of_Vision-Language_Models_CVPR_2024_paper.html
- Tip-Adapter: https://github.com/gaopengcuhk/Tip-Adapter, https://www.ecva.net/papers/eccv_2022/papers_ECCV/html/154_ECCV_2022_paper.php
- BoostAdapter (NeurIPS 2024, ineligible): https://proceedings.neurips.cc/paper_files/paper/2024/hash/7d60bfd8458b67acbbaf18b892338d00-Abstract.html
- PatchCore: https://github.com/amazon-research/patchcore-inspection, https://openaccess.thecvf.com/content/CVPR2022/html/Roth_Towards_Total_Recall_in_Industrial_Anomaly_Detection_CVPR_2022_paper.html
- WinCLIP: https://openaccess.thecvf.com/content/CVPR2023/html/Jeong_WinCLIP_Zero-Few-Shot_Anomaly_Classification_and_Segmentation_CVPR_2023_paper.html
- ClearCLIP: https://github.com/mc-lan/ClearCLIP (arXiv 2407.12442)
- SCLIP: https://github.com/wangf3014/SCLIP (arXiv 2312.01597)
- SmallCap: https://github.com/RitaRamo/smallcap, https://openaccess.thecvf.com/content/CVPR2023/papers/Ramos_SmallCap_Lightweight_Image_Captioning_Prompted_With_Retrieval_Augmentation_CVPR_2023_paper.pdf
- ConZIC: https://github.com/joeyz0z/ConZIC, https://openaccess.thecvf.com/content/CVPR2023/html/Zeng_ConZIC_Controllable_Zero-Shot_Image_Captioning_by_Sampling-Based_Polishing_CVPR_2023_paper.html
- Depth Anything: https://github.com/LiheYoung/Depth-Anything, https://openaccess.thecvf.com/content/CVPR2024/html/Yang_Depth_Anything_Unleashing_the_Power_of_Large-Scale_Unlabeled_Data_CVPR_2024_paper.html
- GL-MCM: https://github.com/AtsuMiyai/GL-MCM
- E²VPT: https://github.com/chenghan111/e2vpt
