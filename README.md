# Awesome Scientific Peer Review [![Awesome](https://awesome.re/badge-flat.svg)](https://awesome.re)

[![License: CC BY 4.0](https://img.shields.io/badge/license-CC%20BY%204.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/) [![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)

A curated catalog of datasets, systems, papers, evaluation methods, and infrastructure for AI-assisted scientific peer review.

Use this list to study or build tools for reviewer matching, critique assistance, review-quality analysis, meta-reviewing, rebuttal and revision support, scholarly retrieval, and responsible human-in-the-loop workflows.

> [!IMPORTANT]
> Scientific peer review requires expert judgment, confidentiality, fairness, and accountability. These resources should support human reviewers and editors, not replace responsible human decision-making.

## Contents

- [Quick Browse](#quick-browse)
- [How to Read](#how-to-read)
- [Taxonomy](#taxonomy)
- [Resource Catalog](#resource-catalog)
- [Infrastructure and Building Blocks](#infrastructure-and-building-blocks)
- [Learning Resources](#learning-resources)
- [Policies, Ethics, and Governance](#policies-ethics-and-governance)
- [Evaluation Checklist](#evaluation-checklist)
- [Open Gaps](#open-gaps)
- [Related Awesome Lists](#related-awesome-lists)

## Quick Browse

| I want to... | Start here |
| --- | --- |
| Understand the field | [Foundations and Surveys](#foundations-and-surveys) |
| Find training or evaluation data | [Datasets and Benchmarks](#datasets-and-benchmarks) |
| Generate structured review feedback | [Review Generation and Critique Assistance](#review-generation-and-critique-assistance) |
| Measure review quality or utility | [Review Analysis and Quality Assessment](#review-analysis-and-quality-assessment) |
| Model arguments, discourse, or rebuttal links | [Argument, Discourse, and Interaction Modeling](#argument-discourse-and-interaction-modeling) |
| Synthesize reviews for chairs or editors | [Meta-Review and Decision Support](#meta-review-and-decision-support) |
| Match papers with reviewers | [Reviewer Matching and Editorial Workflow](#reviewer-matching-and-editorial-workflow) |
| Support rebuttals or manuscript revision | [Rebuttal and Revision Support](#rebuttal-and-revision-support) |
| Parse papers and retrieve scholarly evidence | [Scientific Documents and Scholarly Data](#scientific-documents-and-scholarly-data) |
| Evaluate an LLM reviewer | [Evaluation Frameworks and Judge Models](#evaluation-frameworks-and-judge-models) |
| Build an agentic or RAG pipeline | [RAG, Agents, and Workflow Frameworks](#rag-agents-and-workflow-frameworks) |
| Check policy, confidentiality, or governance | [Policies, Ethics, and Governance](#policies-ethics-and-governance) |

## How to Read

Each resource has one primary catalog location and compact tags for cross-cutting discovery.

### Resource Type

- `📚 survey` - Survey, overview, or field-level synthesis.
- `🗃️ dataset` - Corpus, benchmark, annotations, or structured research data.
- `🤖 system` - Model, workflow, or research prototype for a peer-review task.
- `🛠️ tool` - Reusable software, API, platform, or production service.
- `📏 evaluation` - Metric, evaluator, judge model, or evaluation framework.
- `🎓 learning` - Course, tutorial, or educational implementation.
- `⚖️ policy` - Policy, ethical guidance, or governance resource.

### Workflow Stage

- `📥 ingest` - Manuscript parsing, metadata, references, and evidence retrieval.
- `👥 match` - Reviewer recommendation, assignment, and conflict support.
- `✍️ review` - Review drafting, critique, and focused feedback.
- `🔎 assess` - Review analysis, quality evaluation, and diagnostics.
- `🧑‍⚖️ meta` - Meta-review, reviewer discussion, and decision support.
- `💬 rebuttal` - Author response and review-rebuttal interaction.
- `📝 revise` - Review-to-edit alignment and manuscript revision.
- `🛡️ audit` - Robustness, bias, integrity, policy, and accountability.

### Evaluation Facet

- `argument` - Claims, evidence, requests, substantiation, actionability, or cross-text links.
- `aspect` - Novelty, soundness, clarity, impact, comparison, replicability, or validity.
- `structure` - Discourse roles, organization, section links, or multi-stage interaction.
- `tone` - Politeness, harshness, helpfulness, or interpersonal style.
- `polarity` - Strengths, weaknesses, disagreement, contradiction, hedging, or calibration.

### Availability

- `🟢 open artifact` - Public code, data, model, or reusable software.
- `🟡 public data` - Public dataset or corpus without a complete reusable implementation.
- `🔵 paper` - Paper or description is public; implementation availability is limited or unclear.
- `🟣 service` - Hosted platform or API.
- `⚫ proprietary` - Commercial or closed implementation.

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

Across both levels, five facet families recur:

- **Argument facets** - Evaluation, request, fact, reference, quote, substantiation, claim-evidence links, actionability, argument completeness, and review-rebuttal links.
- **Content aspect facets** - Novelty, originality, soundness, correctness, clarity, substance, impact, appropriateness, meaningful comparison, replicability, and methodological validity.
- **Structure facets** - Review organization, summary-strengths-weaknesses-conclusion structure, discourse functions, review-rebuttal interaction, paper-section links, and multi-stage workflows.
- **Sentiment facets** - Politeness, harshness, helpfulness, interpersonal tone, and aspect-conditioned sentiment.
- **Polarity facets** - Strengths versus weaknesses, accept/reject orientation, disagreement, contradiction, hedging, uncertainty, calibration, and bias.

## Resource Catalog

### Foundations and Surveys

- [Can AI Be a Good Peer Reviewer? A Survey of Peer Review Process, Evaluation, and the Future](https://arxiv.org/abs/2604.27924) - Surveys generation, rebuttal, meta-review, revision, evaluation, and governance across the full AI-assisted review workflow. Tags: `📚 survey` `✍️ review` `🧑‍⚖️ meta` `💬 rebuttal` `🛡️ audit` `🔵 paper`.
- [Can We Automate Scientific Reviewing?](https://arxiv.org/abs/2102.00176) - Foundational study of aspect-aware review generation, evaluation criteria, and the limitations of automatically generated feedback. Tags: `📚 survey` `🤖 system` `✍️ review` `aspect` `🟢 open artifact`.
- [Challenges, Experiments, and Computational Solutions in Peer Review](https://doi.org/10.1145/3528086) - Reviews computational approaches to reviewer assignment, review quality, incentives, bias, and large-conference experimentation. Tags: `📚 survey` `👥 match` `🔎 assess` `🛡️ audit` `🔵 paper`.
- [Reviewer Assignment Problem: A Scoping Review](https://arxiv.org/abs/2305.07887) - Synthesizes computational reviewer-matching methods, selection criteria, representations, and evaluation practices. Tags: `📚 survey` `👥 match` `🔵 paper`.
- [What Can Natural Language Processing Do for Peer Review?](https://arxiv.org/abs/2405.06563) - Maps opportunities and risks for NLP assistance from submission through camera-ready revision. ([Companion Resources](https://github.com/OAfzal/nlp-for-peer-review)) Tags: `📚 survey` `📥 ingest` `✍️ review` `📝 revise` `🛡️ audit` `🟢 open artifact`.

### Datasets and Benchmarks

#### End-to-End Review Corpora

- [F1000RD](https://arxiv.org/abs/2204.10805) - Multidomain corpus for pragmatic tagging, intertextual links, and document-version alignment in open journal peer review. ([Data and Code](https://github.com/UKPLab/f1000rd)) Tags: `🗃️ dataset` `✍️ review` `📝 revise` `structure` `🟢 open artifact`.
- [GenReview](https://arxiv.org/abs/2510.21192) - Large dataset pairing human reviews with controlled positive, neutral, and negative LLM-generated reviews for ICLR submissions. ([Data](https://anonymous.4open.science/r/gen_review)) Tags: `🗃️ dataset` `✍️ review` `🔎 assess` `polarity` `🟡 public data`.
- [MOPRD](https://arxiv.org/abs/2212.04972) - Multidisciplinary open peer-review dataset containing manuscript versions, reviews, meta-reviews, rebuttals, and editorial decisions. Tags: `🗃️ dataset` `✍️ review` `🧑‍⚖️ meta` `💬 rebuttal` `📝 revise` `🟡 public data`.
- [NLPeer](https://arxiv.org/abs/2211.06651) - Ethically sourced multidomain corpus of papers, reviews, decisions, and revisions in a unified structured representation. ([Data and Code](https://github.com/UKPLab/nlpeer)) Tags: `🗃️ dataset` `📥 ingest` `✍️ review` `📝 revise` `🟢 open artifact`.
- [PeerRead](https://aclanthology.org/N18-1145/) - Foundational dataset of scientific papers, reviews, aspect scores, and acceptance decisions from major computer science venues. ([Data and Code](https://github.com/allenai/PeerRead)) Tags: `🗃️ dataset` `✍️ review` `aspect` `polarity` `🟢 open artifact`.

#### Review Quality and Evaluation Facets

- [Aspect-Based Sentiment Analysis of Scientific Reviews](https://arxiv.org/abs/2006.03257) - Dataset and models for manuscript-aspect prediction, aspect-conditioned sentiment, and reviewer disagreement analysis. Tags: `🗃️ dataset` `🔎 assess` `aspect` `tone` `polarity` `🔵 paper`.
- [HedgePeer](https://github.com/Tirthankar-Ghosal/HedgePeer-Dataset) - Dataset of hedge cues and spans for studying uncertainty and reviewer calibration. Tags: `🗃️ dataset` `🔎 assess` `polarity` `🟢 open artifact`.
- [LazyReview](https://arxiv.org/abs/2504.11042) - Peer-review sentences labeled with fine-grained lazy-thinking patterns for training review-quality diagnostics. ([Data and Code](https://github.com/UKPLab/acl2025-lazy-review)) Tags: `🗃️ dataset` `🔎 assess` `argument` `🛡️ audit` `🟢 open artifact`.
- [Peer Review Analyze](https://doi.org/10.1371/journal.pone.0259238) - Benchmark with sentence-level purpose, significance, sentiment, section correspondence, and manuscript-aspect annotations. Tags: `🗃️ dataset` `🔎 assess` `aspect` `structure` `tone` `🔵 paper`.
- [ReAct](https://arxiv.org/abs/2210.00443) - OpenReview comment dataset labeled for actionability and functional review-comment types. ([Data](https://github.com/gtmdotme/ReAct)) Tags: `🗃️ dataset` `🔎 assess` `argument` `structure` `🟢 open artifact`.
- [ReviewCritique](https://arxiv.org/abs/2406.16253) - Papers and human/LLM reviews with expert annotations of review deficiencies and explanations. ([Code and Data](https://github.com/jiangshdd/ReviewCritique)) Tags: `🗃️ dataset` `🔎 assess` `argument` `🛡️ audit` `🟢 open artifact`.
- [RevUtil](https://arxiv.org/abs/2509.04484) - Review comments labeled for actionability, grounding and specificity, verifiability, and helpfulness. ([Data and Code](https://github.com/bodasadallah/RevUtil)) Tags: `🗃️ dataset` `🔎 assess` `argument` `tone` `🟢 open artifact`.
- [SubstanReview](https://arxiv.org/abs/2311.11967) - Expert-annotated peer reviews for extracting review claims and the evidence used to substantiate them. ([Data and Code](https://github.com/YanzhuGuo/SubstanReview)) Tags: `🗃️ dataset` `🔎 assess` `argument` `🟢 open artifact`.

#### Review Interaction, Meta-Review, and Revision

- [ARIES](https://arxiv.org/abs/2306.12587) - Corpus linking peer-review comments to corresponding scientific paper edits, with silver training data and an expert-labeled evaluation set. Tags: `🗃️ dataset` `📝 revise` `argument` `🟡 public data`.
- [CASIMIR](https://arxiv.org/abs/2403.00241) - Corpus of multi-version OpenReview papers with sentence alignments, extracted edits, revision intents, and associated reviews. Tags: `🗃️ dataset` `📝 revise` `structure` `🟡 public data`.
- [DISAPERE](https://arxiv.org/abs/2110.08520) - Expert-annotated review-rebuttal pairs with discourse functions, aspects, polarity, and cross-document links. ([Data and Code](https://github.com/nnkennard/DISAPERE)) Tags: `🗃️ dataset` `💬 rebuttal` `argument` `structure` `polarity` `🟢 open artifact`.
- [MReD](https://arxiv.org/abs/2110.07474) - Dataset of meta-reviews with sentence-level structural labels for controllable meta-review generation. Tags: `🗃️ dataset` `🧑‍⚖️ meta` `structure` `🟡 public data`.

### Review Generation and Critique Assistance

- [Automated Focused Feedback Generation for Scientific Writing Assistance](https://arxiv.org/abs/2405.20477) - Multi-agent workflow that plans, investigates, reviews, and controls focused feedback about specific manuscript weakness types. Tags: `🤖 system` `✍️ review` `aspect` `🔵 paper`.
- [DeepReview](https://arxiv.org/abs/2503.08569) - Multi-stage review framework combining structured analysis, literature retrieval, and evidence-based argumentation. ([Project](https://ai-researcher.net/)) Tags: `🤖 system` `✍️ review` `argument` `structure` `🟣 service`.
- [MARG](https://arxiv.org/abs/2401.04259) - Multi-agent review generation approach that distributes long papers across specialized agents to improve feedback coverage and specificity. Tags: `🤖 system` `✍️ review` `aspect` `structure` `🔵 paper`.
- [OpenReviewer](https://arxiv.org/abs/2412.11948) - Open scientific-review model and system fine-tuned to generate structured, critical feedback for machine-learning papers. Tags: `🤖 system` `✍️ review` `structure` `🟢 open artifact`.
- [ReviewAdvisor](https://github.com/neulab/ReviewAdvisor) - Aspect-aware scientific review generation code, data, and models accompanying early work on automated reviewing. Tags: `🤖 system` `✍️ review` `aspect` `🟢 open artifact`.
- [ReviewAgents](https://arxiv.org/abs/2503.08506) - Multi-role reviewer-agent framework trained with structured review reasoning and evaluated on ReviewBench. Tags: `🤖 system` `✍️ review` `structure` `🔵 paper`.
- [ReviewRobot](https://arxiv.org/abs/2010.06119) - Explainable review generation system that compares paper, related-work, and background knowledge graphs. ([Code](https://github.com/EagleW/ReviewRobot)) Tags: `🤖 system` `📥 ingest` `✍️ review` `argument` `🟢 open artifact`.
- [STRICTA](https://github.com/UKPLab/acl2025-stricta) - Structured READ-EXTRACT-INFER workflow for reliable critical text assessment with human-correctable intermediate steps. Tags: `🤖 system` `✍️ review` `🔎 assess` `structure` `🟢 open artifact`.
- [TreeReview](https://arxiv.org/abs/2506.07642) - Hierarchical question-decomposition framework for deep review generation and actionable feedback with lower inference cost. ([Code and Benchmark](https://github.com/YuanChang98/tree-review)) Tags: `🤖 system` `✍️ review` `argument` `structure` `🟢 open artifact`.

### Review Analysis and Quality Assessment

- [Can Large Language Models Provide Useful Feedback on Research Papers?](https://arxiv.org/abs/2310.01783) - Large-scale comparison of GPT-generated and human feedback across ICLR and Nature-family papers. ([Project](https://github.com/Weixin-Liang/LLM-scientific-feedback)) Tags: `📏 evaluation` `✍️ review` `🔎 assess` `🟢 open artifact`.
- [Identifying Aspects in Peer Reviews](https://github.com/UKPLab/emnlp2025-aspects-in-reviews) - Resources for inducing review-aspect taxonomies and predicting which aspects papers need and reviews cover. Tags: `🤖 system` `🔎 assess` `aspect` `🟢 open artifact`.
- [Is Your Paper Being Reviewed by an LLM?](https://arxiv.org/abs/2502.19614) - Benchmark of paired AI-written and human reviews for evaluating peer-review-specific AI-text detection. Tags: `🗃️ dataset` `🔎 assess` `🛡️ audit` `🔵 paper`.
- [Mind the Blind Spots](https://arxiv.org/abs/2502.17086) - Focus-level framework for comparing how human and LLM reviews allocate attention across manuscript targets and aspects. Tags: `📏 evaluation` `🔎 assess` `aspect` `structure` `🔵 paper`.
- [Peer Reviews of Peer Reviews](https://doi.org/10.1371/journal.pone.0320444) - Randomized experiments on whether feedback about reviewing improves review quality and reviewing behavior. Tags: `📏 evaluation` `🔎 assess` `🛡️ audit` `🔵 paper`.
- [When Reviewers Lock Horns](https://github.com/sandeep82945/Contradiction-in-Peer-Review) - Dataset and models for detecting disagreement and contradiction across reviews of the same paper. Tags: `🗃️ dataset` `🔎 assess` `polarity` `🟢 open artifact`.

### Argument, Discourse, and Interaction Modeling

- [APE: Argument Pair Extraction from Peer Review and Rebuttal](https://github.com/LiyingCheng95/ArgumentPairExtraction) - Multi-task approach and resources for extracting linked argumentative spans from reviews and author rebuttals. Tags: `🤖 system` `💬 rebuttal` `argument` `🟢 open artifact`.
- [Argument Mining Driven Analysis of Peer Reviews](https://arxiv.org/abs/2012.07743) - Models PRO, CON, and non-argument spans to analyze decision-oriented reasoning in reviews. Tags: `🤖 system` `🔎 assess` `argument` `polarity` `🔵 paper`.
- [Argument Mining for Understanding Peer Reviews](https://arxiv.org/abs/1903.10104) - Introduces AMPERE and its evaluation, request, fact, reference, and quote proposition taxonomy. ([Data](https://xinyuhua.github.io/Resources/naacl19/)) Tags: `🗃️ dataset` `🔎 assess` `argument` `🟡 public data`.
- [Argument Pair Extraction via Attention-Guided Multi-Layer Multi-Cross Encoding](https://github.com/TianyuTerry/MLMC) - Cross-document encoder and code for aligning review arguments with corresponding rebuttal responses. Tags: `🤖 system` `💬 rebuttal` `argument` `🟢 open artifact`.

### Meta-Review and Decision Support

- [AgentReview](https://arxiv.org/abs/2406.12708) - LLM-agent simulation framework for studying how reviewer knowledge, commitment, intention, and social influence affect outcomes. ([Code](https://github.com/Ahren09/AgentReview)) Tags: `🤖 system` `🧑‍⚖️ meta` `🛡️ audit` `🟢 open artifact`.
- [Auto-PRE](https://arxiv.org/abs/2410.12265) - Automatic peer-review framework for evaluating language-generation systems with configurable reviewer agents. ([Code](https://github.com/cjj826/Auto-PRE)) Tags: `🤖 system` `🧑‍⚖️ meta` `📏 evaluation` `🟢 open artifact`.
- [ReviewGraph](https://github.com/relic-yuexi/ReViewGraph) - Heterogeneous graph reasoning over simulated reviewer-author debates for review and decision-support research. Tags: `🤖 system` `🧑‍⚖️ meta` `argument` `structure` `🟢 open artifact`.

> Decision-support systems should expose evidence, uncertainty, and reviewer disagreement while leaving final judgments to accountable human chairs and editors.

### Reviewer Matching and Editorial Workflow

- [OpenReview](https://openreview.net/) - Open peer-review platform with APIs, reviewer assignment infrastructure, discussions, rebuttals, and public review data. ([API](https://docs.openreview.net/)) Tags: `🛠️ tool` `👥 match` `🧑‍⚖️ meta` `💬 rebuttal` `🟣 service`.
- [OpenReview Matcher](https://github.com/openreview/openreview-matcher) - Open-source minimum-cost-flow matcher for assigning papers to reviewers under affinity and constraint settings. Tags: `🛠️ tool` `👥 match` `🟢 open artifact`.
- [Prophy Referee Finder](https://www.prophy.ai/referee-finder) - Proprietary reviewer-discovery service using publication records, semantic matching, and conflict signals. Tags: `🛠️ tool` `👥 match` `⚫ proprietary`.

### Rebuttal and Revision Support

- [arXivEdits](https://arxiv.org/abs/2210.15067) - Corpus and extraction framework for sentence alignment, fine-grained edits, and revision intentions across arXiv versions. Tags: `🗃️ dataset` `📝 revise` `structure` `🔵 paper`.
- [DEFEND](https://arxiv.org/abs/2603.27360) - Human-in-the-loop framework for evidence-grounded, segment-wise rebuttal reasoning and response drafting. Tags: `🤖 system` `💬 rebuttal` `argument` `🔵 paper`.

### Robustness, Integrity, and Risk

- [Are We There Yet? Revealing the Risks of Utilizing Large Language Models in Scholarly Peer Review](https://arxiv.org/abs/2412.01708) - Evaluates manipulation, incompleteness, prestige bias, and other risks in LLM-generated reviews. Tags: `📏 evaluation` `🛡️ audit` `polarity` `🔵 paper`.
- [Breaking the Reviewer](https://arxiv.org/abs/2506.11113) - Tests automated reviewers under textual adversarial attacks and motivates robustness-aware review evaluation. ([Code](https://github.com/Lin-TzuLing/Breaking-the-Reviewer)) Tags: `📏 evaluation` `🛡️ audit` `🟢 open artifact`.

## Infrastructure and Building Blocks

### Scientific Documents and Scholarly Data

- [ACL Anthology](https://aclanthology.org/) - Canonical open collection of computational-linguistics papers, metadata, and PDFs for literature-grounded review tools. Tags: `🛠️ tool` `📥 ingest` `🟣 service`.
- [arXiv API](https://info.arxiv.org/help/api/) - Programmatic access to preprint metadata for search, related-work retrieval, and submission monitoring. Tags: `🛠️ tool` `📥 ingest` `🟣 service`.
- [CERMINE](https://github.com/CeON/CERMINE) - Java library for extracting structured metadata, references, and text from scholarly PDFs. Tags: `🛠️ tool` `📥 ingest` `🟢 open artifact`.
- [Crossref REST API](https://www.crossref.org/documentation/retrieve-metadata/rest-api/) - DOI and publication-metadata API useful for citation verification and bibliographic normalization. Tags: `🛠️ tool` `📥 ingest` `🟣 service`.
- [GROBID](https://github.com/kermitt2/grobid) - Mature machine-learning library for converting scholarly PDFs into structured TEI XML. Tags: `🛠️ tool` `📥 ingest` `🟢 open artifact`.
- [Nougat](https://github.com/facebookresearch/nougat) - Neural document-understanding model that converts academic PDFs into structured markup. Tags: `🛠️ tool` `📥 ingest` `🟢 open artifact`.
- [OpenAlex](https://docs.openalex.org/) - Open scholarly graph and API for papers, authors, institutions, concepts, and citations. Tags: `🛠️ tool` `📥 ingest` `👥 match` `🟣 service`.
- [OpenCitations](https://opencitations.net/) - Open citation data and APIs for checking reference networks and related literature. Tags: `🛠️ tool` `📥 ingest` `🛡️ audit` `🟣 service`.
- [Open Research Knowledge Graph](https://orkg.org/) - Infrastructure for representing and comparing research contributions as structured scholarly knowledge. ([API](https://orkg.org/about/19/API)) Tags: `🛠️ tool` `📥 ingest` `argument` `🟣 service`.
- [Science Parse](https://github.com/allenai/science-parse) - Research-paper parser for metadata and bibliography extraction; useful as a reference implementation despite limited maintenance. Tags: `🛠️ tool` `📥 ingest` `🟢 open artifact`.
- [Semantic Scholar Academic Graph API](https://api.semanticscholar.org/api-docs/graph) - Scholarly metadata, citation, recommendation, and embedding endpoints for review grounding. Tags: `🛠️ tool` `📥 ingest` `👥 match` `🟣 service`.
- [S2ORC](https://arxiv.org/abs/1911.02782) - Large structured corpus of scholarly full text, citations, figures, tables, and metadata. Tags: `🗃️ dataset` `📥 ingest` `🟡 public data`.
- [Unpaywall](https://unpaywall.org/products/api) - API for locating legally available open-access versions of scholarly works. Tags: `🛠️ tool` `📥 ingest` `🟣 service`.

### Evaluation Frameworks and Judge Models

- [DeepEval](https://github.com/confident-ai/deepeval) - Open-source unit-testing framework for rubric-based LLM application evaluation. Tags: `📏 evaluation` `🔎 assess` `🟢 open artifact`.
- [G-Eval](https://arxiv.org/abs/2303.16634) - Rubric and chain-of-thought-based LLM evaluation approach adaptable to structured review-quality criteria. Tags: `📏 evaluation` `🔎 assess` `🔵 paper`.
- [Phoenix](https://github.com/Arize-ai/phoenix) - Open-source tracing and evaluation platform for inspecting retrieval, agent, and judge behavior. Tags: `📏 evaluation` `📥 ingest` `🛡️ audit` `🟢 open artifact`.
- [Prometheus](https://github.com/prometheus-eval/prometheus-eval) - Open evaluator models and tooling for reference-aware, rubric-conditioned scoring and feedback. Tags: `📏 evaluation` `🔎 assess` `🟢 open artifact`.
- [Ragas](https://github.com/explodinggradients/ragas) - Evaluation framework for retrieval-grounded generation, useful for measuring evidence relevance and faithfulness. Tags: `📏 evaluation` `📥 ingest` `🔎 assess` `🟢 open artifact`.
- [TruLens](https://github.com/truera/trulens) - Instrumentation and feedback-function framework for evaluating grounded LLM applications. Tags: `📏 evaluation` `🔎 assess` `🛡️ audit` `🟢 open artifact`.
- [YESciEval](https://arxiv.org/abs/2505.14279) - Scientific-domain LLM-as-a-judge framework with configurable evaluation aspects and evaluator qualification. Tags: `📏 evaluation` `🔎 assess` `aspect` `🟢 open artifact`.

### RAG, Agents, and Workflow Frameworks

- [AutoGen](https://github.com/microsoft/autogen) - Multi-agent application framework for prototyping specialized reviewer, evidence, and synthesis agents. Tags: `🛠️ tool` `✍️ review` `🧑‍⚖️ meta` `🟢 open artifact`.
- [CrewAI](https://github.com/crewAIInc/crewAI) - Role-based agent orchestration framework suitable for experimental review workflows. Tags: `🛠️ tool` `✍️ review` `🧑‍⚖️ meta` `🟢 open artifact`.
- [DSPy](https://github.com/stanfordnlp/dspy) - Framework for optimizing modular language-model programs, including retrieval and evaluation pipelines. Tags: `🛠️ tool` `📥 ingest` `🔎 assess` `🟢 open artifact`.
- [Haystack](https://github.com/deepset-ai/haystack) - Open framework for retrieval, document processing, and production RAG pipelines. Tags: `🛠️ tool` `📥 ingest` `🟢 open artifact`.
- [LangChain](https://github.com/langchain-ai/langchain) - General orchestration framework for retrieval, tools, structured output, and agent workflows. Tags: `🛠️ tool` `📥 ingest` `✍️ review` `🟢 open artifact`.
- [LlamaIndex](https://github.com/run-llama/llama_index) - Data and retrieval framework for building literature-grounded assistants over papers and scholarly metadata. Tags: `🛠️ tool` `📥 ingest` `🟢 open artifact`.
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel) - SDK for composing model calls, tools, memory, and agent workflows. Tags: `🛠️ tool` `✍️ review` `🧑‍⚖️ meta` `🟢 open artifact`.
- [Sentence Transformers](https://github.com/UKPLab/sentence-transformers) - Embedding and reranking toolkit for reviewer matching, related-work retrieval, and semantic review analysis. Tags: `🛠️ tool` `📥 ingest` `👥 match` `🔎 assess` `🟢 open artifact`.

## Learning Resources

- [CS224N: Natural Language Processing with Deep Learning](https://web.stanford.edu/class/cs224n/) - Stanford course covering representation learning, transformers, information extraction, and modern NLP foundations. Tags: `🎓 learning`.
- [CS25: Transformers United](https://web.stanford.edu/class/cs25/) - Public Stanford seminar series on transformer research and applications. Tags: `🎓 learning`.
- [DeepLearning.AI Short Courses](https://www.deeplearning.ai/short-courses/) - Practical courses on RAG, agents, evaluation, prompt engineering, and LLM application development. Tags: `🎓 learning` `📥 ingest` `🔎 assess`.
- [fast.ai Practical Deep Learning](https://course.fast.ai/) - Implementation-oriented deep-learning course with transferable lessons for scientific NLP models. Tags: `🎓 learning`.
- [Hugging Face LLM Course](https://huggingface.co/learn/llm-course/) - Hands-on course covering transformers, datasets, tokenizers, fine-tuning, and model sharing. Tags: `🎓 learning`.
- [LLMs from Scratch](https://github.com/rasbt/LLMs-from-scratch) - Sebastian Raschka's code-centered guide to implementing, training, and fine-tuning language models. Tags: `🎓 learning` `🟢 open artifact`.
- [nanoGPT](https://github.com/karpathy/nanoGPT) - Compact GPT training implementation for understanding core language-model mechanics. Tags: `🎓 learning` `🟢 open artifact`.
- [Neural Networks: Zero to Hero](https://github.com/karpathy/nn-zero-to-hero) - Andrej Karpathy's from-first-principles neural-network and language-model course. Tags: `🎓 learning` `🟢 open artifact`.
- [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) - Visual explanation of transformer internals useful for newcomers building scholarly NLP systems. Tags: `🎓 learning`.

## Policies, Ethics, and Governance

- [ACM Policy on Authorship](https://www.acm.org/publications/policies/new-acm-policy-on-authorship) - ACM guidance on generative-AI tools, authorship responsibility, disclosure, and publication integrity. Tags: `⚖️ policy` `🛡️ audit`.
- [ICLR Code of Ethics](https://iclr.cc/public/CodeOfEthics) - Conference ethics requirements relevant to confidentiality, responsible reviewing, and research integrity. Tags: `⚖️ policy` `🛡️ audit`.
- [Nature Portfolio Artificial Intelligence Policy](https://www.nature.com/nature-portfolio/editorial-policies/ai) - Publisher policy covering AI authorship, generative content, and reviewer confidentiality. Tags: `⚖️ policy` `🛡️ audit`.
- [NeurIPS Code of Ethics](https://neurips.cc/public/EthicsGuidelines) - Ethics guidance for authors, reviewers, and organizers in machine-learning research. Tags: `⚖️ policy` `🛡️ audit`.
- [The COPE Ethical Guidelines for Peer Reviewers](https://publicationethics.org/resources/guidelines-new/cope-ethical-guidelines-peer-reviewers) - Core guidance on confidentiality, conflicts, objectivity, timeliness, and accountability. Tags: `⚖️ policy` `🛡️ audit`.

## Evaluation Checklist

When assessing a peer-review assistant, ask:

- **Scope** - Which workflow stage, submission type, field, and venue is supported?
- **Facet coverage** - Which argument, aspect, structure, tone, and polarity dimensions are measured?
- **Grounding** - Are critiques linked to manuscript passages, citations, experiments, or external evidence?
- **Utility** - Are comments actionable, specific, verifiable, and helpful to authors?
- **Calibration** - Does the system express uncertainty and distinguish minor issues from decision-relevant weaknesses?
- **Robustness** - Has it been tested against prompt injection, paper rewriting, adversarial text, and repeated-run instability?
- **Human agreement** - Is evaluation calibrated against qualified reviewers rather than only model-based judges?
- **Process fit** - Are humans able to inspect, correct, override, and take responsibility for outputs?
- **Data governance** - Are licenses, consent, confidentiality, provenance, and access restrictions explicit?
- **Reproducibility** - Are prompts, models, retrieval sources, rubrics, versions, and evaluation settings documented?

## Open Gaps

- Multidisciplinary, multilingual, and non-conference review corpora remain limited.
- Few resources connect review comments, rebuttals, manuscript versions, editorial discussion, and final decisions end to end.
- Novelty, significance, and methodological validity remain difficult to evaluate reliably without domain experts.
- Review-quality benchmarks need stronger tests of evidence grounding, calibration, fairness, and long-document reasoning.
- Multi-agent review systems need reproducibility checks across repeated runs and changing model versions.
- Reviewer matching needs transparent evaluation of conflicts, workload, diversity, and expertise beyond topical similarity.
- Policy guidance is evolving faster than technical benchmarks, especially around confidentiality and permissible reviewer assistance.
- More datasets need clear licenses, ethical release documentation, and machine-readable provenance.

## Related Awesome Lists

- [Awesome AI Agents](https://github.com/e2b-dev/awesome-ai-agents#readme) - Agent frameworks, platforms, and applied autonomous-system resources.
- [Awesome LLM](https://github.com/Hannibal046/Awesome-LLM#readme) - Broad collection of large-language-model research and engineering resources.
- [Awesome LLM Evaluation](https://github.com/CSHaitao/Awesome-LLMs-as-Judges#readme) - Research on LLM judges, evaluator bias, robustness, and benchmarking.
- [Awesome Peer Review](https://github.com/formula12/Awesome-Peer-Review#readme) - Broad bibliography of automated and computational scientific peer-review research.
- [Awesome RAG](https://github.com/hymie122/RAG-Survey#readme) - Retrieval-augmented generation papers, benchmarks, and methods.
- [Awesome Scientific Language Models](https://github.com/yuzhimanhua/Awesome-Scientific-Language-Models#readme) - Models and datasets for scientific language understanding and generation.

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request. Add each resource to one primary section and use the compact tag vocabulary above.

## License

The original taxonomy, selection, organization, and descriptive text in this repository are released under the [Creative Commons Attribution 4.0 International License](LICENSE). Please credit this repository when reusing or adapting the curated work. Linked resources remain governed by their own licenses and terms.

## Acknowledgements

This catalog was developed from original literature review and taxonomy research, supplemented by public primary sources and community-maintained research artifacts.

The initial repository structure and editorial pass were assisted by [OpenAI Codex](https://openai.com/codex/). Resource selection, interpretation, and maintenance remain human-led.
