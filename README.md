# Awesome Scientific Peer Review [![Awesome](https://awesome.re/badge-flat.svg)](https://awesome.re)

<!--lint disable double-link-->
[![License: CC BY 4.0](https://img.shields.io/badge/license-CC%20BY%204.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/) [![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](#contributing)
<!--lint enable double-link-->

A curated catalog of datasets, systems, papers, evaluation methods, and infrastructure for AI-assisted scientific peer review.

Use this list to find resources for reviewer matching, critique assistance, review-quality analysis, meta-reviewing, rebuttal and revision support, scholarly retrieval, and responsible human-in-the-loop workflows.

> [!IMPORTANT]
> Scientific peer review requires expert judgment, confidentiality, fairness, and accountability. These resources should support human reviewers and editors, not replace responsible human decision-making.

## Contents

- [Find Resources by Purpose](#find-resources-by-purpose)
- [Recommended Baselines by Task](#recommended-baselines-by-task)
- [Dataset Selection Guide](#dataset-selection-guide)
- [Evaluation Recipes](#evaluation-recipes)
- [Starter Packs](#starter-packs)
- [Tag Guide](#tag-guide)
- [Taxonomy](#taxonomy)
- [Resource Catalog](#resource-catalog)
- [Infrastructure and Building Blocks](#infrastructure-and-building-blocks)
- [Policies, Ethics, and Governance](#policies-ethics-and-governance)
- [Evaluation Checklist](#evaluation-checklist)
- [Open Gaps](#open-gaps)
- [Related Awesome Lists](#related-awesome-lists)
- [Contributing](#contributing)
- [Acknowledgements](#acknowledgements)

<!--lint disable awesome-list-item double-link table-pipe-alignment-->
## Find Resources by Purpose

| Purpose | Start with | Good baseline | Notes |
| --- | --- | --- | --- |
| Understand the field | *What Can NLP Do for Peer Review?*; *Can AI Be a Good Peer Reviewer?* | Reproduce one task taxonomy and compare it with the workflow and facet taxonomy below | Surveys age quickly; verify artifact and policy status. |
| Train or evaluate on end-to-end peer-review data | PeerRead; NLPeer; MOPRD | Fine-tune or evaluate a text model on papers, reviews, scores, or decisions | Venue and discipline coverage differ substantially. |
| Predict review scores or acceptance decisions | PeerRead; ASAP-Review | Majority/mean predictor, then a paper-and-review text classifier | Decision prediction is not a substitute for scientific judgment. |
| Generate paper reviews or structured critique | NLPeer; ReviewAdvisor; OpenReviewer | Prompt an LLM with the paper and a fixed review rubric | Fluency can hide weak novelty and methodology analysis. |
| Evaluate review helpfulness, utility, or actionability | RevUtil; ReAct; SubstanReview | Binary or ordinal classifier over utility labels | Use when the target is usefulness to authors rather than paper quality. |
| Detect review deficiencies or low-quality critiques | ReviewCritique; LazyReview | Rubric-based judge for vague, unsupported, contradictory, or misunderstood claims | Validate model judgments with qualified humans. |
| Analyze novelty, soundness, clarity, comparison, or impact | PeerRead; Peer Review Analyze; Mind the Blind Spots | Sentence-level aspect classifier | Aspect coverage does not establish correctness. |
| Model argument structure in reviews | AMPERE; Argument Mining Driven Analysis | Proposition classifier for evaluation, request, fact, reference, and quote | Argument roles are descriptive, not correctness labels. |
| Link reviews to rebuttals or author responses | DISAPERE; APE | Sentence-pair similarity or NLI-style matching | Paraphrase and omitted context make alignment difficult. |
| Generate or evaluate meta-reviews | MReD; ReviewAgents | Structured multi-review summarization | Preserve disagreement and uncertainty instead of averaging them away. |
| Align review comments to manuscript revisions | ARIES; CASIMIR; F1000RD | Sentence alignment between comments and changed spans | Author changes may address comments indirectly. |
| Match reviewers to papers | OpenReview Matcher; OpenAlex; Semantic Scholar | Abstract-to-publication embedding similarity | Add conflicts, workload, diversity, seniority, and recency constraints. |
| Parse papers and retrieve scholarly evidence | GROBID; Semantic Scholar; OpenAlex | Parse sections and references, retrieve top-k related papers, then apply a review rubric | Evaluate parsing errors and retrieval coverage separately. |
| Evaluate RAG-based review assistants | Ragas; TruLens; Phoenix; YESciEval | Retrieval relevance plus citation-faithfulness checks | Good retrieval does not guarantee a correct critique. |
| Evaluate LLM-as-reviewer systems | Mind the Blind Spots; ReviewCritique; RevUtil | Rubric-based judge plus expert review of sampled outputs | Use multiple dimensions and qualified human validation. |
| Test robustness, bias, gaming, or policy risks | Breaking the Reviewer; Are We There Yet?; Stop Automating Peer Review Without Rigorous Evaluation | Repeated runs with prompt perturbations and rewritten paper text | Robustness is cross-cutting and cannot be reduced to one score. |

## Recommended Baselines by Task

| Task | Simple Baseline | Stronger Baseline | Evaluation Data | Caveats |
| --- | --- | --- | --- | --- |
| Review generation | Prompt an LLM with the paper and a structured review rubric | ReviewAdvisor, ReviewRobot, TreeReview, or OpenReviewer, depending on artifact availability | PeerRead, NLPeer, and OpenReview-derived corpora | Fluent reviews may miss novelty, methodological validity, and decision-relevant weaknesses. |
| Aspect-aware review evaluation | Classify review sentences using PeerRead or Peer Review Analyze aspect labels | Identifying Aspects in Peer Reviews; Mind the Blind Spots | PeerRead, Peer Review Analyze, ASAP-Review | Aspect coverage is not the same as correctness or usefulness. |
| Review utility and actionability | Binary or ordinal classifier over comment-level utility labels | RevUtil, ReAct, or SubstanReview methods and rubrics | RevUtil, ReAct, SubstanReview | An actionable comment can still be wrong or poorly grounded. |
| Deficiency detection | Rubric-based LLM judge for vague, unsupported, contradictory, or misunderstood critique | ReviewCritique; LazyReview | ReviewCritique, LazyReview | Model judges can reproduce review and annotation biases. |
| Argument mining | Proposition classifier for evaluation, request, fact, reference, and quote | AMPERE models; Argument Mining Driven Analysis | AMPERE | Argument labels do not directly measure scientific correctness. |
| Review-rebuttal linking | Sentence-pair similarity or NLI-style matching | APE, DISAPERE, or MLMC | DISAPERE, APE | Pairing is sensitive to paraphrase, many-to-many links, and missing context. |
| Meta-review generation | Summarize multiple reviews with a structured template | MReD or ReviewAgents-style synthesis | MReD and OpenReview review/meta-review data | Preserve disagreement, confidence, and unresolved concerns. |
| Review-to-revision alignment | Align review comments with changed manuscript sentences | ARIES, CASIMIR, or F1000RD workflows | ARIES, CASIMIR, F1000RD, arXivEdits | Revisions can respond indirectly or incompletely. |
| Reviewer matching | Compare paper-abstract and reviewer-publication embeddings | OpenReview Matcher with affinities and constraints | OpenReview Matcher, OpenAlex, Semantic Scholar, Sentence Transformers | Topical similarity alone ignores conflicts and assignment fairness. |
| RAG-grounded review assistance | GROBID + Semantic Scholar/OpenAlex retrieval + LLM rubric | A traced RAG pipeline evaluated with Ragas, TruLens, Phoenix, or YESciEval | Parsed papers, retrieved literature, and expert review samples | Test retrieval relevance and citation faithfulness separately. |
| Robustness and gaming | Repeat runs with prompt perturbations and rewritten paper text | Breaking the Reviewer; Stop Automating Peer Review Without Rigorous Evaluation; Are We There Yet? | Adversarial examples and robustness studies | Robustness is a system property, not a single benchmark metric. |

## Dataset Selection Guide

| Dataset | Best For | Contains | Baseline Use | Limitations |
| --- | --- | --- | --- | --- |
| PeerRead | Review generation, score prediction, aspect modeling | Papers + reviews + scores + decisions | Foundational paper-review modeling baseline | Mostly computer-science venues; incomplete review workflow. |
| NLPeer | Cross-domain review modeling and guided reading | Papers + reviews + decisions + revisions | Strong open corpus for review assistance | Still concentrated in NLP/AI communities. |
| MOPRD | Multi-round and multidisciplinary review workflows | Manuscript versions + reviews + rebuttals + meta-reviews + decisions | End-to-end workflow experiments | Check source-specific access and license details. |
| F1000RD | Pragmatic roles, intertextual links, and revisions | Open-review articles + reviews + document versions + links | Review-to-document and revision alignment | Open-journal setting may not transfer to closed review. |
| AMPERE | Argument mining in review text | Reviews + proposition spans + argument-role labels | Evaluation/request/fact/reference/quote classifier | Small, domain-focused corpus; not a correctness benchmark. |
| DISAPERE | Review-rebuttal discourse and linking | Reviews + rebuttals + discourse/aspect/polarity labels + links | Review-response alignment baseline | Limited venue/domain coverage. |
| MReD | Meta-review generation | Reviews + meta-reviews + structural labels | Structured multi-review summarization | Primarily one research community. |
| Peer Review Analyze | Aspect, purpose, sentiment, and section analysis | Reviews + sentence-level multilayer labels | Multi-task review analysis | Limited scale; check source for access details. |
| ReAct | Actionability and review-comment function | Review comments + actionability/function labels | Comment classification | Does not test whether critiques are scientifically correct. |
| RevUtil | Author-facing review utility | Review comments + utility dimensions | Actionability/helpfulness scoring | Utility dimensions require human validation across domains. |
| ReviewCritique | Review deficiency detection | Papers + reviews + deficiency labels + explanations | Rubric or classifier for review failures | Expert annotations are costly and domain-sensitive. |
| LazyReview | Lazy-thinking critique patterns | Review sentences + deficiency categories | Cognitive-shortcut classifier | Focused on NLP reviews and selected failure modes. |
| SubstanReview | Claim-evidence grounding | Review claims + supporting evidence links | Substantiation extraction | Limited size; not a complete review-quality benchmark. |
| ARIES | Review-to-edit alignment | Review comments + manuscript edits | Comment-to-revision alignment | Silver labels can be noisy; field coverage is limited. |
| CASIMIR | Revision intent and version alignment | Paper versions + aligned sentences + revision intents + reviews | Sentence alignment and edit classification | Limited to openly available review/version histories. |
| HedgePeer | Uncertainty and calibration language | Reviews + hedge cues/spans | Hedge detection | Linguistic uncertainty is only one calibration signal. |
| ASAP-Review | Aspect-informed review score prediction | Review comments + aspect/sentiment annotations reported by the source paper | Intermediate-task transfer baseline | Standalone artifact access/license is unclear; verify through the source paper. |
| CiteTracked | Longitudinal review and impact analysis | Published ML papers + reviews + citation counts | Review/citation correlation or prediction | Older, domain-specific data; dataset access details require checking. |

## Evaluation Recipes

### Review Generation Quality

Evaluate aspect coverage, grounding in manuscript passages, novelty and methodology critique, actionability, professionalism, calibration, and agreement with qualified reviewers.

Start with PeerRead or NLPeer for data; compare a structured prompt with ReviewAdvisor or OpenReviewer where runnable artifacts are available. Use RevUtil or ReviewCritique for diagnostics and YESciEval, Prometheus, or G-Eval for rubric-based judging, always with human validation.

### Review Utility and Actionability

Check whether each comment identifies a concrete issue, provides sufficient context, suggests a feasible improvement, and is verifiable. RevUtil, ReAct, and SubstanReview provide complementary utility, function, and substantiation signals.

### Rebuttal and Revision Support

Measure review-to-rebuttal alignment, response completeness, whether responses address the original critique, and whether manuscript changes correspond to review comments. Useful resources include DISAPERE, APE, ARIES, CASIMIR, and F1000RD.

### Reviewer Matching

Evaluate topical expertise, conflict avoidance, assignment coverage, workload balance, diversity and seniority constraints, and historical reviewing load. A practical stack combines OpenReview Matcher with OpenAlex or Semantic Scholar metadata and Sentence Transformers embeddings.

### Robustness and Policy

Test repeated-run stability, paper rewriting, prompt injection, citation hallucination, prestige bias, confidentiality risk, and review homogenization. Use Breaking the Reviewer, Are We There Yet?, Stop Automating Peer Review Without Rigorous Evaluation, and current COPE, Nature, ACM, NeurIPS, and ICLR policies.

## Starter Packs

### Minimal Review-Generation Baseline

- **Dataset:** PeerRead or NLPeer.
- **Parser:** GROBID.
- **Retrieval:** Semantic Scholar or OpenAlex.
- **Generator:** Structured LLM prompt or ReviewAdvisor.
- **Evaluation:** RevUtil-style actionability rubric plus expert review.

### Review-Quality Diagnostics

- **Dataset:** RevUtil and ReviewCritique.
- **Baseline:** Supervised classifier or rubric-based LLM judge.
- **Evaluation:** Actionability, grounding, specificity, verifiability, helpfulness, and deficiency labels.

### Review-Rebuttal Alignment

- **Dataset:** DISAPERE or APE.
- **Baseline:** Sentence-pair similarity or NLI.
- **Stronger method:** APE or MLMC.
- **Evaluation:** Linked review-rebuttal pairs.

### Reviewer Matching

- **Metadata:** OpenAlex or Semantic Scholar.
- **Embeddings:** Sentence Transformers.
- **Assignment:** OpenReview Matcher.
- **Evaluation:** Topical match, conflict constraints, and load balance.

### RAG-Grounded Reviewer Assistant

- **Parser:** GROBID.
- **Metadata:** Semantic Scholar, OpenAlex, and Crossref.
- **RAG framework:** LlamaIndex, Haystack, or LangChain.
- **Evaluation:** Ragas, TruLens, Phoenix, or YESciEval.
- **Human check:** Domain-expert validation.

### Robustness Audit

- **Baseline:** Repeated-run stability tests.
- **Perturbations:** Rewritten paper, adversarial phrasing, and prompt injection.
- **Resources:** Breaking the Reviewer, Are We There Yet?, and Stop Automating Peer Review Without Rigorous Evaluation.
- **Policy:** COPE, Nature, ACM, ICLR, and NeurIPS.

## Tag Guide

Use 3–6 functional tags per catalog item.

- **Resource kind:** `[survey]`, `[paper]`, `[dataset]`, `[benchmark]`, `[system]`, `[model]`, `[tool]`, `[service]`, `[policy]`.
- **Access:** `[open-code]`, `[open-data]`, `[paper-only]`, `[api]`, `[proprietary]`, `[access-unclear]`.
- **Purpose:** `[review-generation]`, `[review-quality]`, `[aspect-evaluation]`, `[argument-mining]`, `[meta-review]`, `[rebuttal]`, `[revision]`, `[reviewer-matching]`, `[scholarly-retrieval]`, `[document-parsing]`, `[llm-as-judge]`, `[robustness]`.
- **Evaluation facet:** `[argument]`, `[aspect]`, `[structure]`, `[tone]`, `[polarity]`, `[grounding]`, `[calibration]`.
- **Baseline status:** `[baseline]`, `[starter]`, `[advanced]`, `[human-study]`, `[field-trial]`.

## Taxonomy

This catalog uses two complementary taxonomies: where a resource acts in the peer-review workflow, and what it evaluates.

### Peer Review Workflow

1. **Manuscript ingestion and parsing** - Extract sections, references, figures, tables, equations, and metadata.
2. **Reviewer matching and conflict support** - Identify qualified reviewers while considering expertise, workload, relationships, and conflicts.
3. **Review generation and critique assistance** - Draft structured feedback, identify possible weaknesses, and retrieve supporting literature.
4. **Review analysis and quality assessment** - Measure grounding, coverage, utility, professionalism, and reasoning quality.
5. **Meta-review and decision support** - Synthesize reviews and discussions for accountable human chairs and editors.
6. **Rebuttal and author-response support** - Link review points to responses and help authors prepare evidence-grounded replies.
7. **Revision and review-to-edit alignment** - Connect comments to manuscript changes and model revision intent.
8. **Auditing, robustness, bias, and policy** - Test manipulation resistance, calibration, fairness, confidentiality, and governance.
9. **Infrastructure and reusable building blocks** - Supply scholarly data, retrieval, evaluation, and agent capabilities.

### Evaluation Levels and Facets

- **Paper review evaluation facets** are criteria used within a review to assess a manuscript.
- **Peer review evaluation facets** are criteria used to assess the review itself.
- **Argument facets** cover evaluation, requests, facts, references, quotes, substantiation, actionability, and cross-text links.
- **Content aspect facets** cover novelty, soundness, clarity, impact, comparison, replicability, and validity.
- **Structure facets** cover discourse roles, organization, manuscript-section links, and multi-stage interaction.
- **Sentiment facets** cover politeness, harshness, helpfulness, and interpersonal tone.
- **Polarity facets** cover strengths, weaknesses, disagreement, contradiction, hedging, uncertainty, and calibration.

<!--lint enable awesome-list-item double-link table-pipe-alignment-->
## Resource Catalog

### Foundations and Surveys

- [Can AI Be a Good Peer Reviewer? A Survey of Peer Review Process, Evaluation, and the Future](https://arxiv.org/abs/2604.27924) - Surveys generation, rebuttal, meta-review, revision, evaluation, and governance across the AI-assisted review workflow. Tags: `[survey]` `[paper-only]` `[review-generation]` `[meta-review]` `[robustness]`.
- [Can We Automate Scientific Reviewing?](https://arxiv.org/abs/2102.00176) - Foundational study of aspect-aware review generation, evaluation criteria, and limitations of automatically generated feedback. Tags: `[paper]` `[system]` `[open-code]` `[review-generation]` `[baseline]`.
- [Challenges, Experiments, and Computational Solutions in Peer Review](https://doi.org/10.1145/3528086) - Reviews reviewer assignment, review quality, incentives, bias, and large-conference experimentation. Tags: `[survey]` `[paper-only]` `[reviewer-matching]` `[review-quality]` `[robustness]`.
- [Reviewer Assignment Problem: A Scoping Review](https://arxiv.org/abs/2305.07887) - Synthesizes reviewer-matching methods, selection criteria, representations, and evaluation practices. Tags: `[survey]` `[paper-only]` `[reviewer-matching]`.
- [What Can Natural Language Processing Do for Peer Review?](https://arxiv.org/abs/2405.06563) - Maps NLP opportunities and risks from submission through camera-ready revision. ([Companion Resources](https://github.com/OAfzal/nlp-for-peer-review)) Tags: `[survey]` `[open-code]` `[review-generation]` `[revision]` `[robustness]`.

### Datasets and Benchmarks

- [ASAP-Review](https://aclanthology.org/2023.ijcnlp-srw.6/) - Aspect-annotated peer-review resource used for intermediate-task transfer in review-score prediction. Tags: `[dataset]` `[access-unclear]` `[aspect-evaluation]` `[baseline]`.
- [CiteTracked](https://pure.itu.dk/portal/da/publications/0270dbc3-5fa8-4b2c-8e65-3a867f5f8cb4) - Longitudinal dataset connecting machine-learning papers and peer reviews with later citation counts. Tags: `[dataset]` `[open-data]` `[review-quality]` `[paper]`.
- [GenReview](https://arxiv.org/abs/2510.21192) - Pairs human reviews with controlled positive, neutral, and negative LLM-generated reviews for ICLR submissions. ([Data](https://anonymous.4open.science/r/gen_review)) Tags: `[dataset]` `[open-data]` `[review-generation]` `[review-quality]` `[polarity]`.
- [MOPRD](https://arxiv.org/abs/2212.04972) - Multidisciplinary open-review data with manuscript versions, reviews, meta-reviews, rebuttals, and decisions. Tags: `[dataset]` `[open-data]` `[meta-review]` `[rebuttal]` `[revision]`.
- [NLPeer](https://arxiv.org/abs/2211.06651) - Ethically sourced multidomain corpus of papers, reviews, decisions, and revisions in a unified representation. ([Data and Code](https://github.com/UKPLab/nlpeer)) Tags: `[dataset]` `[open-data]` `[open-code]` `[review-generation]` `[baseline]`.
- [PeerRead](https://aclanthology.org/N18-1145/) - Foundational dataset of papers, reviews, aspect scores, and acceptance decisions from computer-science venues. ([Data and Code](https://github.com/allenai/PeerRead)) Tags: `[dataset]` `[open-data]` `[open-code]` `[review-generation]` `[baseline]`.

### Review Generation and Critique Assistance

- [Automated Focused Feedback Generation for Scientific Writing Assistance](https://arxiv.org/abs/2405.20477) - Multi-agent workflow for feedback about specific manuscript weakness types. Tags: `[system]` `[paper-only]` `[review-generation]` `[aspect]`.
- [DeepReview](https://arxiv.org/abs/2503.08569) - Multi-stage review framework combining structured analysis, literature retrieval, and evidence-based argumentation. ([Project](https://ai-researcher.net/)) Tags: `[system]` `[service]` `[review-generation]` `[grounding]` `[advanced]`.
- [MARG](https://arxiv.org/abs/2401.04259) - Multi-agent approach that distributes long papers across specialized reviewer agents. Tags: `[system]` `[paper-only]` `[review-generation]` `[structure]`.
- [OpenReviewer](https://arxiv.org/abs/2412.11948) - Open scientific-review model fine-tuned to generate structured critique for machine-learning papers. Tags: `[model]` `[open-code]` `[review-generation]` `[baseline]`.
- [ReviewAdvisor](https://github.com/neulab/ReviewAdvisor) - Aspect-aware review generation code, data, and models accompanying early work on automated reviewing. Tags: `[system]` `[open-code]` `[review-generation]` `[aspect]` `[baseline]`.
- [ReviewAgents](https://arxiv.org/abs/2503.08506) - Multi-role reviewer-agent framework trained with structured review reasoning. Tags: `[system]` `[paper-only]` `[review-generation]` `[meta-review]` `[advanced]`.
- [ReviewRobot](https://arxiv.org/abs/2010.06119) - Explainable review generation based on paper, related-work, and background knowledge graphs. ([Code](https://github.com/EagleW/ReviewRobot)) Tags: `[system]` `[open-code]` `[review-generation]` `[grounding]` `[baseline]`.
- [STRICTA](https://github.com/UKPLab/acl2025-stricta) - Structured READ-EXTRACT-INFER workflow with human-correctable intermediate assessment steps. Tags: `[system]` `[open-code]` `[review-generation]` `[review-quality]` `[structure]`.
- [TreeReview](https://arxiv.org/abs/2506.07642) - Hierarchical question decomposition for deep review generation and actionable feedback. ([Code and Benchmark](https://github.com/YuanChang98/tree-review)) Tags: `[system]` `[open-code]` `[review-generation]` `[argument]` `[advanced]`.

### Review Quality, Utility, and Deficiency Detection

- [Can Large Language Models Provide Useful Feedback on Research Papers?](https://arxiv.org/abs/2310.01783) - Large-scale comparison of GPT-generated and human feedback across ICLR and Nature-family papers. ([Project](https://github.com/Weixin-Liang/LLM-scientific-feedback)) Tags: `[paper]` `[open-code]` `[review-quality]` `[human-study]`.
- [Is Your Paper Being Reviewed by an LLM?](https://arxiv.org/abs/2502.19614) - Benchmark of paired AI-written and human reviews for peer-review-specific AI-text detection. Tags: `[benchmark]` `[paper-only]` `[review-quality]` `[robustness]`.
- [LazyReview](https://arxiv.org/abs/2504.11042) - Review sentences labeled with fine-grained lazy-thinking patterns. ([Data and Code](https://github.com/UKPLab/acl2025-lazy-review)) Tags: `[dataset]` `[open-data]` `[open-code]` `[review-quality]` `[robustness]`.
- [Peer Reviews of Peer Reviews](https://doi.org/10.1371/journal.pone.0320444) - Randomized experiments on whether feedback about reviewing improves review quality and behavior. Tags: `[paper]` `[human-study]` `[review-quality]`.
- [ReAct](https://arxiv.org/abs/2210.00443) - OpenReview comments labeled for actionability and functional review-comment types. ([Data](https://github.com/gtmdotme/ReAct)) Tags: `[dataset]` `[open-data]` `[review-quality]` `[argument]` `[baseline]`.
- [ReviewCritique](https://arxiv.org/abs/2406.16253) - Papers and human/LLM reviews with expert annotations of review deficiencies and explanations. ([Code and Data](https://github.com/jiangshdd/ReviewCritique)) Tags: `[dataset]` `[open-data]` `[open-code]` `[review-quality]` `[robustness]`.
- [RevUtil](https://arxiv.org/abs/2509.04484) - Review comments labeled for actionability, grounding, specificity, verifiability, and helpfulness. ([Data and Code](https://github.com/bodasadallah/RevUtil)) Tags: `[dataset]` `[open-data]` `[open-code]` `[review-quality]` `[grounding]`.
- [SubstanReview](https://arxiv.org/abs/2311.11967) - Expert-annotated reviews for extracting critique claims and supporting evidence. ([Data and Code](https://github.com/YanzhuGuo/SubstanReview)) Tags: `[dataset]` `[open-data]` `[open-code]` `[review-quality]` `[grounding]`.

### Aspect Coverage and Focus Evaluation

- [Aspect-Based Sentiment Analysis of Scientific Reviews](https://arxiv.org/abs/2006.03257) - Models manuscript aspects, aspect-conditioned sentiment, and reviewer disagreement. Tags: `[paper]` `[paper-only]` `[aspect-evaluation]` `[tone]` `[polarity]`.
- [HedgePeer](https://github.com/Tirthankar-Ghosal/HedgePeer-Dataset) - Dataset of hedge cues and spans for uncertainty and reviewer-calibration analysis. Tags: `[dataset]` `[open-data]` `[aspect-evaluation]` `[calibration]`.
- [Identifying Aspects in Peer Reviews](https://github.com/UKPLab/emnlp2025-aspects-in-reviews) - Resources for inducing aspect taxonomies and predicting which aspects papers need and reviews cover. Tags: `[system]` `[open-code]` `[aspect-evaluation]` `[aspect]`.
- [Mind the Blind Spots](https://arxiv.org/abs/2502.17086) - Focus-level framework for comparing attention across manuscript targets and evaluation aspects. Tags: `[benchmark]` `[paper-only]` `[aspect-evaluation]` `[aspect]` `[structure]`.
- [Peer Review Analyze](https://doi.org/10.1371/journal.pone.0259238) - Benchmark with purpose, significance, sentiment, section, and manuscript-aspect annotations. Tags: `[dataset]` `[access-unclear]` `[aspect-evaluation]` `[structure]` `[tone]`.

### Argument Mining and Review-Rebuttal Structure

- [APE: Argument Pair Extraction from Peer Review and Rebuttal](https://github.com/LiyingCheng95/ArgumentPairExtraction) - Multi-task approach and resources for extracting linked argumentative spans. Tags: `[system]` `[open-code]` `[argument-mining]` `[rebuttal]` `[baseline]`.
- [Argument Mining Driven Analysis of Peer Reviews](https://arxiv.org/abs/2012.07743) - Models PRO, CON, and non-argument spans for decision-oriented review analysis. Tags: `[paper]` `[paper-only]` `[argument-mining]` `[polarity]`.
- [Argument Mining for Understanding Peer Reviews](https://arxiv.org/abs/1903.10104) - Introduces AMPERE and its evaluation, request, fact, reference, and quote taxonomy. ([Data](https://xinyuhua.github.io/Resources/naacl19/)) Tags: `[dataset]` `[open-data]` `[argument-mining]` `[argument]` `[baseline]`.
- [Argument Pair Extraction via Attention-Guided Multi-Layer Multi-Cross Encoding](https://github.com/TianyuTerry/MLMC) - Cross-document encoder for aligning review arguments with rebuttal responses. Tags: `[system]` `[open-code]` `[argument-mining]` `[rebuttal]` `[advanced]`.
- [DISAPERE](https://arxiv.org/abs/2110.08520) - Review-rebuttal pairs with discourse functions, aspects, polarity, and cross-document links. ([Data and Code](https://github.com/nnkennard/DISAPERE)) Tags: `[dataset]` `[open-data]` `[open-code]` `[rebuttal]` `[structure]`.
- [When Reviewers Lock Horns](https://github.com/sandeep82945/Contradiction-in-Peer-Review) - Dataset and models for disagreement and contradiction across reviews. Tags: `[dataset]` `[open-code]` `[review-quality]` `[polarity]`.

### Meta-Review and Decision Support

- [AgentReview](https://arxiv.org/abs/2406.12708) - Agent simulation for studying how reviewer knowledge, commitment, intention, and social influence affect outcomes. ([Code](https://github.com/Ahren09/AgentReview)) Tags: `[system]` `[open-code]` `[meta-review]` `[robustness]`.
- [Auto-PRE](https://arxiv.org/abs/2410.12265) - Configurable reviewer-agent framework for evaluating language-generation systems. ([Code](https://github.com/cjj826/Auto-PRE)) Tags: `[system]` `[open-code]` `[meta-review]` `[llm-as-judge]`.
- [MReD](https://arxiv.org/abs/2110.07474) - Meta-review dataset with sentence-level structural labels for controllable generation. Tags: `[dataset]` `[open-data]` `[meta-review]` `[structure]` `[baseline]`.
- [ReviewGraph](https://github.com/relic-yuexi/ReViewGraph) - Graph reasoning over simulated reviewer-author debates for review and decision-support research. Tags: `[system]` `[open-code]` `[meta-review]` `[argument]`.

> Decision-support systems should expose evidence, uncertainty, and reviewer disagreement while leaving final judgments to accountable human chairs and editors.

### Reviewer Matching and Editorial Workflow

- [OpenReview](https://openreview.net/) - Peer-review platform with APIs, reviewer assignment, discussions, rebuttals, and public review data. ([API](https://docs.openreview.net/)) Tags: `[service]` `[api]` `[reviewer-matching]` `[meta-review]` `[rebuttal]`.
- [OpenReview Matcher](https://github.com/openreview/openreview-matcher) - Minimum-cost-flow matcher for assigning papers under affinity and constraint settings. Tags: `[tool]` `[open-code]` `[reviewer-matching]` `[baseline]`.
- [Prophy Referee Finder](https://www.prophy.ai/referee-finder) - Commercial reviewer-discovery service using publications, semantic matching, and conflict signals. Tags: `[service]` `[proprietary]` `[reviewer-matching]`.

### Rebuttal and Revision Support

- [ARIES](https://arxiv.org/abs/2306.12587) - Corpus linking review comments to corresponding scientific paper edits. Tags: `[dataset]` `[open-data]` `[revision]` `[argument]` `[baseline]`.
- [arXivEdits](https://arxiv.org/abs/2210.15067) - Corpus and extraction framework for sentence alignment, edits, and revision intentions across arXiv versions. Tags: `[dataset]` `[paper-only]` `[revision]` `[structure]`.
- [CASIMIR](https://arxiv.org/abs/2403.00241) - Multi-version OpenReview papers with sentence alignments, edits, revision intents, and reviews. Tags: `[dataset]` `[open-data]` `[revision]` `[structure]`.
- [DEFEND](https://arxiv.org/abs/2603.27360) - Human-in-the-loop framework for evidence-grounded, segment-wise rebuttal reasoning and drafting. Tags: `[system]` `[paper-only]` `[rebuttal]` `[grounding]`.
- [F1000RD](https://arxiv.org/abs/2204.10805) - Multidomain corpus for pragmatic tagging, intertextual links, and document-version alignment. ([Data and Code](https://github.com/UKPLab/f1000rd)) Tags: `[dataset]` `[open-data]` `[open-code]` `[revision]` `[structure]`.

### Robustness, Integrity, and Risk

- [Are We There Yet? Revealing the Risks of Utilizing Large Language Models in Scholarly Peer Review](https://arxiv.org/abs/2412.01708) - Evaluates manipulation, incompleteness, prestige bias, and other risks in LLM-generated reviews. Tags: `[paper]` `[paper-only]` `[robustness]` `[polarity]`.
- [Breaking the Reviewer](https://arxiv.org/abs/2506.11113) - Tests automated reviewers under textual adversarial attacks. ([Code](https://github.com/Lin-TzuLing/Breaking-the-Reviewer)) Tags: `[benchmark]` `[open-code]` `[robustness]` `[advanced]`.
- [Stop Automating Peer Review Without Rigorous Evaluation](https://arxiv.org/abs/2605.03202) - Position paper and empirical study of review homogenization and score gaming through paper rewriting. Tags: `[paper]` `[paper-only]` `[robustness]` `[human-study]`.

## Infrastructure and Building Blocks

### Scientific Document Parsing and Scholarly Retrieval

- [ACL Anthology](https://aclanthology.org/) - Open collection of computational-linguistics papers, metadata, and PDFs. Tags: `[service]` `[api]` `[scholarly-retrieval]`.
- [arXiv API](https://info.arxiv.org/help/api/) - Programmatic access to preprint metadata for search and related-work retrieval. Tags: `[api]` `[scholarly-retrieval]` `[starter]`.
- [CERMINE](https://github.com/CeON/CERMINE) - Library for extracting structured metadata, references, and text from scholarly PDFs. Tags: `[tool]` `[open-code]` `[document-parsing]`.
- [Crossref REST API](https://www.crossref.org/documentation/retrieve-metadata/rest-api/) - DOI and publication metadata for citation verification and normalization. Tags: `[service]` `[api]` `[scholarly-retrieval]`.
- [GROBID](https://github.com/kermitt2/grobid) - Converts scholarly PDFs into structured TEI XML. Tags: `[tool]` `[open-code]` `[document-parsing]` `[baseline]`.
- [Nougat](https://github.com/facebookresearch/nougat) - Neural model that converts academic PDFs into structured markup. Tags: `[model]` `[open-code]` `[document-parsing]`.
- [OpenAlex](https://docs.openalex.org/) - Open scholarly graph and API for papers, authors, institutions, concepts, and citations. Tags: `[api]` `[scholarly-retrieval]` `[reviewer-matching]` `[baseline]`.
- [OpenCitations](https://opencitations.net/) - Open citation data and APIs for reference networks and related literature. Tags: `[api]` `[scholarly-retrieval]` `[open-data]`.
- [Open Research Knowledge Graph](https://orkg.org/) - Represents and compares research contributions as structured scholarly knowledge. ([API](https://orkg.org/about/19/API)) Tags: `[service]` `[api]` `[scholarly-retrieval]` `[grounding]`.
- [Science Parse](https://github.com/allenai/science-parse) - Metadata and bibliography parser retained as a useful reference implementation despite limited maintenance. Tags: `[tool]` `[open-code]` `[document-parsing]`.
- [Semantic Scholar Academic Graph API](https://api.semanticscholar.org/api-docs/graph) - Scholarly metadata, citation, recommendation, and embedding endpoints. Tags: `[api]` `[scholarly-retrieval]` `[reviewer-matching]` `[baseline]`.
- [S2ORC](https://arxiv.org/abs/1911.02782) - Structured corpus of scholarly text, citations, figures, tables, and metadata. Tags: `[dataset]` `[open-data]` `[scholarly-retrieval]`.
- [Sentence Transformers](https://github.com/UKPLab/sentence-transformers) - Embedding and reranking toolkit for matching and semantic review analysis. Tags: `[tool]` `[open-code]` `[reviewer-matching]` `[baseline]`.
- [Unpaywall](https://unpaywall.org/products/api) - API for locating legally available open-access versions of scholarly works. Tags: `[service]` `[api]` `[scholarly-retrieval]`.

### Evaluation Frameworks and Judge Models

- [DeepEval](https://github.com/confident-ai/deepeval) - Unit-testing framework for rubric-based LLM application evaluation. Tags: `[tool]` `[open-code]` `[llm-as-judge]`.
- [G-Eval](https://arxiv.org/abs/2303.16634) - Rubric and chain-of-thought-based LLM evaluation method adaptable to review-quality criteria. Tags: `[paper]` `[paper-only]` `[llm-as-judge]` `[baseline]`.
- [Phoenix](https://github.com/Arize-ai/phoenix) - Tracing and evaluation platform for retrieval, agent, and judge behavior. Tags: `[tool]` `[open-code]` `[llm-as-judge]` `[robustness]`.
- [Prometheus](https://github.com/prometheus-eval/prometheus-eval) - Open evaluator models and tooling for rubric-conditioned scoring and feedback. Tags: `[model]` `[open-code]` `[llm-as-judge]` `[baseline]`.
- [Ragas](https://github.com/explodinggradients/ragas) - Evaluation framework for retrieval relevance, grounding, and faithfulness. Tags: `[tool]` `[open-code]` `[llm-as-judge]` `[grounding]`.
- [TruLens](https://github.com/truera/trulens) - Instrumentation and feedback functions for grounded LLM applications. Tags: `[tool]` `[open-code]` `[llm-as-judge]` `[grounding]`.
- [YESciEval](https://arxiv.org/abs/2505.14279) - Scientific-domain LLM-as-a-judge framework with configurable aspects and evaluator qualification. Tags: `[system]` `[open-code]` `[llm-as-judge]` `[aspect]` `[advanced]`.

### RAG, Agents, and Workflow Frameworks

These are general building blocks, not peer-review-specific systems.

- [AutoGen](https://github.com/microsoft/autogen) - Framework for prototyping specialized reviewer, evidence, and synthesis agents. Tags: `[tool]` `[open-code]` `[review-generation]`.
- [CrewAI](https://github.com/crewAIInc/crewAI) - Role-based agent orchestration for experimental review workflows. Tags: `[tool]` `[open-code]` `[review-generation]`.
- [DSPy](https://github.com/stanfordnlp/dspy) - Optimizes modular language-model programs, including retrieval and evaluation pipelines. Tags: `[tool]` `[open-code]` `[llm-as-judge]`.
- [Haystack](https://github.com/deepset-ai/haystack) - Framework for retrieval, document processing, and production RAG pipelines. Tags: `[tool]` `[open-code]` `[scholarly-retrieval]`.
- [LangChain](https://github.com/langchain-ai/langchain) - Orchestration framework for retrieval, tools, structured output, and agents. Tags: `[tool]` `[open-code]` `[scholarly-retrieval]`.
- [LlamaIndex](https://github.com/run-llama/llama_index) - Data and retrieval framework for literature-grounded assistants. Tags: `[tool]` `[open-code]` `[scholarly-retrieval]`.
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel) - SDK for composing model calls, tools, memory, and agent workflows. Tags: `[tool]` `[open-code]` `[review-generation]`.

## Policies, Ethics, and Governance

- [ACM Policy on Authorship](https://www.acm.org/publications/policies/new-acm-policy-on-authorship) - Guidance on generative AI, authorship responsibility, disclosure, and publication integrity. Tags: `[policy]` `[paper-only]` `[robustness]`.
- [ICLR Code of Ethics](https://iclr.cc/public/CodeOfEthics) - Conference requirements relevant to confidentiality, responsible reviewing, and integrity. Tags: `[policy]` `[paper-only]` `[robustness]`.
- [Nature Portfolio Artificial Intelligence Policy](https://www.nature.com/nature-portfolio/editorial-policies/ai) - Publisher policy covering AI authorship, generated content, and reviewer confidentiality. Tags: `[policy]` `[paper-only]` `[robustness]`.
- [NeurIPS Code of Ethics](https://neurips.cc/public/EthicsGuidelines) - Ethics guidance for authors, reviewers, and organizers. Tags: `[policy]` `[paper-only]` `[robustness]`.
- [The COPE Ethical Guidelines for Peer Reviewers](https://publicationethics.org/resources/guidelines-new/cope-ethical-guidelines-peer-reviewers) - Guidance on confidentiality, conflicts, objectivity, timeliness, and accountability. Tags: `[policy]` `[paper-only]` `[robustness]`.

<!--lint disable awesome-list-item double-link-->
## Evaluation Checklist

- **Scope** - Which workflow stage, submission type, field, and venue are supported? See [Find Resources by Purpose](#find-resources-by-purpose).
- **Facet coverage** - Which argument, aspect, structure, tone, and polarity dimensions are measured? See [Taxonomy](#taxonomy).
- **Grounding** - Are critiques linked to manuscript passages, citations, experiments, or external evidence? See [Scientific Document Parsing and Scholarly Retrieval](#scientific-document-parsing-and-scholarly-retrieval).
- **Utility** - Are comments actionable, specific, verifiable, and helpful? See [Review Quality, Utility, and Deficiency Detection](#review-quality-utility-and-deficiency-detection).
- **Calibration** - Does the system express uncertainty and distinguish minor issues from decision-relevant weaknesses? See [Aspect Coverage and Focus Evaluation](#aspect-coverage-and-focus-evaluation).
- **Robustness** - Has it been tested against prompt injection, rewriting, adversarial text, and repeated-run instability? See [Robustness, Integrity, and Risk](#robustness-integrity-and-risk).
- **Human agreement** - Is evaluation calibrated against qualified reviewers rather than only model judges? See [Evaluation Recipes](#evaluation-recipes).
- **Process fit** - Can humans inspect, correct, override, and take responsibility for outputs? See [Policies, Ethics, and Governance](#policies-ethics-and-governance).
- **Data governance** - Are licenses, consent, confidentiality, provenance, and access restrictions explicit? See [Dataset Selection Guide](#dataset-selection-guide).
- **Reproducibility** - Are prompts, models, retrieval sources, rubrics, versions, and settings documented? See [Recommended Baselines by Task](#recommended-baselines-by-task).

## Open Gaps

- Multidisciplinary, multilingual, and non-conference review corpora remain limited.
- Few resources connect reviews, rebuttals, manuscript versions, editorial discussion, and decisions end to end.
- Novelty, significance, and methodological validity remain difficult to evaluate without domain experts.
- Review-quality benchmarks need stronger tests of grounding, calibration, fairness, and long-document reasoning.
- Multi-agent systems need reproducibility checks across repeated runs and changing model versions.
- Reviewer matching needs transparent evaluation of conflicts, workload, diversity, and expertise beyond topical similarity.
- Policy guidance is evolving faster than technical benchmarks, especially around confidentiality.
- More datasets need clear licenses, ethical release documentation, and machine-readable provenance.

<!--lint enable awesome-list-item double-link-->
## Related Awesome Lists

- [Awesome AI Agents](https://github.com/e2b-dev/awesome-ai-agents#readme) - Agent frameworks, platforms, and applied autonomous-system resources.
- [Awesome LLM](https://github.com/Hannibal046/Awesome-LLM#readme) - Broad collection of large-language-model research and engineering resources.
- [Awesome LLM Evaluation](https://github.com/CSHaitao/Awesome-LLMs-as-Judges#readme) - Research on LLM judges, evaluator bias, robustness, and benchmarking.
- [Awesome Peer Review](https://github.com/formula12/Awesome-Peer-Review#readme) - Broad bibliography of computational scientific peer-review research.
- [Awesome RAG](https://github.com/hymie122/RAG-Survey#readme) - Retrieval-augmented generation papers, benchmarks, and methods.
- [Awesome Scientific Language Models](https://github.com/yuzhimanhua/Awesome-Scientific-Language-Models#readme) - Models and datasets for scientific language understanding and generation.

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request. Add each resource to one primary section and use the controlled tags above.

## Acknowledgements

This catalog was developed from original literature review and taxonomy research, supplemented by public primary sources and community-maintained research artifacts.

The initial repository structure and editorial pass were assisted by [OpenAI Codex](https://openai.com/codex/). Resource selection, interpretation, and maintenance remain human-led.

## Footnotes

The original taxonomy, selection, organization, and descriptive text are released under the [Creative Commons Attribution 4.0 International License](LICENSE). Please credit this repository when reusing or adapting the curated work. Linked resources remain governed by their own licenses and terms.
