# Contributing

This collection tracks PET/CT vision-language research and resources. Contributions can add a verified study, improve release/access metadata, or correct an existing entry.

## Inclusion criteria

- Main entries must explicitly study PET or paired PET/CT together with language: alignment/retrieval, reporting, captioning, VQA, grounding, language-guided segmentation, or an imaging-and-language agent.
- Put CT-only foundations in the transfer section and describe their original modality. Do not infer PET/CT evaluation from a general medical VLM release.
- For agents, state whether the language model sees images, volumetric embeddings, tool outputs, measured lesion features, or only text.
- Cite the original paper, publisher/proceedings page, author repository, or official data/model release. Other awesome lists are discovery aids rather than evidence of release status.
- Identify preprints explicitly. Update the venue when a proceedings/publisher page or author release verifies it; preserve the preprint link when helpful.
- Keep one primary paper row per study. Cross-reference additional tasks rather than duplicating the same row across sections. Link associated datasets separately in the dataset table.

## Verify before adding

1. Check PET versus CT versus paired PET/CT, tracer when reported, and the actual image representation: 3D volume, slice, region crop, or projection.
2. Distinguish patients, studies, lesions, region samples, reports, QA pairs, and synthetic conversations. Label paper-reported totals separately from verified release contents.
3. Inspect implementation and dataset/model file listings. A README-only repository is not an implementation; a public QA CSV does not imply that images are public.
4. Mark code, weights, and data independently. Use **available**, **partial**, **gated**, **pending**, or **not verified**, with the specific limitation and a source link.
5. Record application requirements and stated use restrictions concisely. Do not accept access terms or redistribute restricted data as part of maintaining this list.
6. For generated language annotations or LLM-judged benchmarks, describe that provenance when established by the source.
7. Check for an existing paper/project under another name, normalize URLs, and keep links pointed at the actual artifact rather than a search-results page.

## Entry templates

Use the existing English table layout. Newer publication years appear first within each task; ties may follow publication date when verified.

### Paper / model

```markdown
| Year / venue (or arXiv preprint) | **Name — paper title** | Modality, representation, task, and a short factual description. | [Paper](PRIMARY_URL) | [Code](OFFICIAL_URL); weights/data status and specific limitations. |
```

### Dataset

```markdown
| [Dataset name](OFFICIAL_DATA_URL) | Modalities, language supervision, and supported tasks. | Count with explicit unit; state whether paper-reported or release-verified. | Actual download/access status, published scope, and conditions. |
```

### Release watchlist

```markdown
| Resource | Specific missing or announced artifact to check next. | [Primary source](URL) |
```

Keep watchlist entries tied to a substantive paper or author project. When a release becomes available, update the corresponding paper/dataset entry and remove resolved watchlist items. Do not refresh verification dates or create commits when nothing substantive has changed.

## Review

Check Markdown table columns, contents links, duplicate entries, spelling, and whitespace before submitting. Preserve unrelated contributions. Do not delete a resource after a single failed network request; confirm a persistent move or failure with additional evidence. Never add patient records, credentials, downloaded weights, or large imaging archives to this repository.
