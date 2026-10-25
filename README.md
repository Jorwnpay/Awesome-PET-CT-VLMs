# Awesome PET/CT Vision-Language Models

A curated collection of PET/CT vision-language models, datasets, benchmarks, and open-source implementations, covering report generation, image-text alignment, visual grounding, question answering, and agent-assisted interpretation.

收集 PET/CT 视觉语言模型的论文、数据集、模型与开源代码，持续跟踪最新进展及资源发布状态。

Resource status checked: **2026-10-25**. Papers are grouped by task, with newer publication years first within each group. This is a growing collection rather than an exhaustive survey.

## Contents

- [Scope and release status](#scope-and-release-status)
- [Surveys and perspectives](#surveys-and-perspectives)
- [PET/CT papers and models](#petct-papers-and-models)
  - [Report generation](#report-generation)
  - [Image-text alignment and retrieval](#image-text-alignment-and-retrieval)
  - [Visual grounding and lesion captioning](#visual-grounding-and-lesion-captioning)
  - [Visual question answering and multitask models](#visual-question-answering-and-multitask-models)
  - [Image-language diagnosis and prognosis](#image-language-diagnosis-and-prognosis)
  - [Evaluation and hallucination benchmarks](#evaluation-and-hallucination-benchmarks)
  - [Agents and tool-assisted reasoning](#agents-and-tool-assisted-reasoning)
- [Datasets](#datasets)
- [Transferable 3D medical foundations](#transferable-3d-medical-foundations)
- [Evaluation resources](#evaluation-resources)
- [Release watchlist](#release-watchlist)
- [Related collections](#related-collections)
- [Contributing](#contributing)

## Scope and release status

The main collection includes work that explicitly studies PET or paired PET/CT with language. General 3D medical and CT foundations appear in a separate section as potential starting points for transfer. PET image classifiers without language supervision and general medical chatbots without a documented PET/CT experiment are outside the main scope.

**Code available** means implementation files were found, not that the implementation was executed or independently reproduced. **Partial** means only some artifacts are public. **Gated** means access requires accepting conditions or obtaining approval. **Pending** means a release is announced. **Not verified** means no accessible official artifact was confirmed; it does not establish that an artifact does not exist. Check the linked source for current terms and dependencies.

## Surveys and perspectives

| Date / venue | Review | Focus and scope | Source |
| --- | --- | --- | --- |
| 2026-10-08 / Frontiers in Nuclear Medicine | **From task-specific AI to multimodal foundation models in PET/CT: a readiness framework for clinical translation** | Narrative review of PET/CT pretrained representations, image-text grounding, reporting, and agentic workflows, covering literature through July 2026. Introduces MOSAIC-PET, a proposed heuristic evaluation framework whose thresholds and clinical-readiness interpretation have not been formally validated. | [Published review](https://www.frontiersin.org/journals/nuclear-medicine/articles/10.3389/fnume.2026.1956567/full), [DOI](https://doi.org/10.3389/fnume.2026.1956567) |

## PET/CT papers and models

### Report generation

| Year / venue | Work | Input and focus | Paper | Implementation and release |
| --- | --- | --- | --- | --- |
| 2026 / Research | **RIDE — TNM-Accountable Whole-Body 3D FDG PET/CT Report Drafting** | Paired 3D PET/CT for lung-cancer reports; structured impressions and organ-wise exemplar retrieval. The paper reports 1,583 patients, with 520 held-out cases including 276 external cases. | [Paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC13385537/), [DOI](https://doi.org/10.34133/research.1343) | **Partial**: [PETCT2rep demo code](https://github.com/hugowang010406/PETCT2rep) and a [demo checkpoint](https://github.com/hugowang010406/PETCT2rep/releases/tag/weight) are public. The repository explicitly simplifies training, labels, and retrieval resources. Clinical data are by request; proprietary pretraining data are not public. |
| 2026 / CVPR Findings | **PETRG-3D — Vision-Language Models for Automated 3D PET/CT Report Generation** | Paired 3D PET/CT volumes; structured Chinese reports; shared 3D visual encoder, modality-specific projectors, and LoRA language adaptation. | [arXiv](https://arxiv.org/abs/2511.20145) | [Code](https://github.com/Jorwnpay/PETRG-3D), [Qwen3-8B checkpoint](https://huggingface.co/jwppku/PETRG-3D-qwen3-8B), and [AutoPET-RG-Lym](https://huggingface.co/datasets/jwppku/AutoPET-RG-Lym) available. The public lymphoma benchmark is a subset, not the entire clinical cohort studied in the paper. |
| 2026 / ACL | **HiRRA / VietPET-RoI — Region-Grounded Report Generation for 3D Medical Imaging** | Paired 3D PET/CT; hierarchical region and RoI features for Vietnamese reporting. Introduces RoI Coverage and RoI Quality Index. | [ACL Anthology](https://aclanthology.org/2026.acl-long.903/) | [VietPET-RoI data](https://huggingface.co/datasets/b00l26/VietPET-RoI) available, including image volumes, regional reports, and RoI annotations. Official HiRRA model implementation/checkpoints not verified. |
| 2026 / AAAI | **PET2Rep** | Whole-body PET/CT report-generation benchmark; evaluates general VLMs using slice-based visual inputs and prompting. | [arXiv](https://arxiv.org/abs/2508.04062) | [Code, prompts, and results](https://github.com/YichiZhang98/PET2Rep) available; [benchmark data](https://huggingface.co/datasets/r1pples/PET2Rep) gated. Distinguish slice-based evaluation from native 3D model training. |
| 2025 / NeurIPS Datasets and Benchmarks | **ViPET-ReportGen / ViMed-PET — Toward a Vision-Language Foundation Model for Medical Data** | Vietnamese PET/CT-report data; volumetric alignment, report generation, and conversational/VQA benchmarks. | [Paper](https://proceedings.neurips.cc/paper_files/paper/2025/file/a9f5ebadfbf7b6b10d685c385713b35a-Paper-Datasets_and_Benchmarks_Track.pdf) | [Code](https://github.com/AIoT-Lab-AI4LIFE/ViPET-ReportGen) and [multipart data index](https://huggingface.co/datasets/dacthai2807/ViMed-PET) available. Verify coverage of individual parts; the index itself contains links rather than scan volumes. |

The unified PSMA PET/CT model below also studies report generation alongside VQA and segmentation.

### Image-text alignment and retrieval

| Year / venue | Work | Input and focus | Paper | Implementation and release |
| --- | --- | --- | --- | --- |
| 2026 / MICCAI | **PETCT-DiVLA — Semantic-Consistent Dual-Image Vision-Language Alignment via Modality Routing for 3D PET/CT** | Paired 3D PET/CT and reports; modality routing for global/local alignment, retrieval, and classification. | [MICCAI](https://papers.miccai.org/miccai-2026/0946-Paper5633.html) | [Code](https://github.com/Linn60/PETCT-DiVLA) and [pretrained weights](https://huggingface.co/Linn60/PETCT-DiVLA) available. Hugging Face provides the model configuration and checkpoint; this release does not establish public availability of the paired clinical training cohort. |

### Visual grounding and lesion captioning

| Year / venue | Work | Input and focus | Paper | Implementation and release |
| --- | --- | --- | --- | --- |
| 2026 / CVPR | **PETAR / PETAR-4B — Localized Findings Generation with Mask-Aware Vision-Language Modeling for PET Automated Reporting** | PET, CT, and 3D lesion masks as inputs; spatially grounded lesion-level finding generation. | [arXiv](https://arxiv.org/abs/2510.27680) | [Model/inference code](https://github.com/DanyalMaq/petar-release) released; additional preprocessing is announced. [PETARSeg-11K](https://huggingface.co/datasets/UW-Madison-Dept-Radiology/PETARSeg-11K) requires manual approval and a non-commercial research agreement. |
| 2026 / Journal of Imaging Informatics in Medicine | **ConTEXTual Net3D — Vision-Language Modeling in PET/CT for Visual Grounding of Positive Findings** | 3D PET/CT with finding sentences; language-conditioned lesion segmentation using visual features and report-language representations. | [Journal](https://doi.org/10.1007/s10278-026-01879-2), [arXiv](https://arxiv.org/abs/2502.00528) | [Training/inference code](https://github.com/zhuemann/ConTEXTual_Net_3D_Visual_Grounding) available; clinical data access is by request and approval. This is a grounding model rather than a conversational generator. |
| 2025 / MICCAI | **PET-CLIP Captioner — Location-Guided Automated Lesion Captioning in Whole-body PET/CT Images** | Lesion-level image-language modeling with anatomical location guidance. | [Paper](https://papers.miccai.org/miccai-2025/paper/0248_paper.pdf) | Official code, weights, and downloadable paired data not verified. |

### Visual question answering and multitask models

| Year / venue | Work | Input and focus | Paper | Implementation and release |
| --- | --- | --- | --- | --- |
| 2026 / arXiv preprint | **A Unified Vision-Language Model for PSMA PET/CT Report Generation, Visual Question Answering, and Lesion Segmentation** | 3D PSMA PET/CT; a shared multimodal framework for reports, VQA, and segmentation. | [arXiv](https://arxiv.org/abs/2609.15603) | Official model code/weights not verified. Institutional paired reports are available by qualified request and approval; a public segmentation dataset used in experiments does not make the report cohort public. |
| 2026 / arXiv preprint | **MetaStructAtlas / MetaStructVQA** | Whole-body PET/CT; grounded anatomical and metabolic reasoning with hierarchical Chinese/English QA. | [arXiv](https://arxiv.org/abs/2609.03690) | [Data-building/evaluation code](https://github.com/withtst/MetaStructVQA) and [QA tables](https://huggingface.co/datasets/withtst/MetaStructAtlas) available. Complete paired PET/CT volumes were not verified in the public dataset files. |

### Image-language diagnosis and prognosis

| Year / venue | Work | Input and focus | Paper | Implementation and release |
| --- | --- | --- | --- | --- |
| 2026 / npj Digital Medicine | **VITALIS — Graphicalized vision-language modeling for comprehensive lung nodule analysis and risk stratification** | CT/PET slice or subvolume features and structured radiology/clinical text; graph-aware fusion and latent neural-ODE dynamics support nodule detection, malignancy assessment, survival-risk estimation, and nodule counting. Language inputs include template-serialized annotations and clinical attributes. | [Paper](https://doi.org/10.1038/s41746-026-02602-9), [PubMed](https://pubmed.ncbi.nlm.nih.gov/41965884/) | The paper links a [review repository](https://anonymous.4open.science/r/VITALIS-5E6A); accessible implementation files and released weights were not verified. Experiments use both CT-only and PET/CT cohorts; these should not be treated as one shared paired-report dataset. |

### Evaluation and hallucination benchmarks

| Year / venue | Work | Input and focus | Paper | Implementation and release |
| --- | --- | --- | --- | --- |
| 2026 / IJCAI | **Med-StepBench** | Stepwise evaluation of oncologic PET/CT interpretation: anatomy, lesion identification, feature characterization, and diagnostic synthesis. | [IJCAI](https://www.ijcai.org/proceedings/2026/761), [arXiv](https://arxiv.org/abs/2605.10002) | Benchmark release is announced in the paper; official downloadable code/data not verified. |

### Agents and tool-assisted reasoning

These studies connect language models to imaging tools. A pipeline that passes measured features to an LLM is recorded as tool-assisted reasoning, rather than assumed to be a native end-to-end VLM.

| Year / venue | Work | Input and focus | Paper | Implementation and release |
| --- | --- | --- | --- | --- |
| 2026 / arXiv preprint | **VLM- and LLM-Driven Multi-Agent System for PET Image Denoising** | Low-dose FDG PET/CT; slice-based BiomedCLIP dose estimation, image/lesion measurements, and an LLM scheduler selecting diffusion denoisers with quantitative feedback and rollback. | [arXiv](https://arxiv.org/abs/2608.13791) | Official pipeline code, adapted weights, and the clinical low-dose cohort not verified as downloadable. The scheduler receives structured perception outputs; this is tool-assisted restoration rather than native volumetric VLM reporting. |
| 2026 / MICCAI | **RADIANT-PET** | PET/CT segmentation and candidate-feature extraction followed by LLM lesion reasoning; includes local LLM adaptation. | [arXiv](https://arxiv.org/abs/2606.28392) | [Code](https://github.com/jwang-580/RADIANT-PET) available. The reasoning stage consumes structured lesion features; do not equate this with direct volumetric VLM encoding. |
| 2026 / Journal of Nuclear Medicine | **End-to-End PET/CT Interpretation and Quantification with an LLM-Orchestrated AI Agent: A Real-World Pilot Study** | Tool orchestration for image selection, registration, SUV conversion, segmentation, visual interpretation, and reporting; retrospective FDG PET/CT lung-cancer pilot. | [PubMed](https://pubmed.ncbi.nlm.nih.gov/42315314/), [DOI](https://doi.org/10.2967/jnumed.126.272362) | Official code and model release not verified. |

## Datasets

### Image-language data and benchmarks

Counts describe the unit reported by the source. Patients, examinations, region crops, lesions, QA pairs, and generated conversations are different units. Public annotation tables alone do not establish that paired images are downloadable.

| Dataset | Language supervision / task | Reported scale | Access and release scope |
| --- | --- | --- | --- |
| [AutoPET-RG-Lym](https://huggingface.co/datasets/jwppku/AutoPET-RG-Lym) | PET/CT, physician-written structured Chinese reports, and 24-region PET/CT labels; report generation and evaluation. | 135 lymphoma cases derived from AutoPET. | Public images, reports, and labels; distinct from PETRG-3D's full clinical training cohort. |
| [PET2Rep](https://huggingface.co/datasets/r1pples/PET2Rep) | Whole-body PET/CT paired with reports; VLM report-generation evaluation. | 565 cases reported by the [project](https://github.com/YichiZhang98/PET2Rep). | Gated Hugging Face access; review the dataset's conditions. |
| [PETARSeg-11K](https://huggingface.co/datasets/UW-Madison-Dept-Radiology/PETARSeg-11K) | PET/CT lesion descriptions paired with 3D masks; lesion captioning and grounding. | 11,356 description-mask pairs reported in the paper; these are not patient counts. | Manual researcher approval; non-commercial academic/institutional research agreement. |
| [ViMed-PET](https://huggingface.co/datasets/dacthai2807/ViMed-PET) | Vietnamese PET/CT-report pairs; report generation and conversational/VQA tasks. | Paper reports 2,757 studies; expanded text/conversation counts are separate units. | Public index to three release parts, including [Part 2](https://huggingface.co/datasets/Duc2305/ViMed-PET-part2) with image archives and report mappings. Check each part for coverage and terms. |
| [MetaStructAtlas](https://huggingface.co/datasets/withtst/MetaStructAtlas) | Hierarchical Chinese/English PET/CT QA for anatomical and metabolic reasoning. | Public Chinese and English QA tables. | **Partial**: annotation tables verified; full paired image volumes not verified. |
| [VietPET-RoI](https://huggingface.co/datasets/b00l26/VietPET-RoI) | Cropped 3D PET/CT, Vietnamese regional reports, and modality-specific RoI bounding boxes. | Dataset card lists 200 patients, 600 region pairs, and 1,960 RoIs; patient-disjoint 160/40 train/validation split. | Public volume files, reports, manifests, and RoI annotations verified; CC BY-NC-SA 4.0. The card documents stale `_processed.npy` paths in split RoI files, missing physical-space geometry in manifests, and PET values that should not be assumed to be SUV. |
| [Med-StepBench](https://www.ijcai.org/proceedings/2026/761) | Stepwise image-statement evaluation of PET/CT reasoning and hallucination. | Paper reports over 12K images and over 1M image-statement pairs; these are not patient counts. | Release announced; downloadable benchmark not verified. |

### Supporting imaging datasets

These provide PET/CT images and imaging/clinical labels. Paired narrative reports were not verified in the listed releases, so they should not be presented as ready-made image-report training sets.

| Dataset | Imaging and annotations | Access |
| --- | --- | --- |
| [FDG-PET-CT-LESIONS / AutoPET](https://www.cancerimagingarchive.net/collection/fdg-pet-ct-lesions/) | Whole-body FDG PET/CT, lesion segmentations, and clinical metadata; 900 subjects and 1,014 examinations. | TCIA collection currently specifies controlled-data access requirements. Check current access instructions rather than relying on older descriptions of unrestricted availability. |
| [HECKTOR 2026](https://hecktor26.grand-challenge.org/data-download/) | Head-and-neck PET/CT, tumor/lymph-node segmentation, staging and outcome information. | Application and eligibility conditions apply; see the current challenge download page. |

## Transferable 3D medical foundations

These broader 3D medical imaging resources include CT encoders, alignment methods, and instruction-tuning recipes. Their inclusion identifies potential components for transfer; training or validation on paired PET/CT is not implied.

| Year / publication | Resource | Focus | Official resources |
| --- | --- | --- | --- |
| 2026 / Nature | **Merlin** | Abdominal 3D CT foundation model with report/EHR supervision; retrieval, classification, and reporting. | [Paper](https://www.nature.com/articles/s41586-026-10181-8), [code and model instructions](https://github.com/StanfordMIMI/Merlin). |
| 2024 / arXiv | **M3D / M3D-LaMed** | 3D medical image-text pretraining and instruction tuning; retrieval, reporting, VQA, and localization/segmentation tasks. | [Paper](https://arxiv.org/abs/2404.00578), [code and released-model links](https://github.com/BAAI-DCAI/M3D). |
| 2024 / arXiv | **CT-CLIP / CT-CHAT / CT-RATE** | Chest CT-report alignment and conversational modeling with volumetric inputs. | [Paper](https://arxiv.org/abs/2403.17834), [CT-CLIP](https://github.com/ibrahimethemhamamci/CT-CLIP), [CT-CHAT](https://github.com/ibrahimethemhamamci/CT-CHAT), [CT-RATE data and access terms](https://huggingface.co/datasets/ibrahimhamamci/CT-RATE). |

## Evaluation resources

- **PETRG-3D evaluation**: [official evaluation code](https://github.com/Jorwnpay/PETRG-3D/tree/main/evaluation) includes Chinese text-generation metrics and Clinical Efficacy Scores based on 24-region PET uptake and CT-finding labels.
- **Region-grounded reporting**: [HiRRA](https://aclanthology.org/2026.acl-long.903/) introduces RoI Coverage and RoI Quality Index for finding coverage and attribute fidelity, with LLM-based extraction.
- **Stepwise reasoning**: [Med-StepBench](https://www.ijcai.org/proceedings/2026/761) separates errors across stages of PET/CT interpretation.
- **Vietnamese reporting**: [ViPET-ReportGen](https://github.com/AIoT-Lab-AI4LIFE/ViPET-ReportGen) includes a clinical-evaluation component alongside language metrics.

When comparing results, record the tracer, patient-level split, report language, image representation (3D volumes, slices, crops, or projections), text-label provenance, evaluation prompts, and judge model. Report-generation language scores, finding correctness, lesion localization, and segmentation overlap measure different capabilities; compare studies only where their settings support the comparison.

## Release watchlist

Checked **2026-10-25**. Update these rows when official artifacts or access conditions change; an accepted paper or an “open-source” statement alone does not establish a usable release.

| Resource | What to verify next | Primary source |
| --- | --- | --- |
| HiRRA | Locate and inspect the model implementation/checkpoints; VietPET-RoI image/report/RoI data are now verified as released. | [ACL paper](https://aclanthology.org/2026.acl-long.903/), [dataset](https://huggingface.co/datasets/b00l26/VietPET-RoI) |
| PETAR | Check for the announced preprocessing additions and model checkpoint availability. | [Official repository](https://github.com/DanyalMaq/petar-release) |
| MetaStructAtlas | Verify access to complete PET/CT volumes paired with the released QA annotations. | [Dataset](https://huggingface.co/datasets/withtst/MetaStructAtlas) |
| Med-StepBench | Verify the benchmark's promised downloadable release. | [IJCAI paper](https://www.ijcai.org/proceedings/2026/761) |
| Unified PSMA PET/CT VLM | Locate official model code/weights and clarify access to the paired report cohort. | [Paper](https://arxiv.org/abs/2609.15603) |
| PET-CLIP Captioner | Locate official implementation, checkpoints, or paired lesion-caption data. | [MICCAI paper](https://papers.miccai.org/miccai-2025/paper/0248_paper.pdf) |
| PET denoising multi-agent system | Locate official pipeline code, adapted weights, or a release/access statement for the paired low-dose cohort. | [Paper](https://arxiv.org/abs/2608.13791) |
| RIDE / PETCT2rep | Check for the full research implementation and curated data promised by the paper; the current public repository identifies itself as a simplified demo. | [Paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC13385537/), [repository](https://github.com/hugowang010406/PETCT2rep) |

## Related collections

Organization is informed by these broader collections; individual entries above are checked against their original papers and release pages.

- [Awesome Medical Vision-Language Models](https://github.com/yangzhou12/awesome-medical-vision-language-models)
- [Awesome Volumetric Radiology AI](https://github.com/Saint-lsy/Awesome-Volumetric-Radiology-AI)
- [Awesome Radiology Report Generation](https://github.com/mk-runner/Awesome-Radiology-Report-Generation)

## Contributing

Suggestions and corrections are welcome through issues or pull requests. Please include a primary paper/project link and verify modality, task, publication status, and actual artifact availability. See [CONTRIBUTING.md](CONTRIBUTING.md) for inclusion criteria and entry templates.
