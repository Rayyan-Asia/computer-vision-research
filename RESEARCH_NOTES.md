# MSAI6330 Computer Vision: Paper Review & Project Notes

Last updated: 2026-11-02

## 1. Course requirements (from Lecture 1 + course Notion page)

- **Project (20%)**: pick a paper from CVPR / ICCV / ECCV (last 5 years preferred) **with available code**. Then one of:
  1. Reproduce the results
  2. Re-evaluate with modifications/improvements
  3. Apply a novel idea as an extension
- **Paper review (15%)**: summary + critical review (methodology, strengths, weaknesses, improvements). May include a class presentation.
- The same paper may be used for both the review and the project.
- **Compute guidance from professor**: choose lightweight models that run on Google Colab; training from scratch is not required; pre-trained models for inference/evaluation are fine.
- Paper sources: openaccess.thecvf.com, eccv.ecva.net, cvpr.thecvf.com; also OpenReview / ICLR for reviews and a review template.

## 2. My constraints

- Hardware: MacBook Pro M1 (16") or Google Colab (free tier).
- Goal: a paper I can reproduce, find a gap in, and improve, without heavy training.

## 3. Candidate papers (shortlist)

> Status: found via web search only. Hardware needs, venue listing, and repo state are **not yet verified**. Check each before committing.

| # | Paper | Venue | Compute | Code | Notes |
|---|-------|-------|---------|------|-------|
| 1 | **TDA**: Efficient Test-Time Adaptation of Vision-Language Models | CVPR 2024 | Very low: training-free, frozen CLIP, inference only | https://gitee.com/xiaowenza/TDA | **Top pick.** Key-value cache of test features + pseudo-labels. |
| 2 | **E²VPT**: An Effective and Efficient Approach for Visual Prompt Tuning | ICCV 2023 | Medium: needs prompt training (about 0.32% of params on VTAB-1k) | https://github.com/chenghan111/e2vpt | Needs ViT-B/16 checkpoint; may need a subset of VTAB tasks. |
| 3 | **Tip-Adapter**: Training-free Adaption of CLIP for Few-shot Classification | ECCV 2022 | Very low | https://github.com/gaopengcuhk/Tip-Adapter | Easiest to reproduce, but older (2022) and well studied. |
| 4 | CaFo (Tip-Adapter follow-up) | CVPR 2023 (unconfirmed) | Unknown | Unknown | Only seen via a fork README. Verify before considering. |

Search results that were **not** matches (for the record): HILTTA (TMLR), ITTA (CVPR 2023, domain generalization, single V100), ATTA (ICLR 2024).

## 4. Recommendation

**TDA (CVPR 2024)**: inference-only on a frozen CLIP, so it fits an M1 or free Colab. Backups: Tip-Adapter (lightest), E²VPT (heavier).

### Possible gaps to investigate in TDA (hypotheses, not yet confirmed)

- Behaviour under non-i.i.d. or class-imbalanced test streams
- Sensitivity to cache size and thresholds
- Robustness on corrupted / out-of-distribution data
- Whether gains are concentrated on a few favourable datasets
- Cache management: better eviction rule, confidence calibration, entropy-based filtering

## 5. Draft work items

### Paper selection
- [ ] Open TDA on openaccess.thecvf.com; confirm CVPR 2024 listing and experimental setup (hardware, backbone, datasets)
- [ ] Clone the TDA repo and check it is runnable (dependencies, dataset prep, M1 / MPS vs Colab)
- [ ] Run one dataset end to end to confirm feasibility
- [ ] Decide final paper (TDA vs Tip-Adapter vs E²VPT)

### Review
- [ ] Find a review template (CVPR/ICLR reviewer form on OpenReview)
- [ ] Read TDA's key references (CLIP, TPT, CoOp, Tip-Adapter)
- [ ] Summarize contribution, method, and claims
- [ ] Check: does it actually solve the claimed problem? Any cherry-picked results, missing baselines, or hidden costs (latency, memory)?
- [ ] Read the code and compare it to the paper (hyperparameters per dataset, hidden tricks)
- [ ] Write the critical review (strengths, weaknesses, suggested improvements)

### Project
- [ ] Reproduce headline numbers on a subset of datasets
- [ ] Pick one gap and define a hypothesis + experiment
- [ ] Implement the enhancement (e.g. improved cache eviction or filtering)
- [ ] Ablations and comparison against the original
- [ ] Present: look at how the authors present the paper (talk/slides/poster) for ideas

### Housekeeping
- [ ] Mirror final choice and notes into the Notion course page
- [ ] Record dataset paths, seeds, and environment in a README once code is added

## 6. Sources

- TDA repo: https://gitee.com/xiaowenza/TDA
- E²VPT repo: https://github.com/chenghan111/e2vpt
- E²VPT (ICCV 2023) listing: https://mlanthology.org/iccv/2023/han2023iccv-2vpt/
- Tip-Adapter repo: https://github.com/gaopengcuhk/Tip-Adapter
- Tip-Adapter (ECCV 2022) listing: https://www.ecva.net/papers/eccv_2022/papers_ECCV/html/154_ECCV_2022_paper.php
