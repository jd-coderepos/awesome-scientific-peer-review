<p align="center">
  <img src="assets/banner.png" alt="Awesome Scientific Peer Review">
</p>

<!--lint disable double-link-->

<p align="center">
  <a href="https://awesome.re"><img src="https://awesome.re/badge-flat.svg" alt="Awesome"></a>
  <a href="https://creativecommons.org/licenses/by/4.0/"><img src="https://img.shields.io/badge/license-CC%20BY%204.0-blue.svg" alt="License: CC BY 4.0"></a>
  <a href="#contributing"><img src="https://img.shields.io/badge/contributions-welcome-brightgreen.svg" alt="Contributions Welcome"></a>
</p>

A curated, taxonomy-aware catalog of datasets, systems, tools, and evaluation resources for AI-assisted scientific peer review.

> [!IMPORTANT]
> Scientific peer review requires expert judgment, confidentiality, fairness, and accountability. These resources should support human reviewers and editors, not replace responsible human decision-making.

<!--lint disable table-pipe-alignment-->

## Contents

<!--lint disable awesome-toc-->

- [📖 How to Use This Catalog](#-how-to-use-this-catalog)
- [🧭 Browse by Task](#-browse-by-task)
- [📐 Peer Review Evaluation Taxonomy](#-peer-review-evaluation-taxonomy)
- [🗂️ Datasets and Benchmarks](#️-datasets-and-benchmarks)
- [⚙️ Systems and Methods](#️-systems-and-methods)
- [🧱 Infrastructure and Building Blocks](#-infrastructure-and-building-blocks)
- [🏛️ Policies, Ethics, and Governance](#️-policies-ethics-and-governance)
- [📚 Surveys and Field Studies](#-surveys-and-field-studies)
- [✅ Evaluation Checklist](#-evaluation-checklist)
- [🔭 Open Gaps](#-open-gaps)
- [🔗 Related Awesome Lists](#-related-awesome-lists)
- [🤝 Contributing](#-contributing)
- [✨ Acknowledgements](#-acknowledgements)

<!--lint enable awesome-toc-->

## 📖 How to Use This Catalog

Every named resource is linked to its primary paper, repository, dataset, API, or official product page. Entries appear once in the canonical catalogs; the task and taxonomy tables are linked indexes into those resources.

### Visual Legend

<!--lint disable awesome-list-item-->

| Dimension | Symbols |
| --- | --- |
| Resource | 🟦 dataset/benchmark · 🟩 code/tool · 🟪 system/model · 🟨 paper/survey · 🟥 policy/commercial |
| Access | ✅ open artifact · 📦 open data · 📄 paper only · 🌐 hosted service/API · 🔒 proprietary · ⚠️ access unclear |
| Workflow | 📥 ingest · 👥 match · ✍️ review · 🔍 assess · 🧑‍⚖️ meta-review · ↔️ rebuttal · 📝 revision · 🛡️ audit |
| Taxonomy facet | 🧩 argument · 🎯 content aspect · 🧱 structure · 💬 sentiment · ⚖️ polarity |

<!--lint enable awesome-list-item-->

## 🧭 Browse by Task

| Goal | Start with | Baseline or comparison |
| --- | --- | --- |
| Generate a scientific review | [NLPeer](https://github.com/UKPLab/nlpeer), [PeerRead](https://github.com/allenai/PeerRead) | Structured LLM prompt; compare with [ReviewAdvisor](https://github.com/neulab/ReviewAdvisor), [ReviewRobot](https://github.com/EagleW/ReviewRobot), or [TreeReview](https://github.com/YuanChang98/tree-review). |
| Evaluate review usefulness | [RevUtil](https://github.com/bodasadallah/RevUtil), [ReAct](https://github.com/gtmdotme/ReAct) | Classify actionability/helpfulness; add grounding checks from [SubstanReview](https://github.com/YanzhuGuo/SubstanReview). |
| Detect weak or deficient critiques | [ReviewCritique](https://github.com/jiangshdd/ReviewCritique), [LazyReview](https://github.com/UKPLab/acl2025-lazy-review) | Rubric-based classifier or LLM judge with human validation. |
| Measure aspect coverage and blind spots | [PeerRead](https://aclanthology.org/N18-1145/), [Peer Review Analyze](https://doi.org/10.1371/journal.pone.0259238) | Sentence-level aspect classifier; compare focus allocation with [Mind the Blind Spots](https://arxiv.org/abs/2502.17086). |
| Mine arguments in reviews | [AMPERE](https://xinyuhua.github.io/Resources/naacl19/), [Argument Mining Driven Analysis](https://arxiv.org/abs/2012.07743) | Proposition classifier for evaluation, request, fact, reference, and quote. |
| Link reviews and rebuttals | [DISAPERE](https://github.com/nnkennard/DISAPERE), [APE](https://github.com/LiyingCheng95/ArgumentPairExtraction) | Sentence-pair similarity or NLI; compare with [MLMC](https://github.com/TianyuTerry/MLMC). |
| Generate or evaluate meta-reviews | [MReD](https://arxiv.org/abs/2110.07474), [ReviewAgents](https://arxiv.org/abs/2503.08506) | Structured synthesis that preserves disagreement and uncertainty. |
| Align reviews with manuscript changes | [ARIES](https://arxiv.org/abs/2306.12587), [CASIMIR](https://arxiv.org/abs/2403.00241), [F1000RD](https://github.com/UKPLab/f1000rd) | Sentence alignment between review comments and edited spans. |
| Match reviewers to papers | [OpenReview Matcher](https://github.com/openreview/openreview-matcher) | Abstract/publication similarity using [Sentence Transformers](https://github.com/UKPLab/sentence-transformers), then add conflicts and workload constraints. |
| Build a literature-grounded assistant | [GROBID](https://github.com/kermitt2/grobid), [Semantic Scholar API](https://api.semanticscholar.org/api-docs/graph), [OpenAlex](https://docs.openalex.org/) | Parse → retrieve → critique; evaluate retrieval and faithfulness with [Ragas](https://github.com/explodinggradients/ragas) or [TruLens](https://github.com/truera/trulens). |
| Evaluate an LLM reviewer | [ReviewCritique](https://github.com/jiangshdd/ReviewCritique), [RevUtil](https://github.com/bodasadallah/RevUtil), [YESciEval](https://arxiv.org/abs/2505.14279) | Multidimensional rubric plus qualified human review; do not rely on one scalar score. |
| Audit robustness or gaming | [Breaking the Reviewer](https://github.com/Lin-TzuLing/Breaking-the-Reviewer), [Are We There Yet?](https://arxiv.org/abs/2412.01708) | Repeated runs, paper rewrites, adversarial phrasing, and prompt-injection tests. |

## 📐 Peer Review Evaluation Taxonomy

The catalog incorporates the two-level taxonomy from the attached research paper. **Paper review evaluation facets** describe what a review evaluates about the manuscript. **Peer review evaluation facets** describe how well the review itself performs that evaluation.

The five facet families below are cross-cutting. They are useful both for choosing datasets and for designing evaluation modules.

| Facet family | Paper review evaluation | Peer review evaluation | Representative resources |
| --- | --- | --- | --- |
| 🧩 **Argument** | Evaluations, requests, facts, references, claims, evidence, and review-rebuttal links. | Actionability, substantiation, argument completeness, balance, and deficiency types. | [AMPERE](https://xinyuhua.github.io/Resources/naacl19/), [APE](https://github.com/LiyingCheng95/ArgumentPairExtraction), [DISAPERE](https://github.com/nnkennard/DISAPERE), [ReAct](https://github.com/gtmdotme/ReAct), [SubstanReview](https://github.com/YanzhuGuo/SubstanReview), [RevUtil](https://github.com/bodasadallah/RevUtil), [ReviewCritique](https://github.com/jiangshdd/ReviewCritique). |
| 🎯 **Content aspect** | Novelty, originality, soundness, correctness, clarity, substance, impact, comparison, appropriateness, and replicability. | Coverage, balance, attention skew, and omission of important manuscript weaknesses. | [PeerRead](https://aclanthology.org/N18-1145/), [Peer Review Analyze](https://doi.org/10.1371/journal.pone.0259238), [ReviewAdvisor](https://github.com/neulab/ReviewAdvisor), [Identifying Aspects in Peer Reviews](https://github.com/UKPLab/emnlp2025-aspects-in-reviews), [Mind the Blind Spots](https://arxiv.org/abs/2502.17086). |
| 🧱 **Structure** | Summary-strengths-weaknesses-conclusion organization, question trees, causal workflows, and links to manuscript sections. | Pragmatic composition, review-rebuttal interaction, cross-round evolution, and revision structure. | [F1000RD](https://github.com/UKPLab/f1000rd), [NLPeer](https://github.com/UKPLab/nlpeer), [MReD](https://arxiv.org/abs/2110.07474), [DISAPERE](https://github.com/nnkennard/DISAPERE), [TreeReview](https://github.com/YuanChang98/tree-review), [STRICTA](https://github.com/UKPLab/acl2025-stricta). |
| 💬 **Sentiment** | Aspect-conditioned positive or negative sentiment about manuscript properties. | Politeness, harshness, helpfulness, and interpersonal tone. | [Aspect-Based Sentiment Analysis](https://arxiv.org/abs/2006.03257), [Peer Review Analyze](https://doi.org/10.1371/journal.pone.0259238), [RevUtil](https://github.com/bodasadallah/RevUtil), [Peer Reviews of Peer Reviews](https://doi.org/10.1371/journal.pone.0320444). |
| ⚖️ **Polarity** | Strength versus weakness, accept-supporting versus reject-supporting arguments, disagreement, and contradiction. | Positivity bias, contradiction, confidence, uncertainty, hedging, and calibration. | [Argument Mining Driven Analysis](https://arxiv.org/abs/2012.07743), [When Reviewers Lock Horns](https://github.com/sandeep82945/Contradiction-in-Peer-Review), [HedgePeer](https://github.com/Tirthankar-Ghosal/HedgePeer-Dataset), [Breaking the Reviewer](https://github.com/Lin-TzuLing/Breaking-the-Reviewer). |

### Taxonomy-Aligned Evaluation Blueprint

A practical reviewer-assistance evaluation should combine:

1. 🎯 **Content-aspect coverage** - Did the review inspect the criteria that matter for this paper and venue?
2. 🧩 **Argument and grounding** - Are criticisms specific, justified, and linked to manuscript evidence?
3. 🧱 **Structure and interaction** - Is feedback organized, traceable, and responsive across reviews, rebuttals, and revisions?
4. 💬 **Utility and tone** - Is the review professional and useful to authors?
5. ⚖️ **Polarity and calibration** - Are strengths, weaknesses, disagreement, and uncertainty represented faithfully?
6. 🛡️ **Robustness and integrity** - Is the system stable under manipulation, repetition, and changing model conditions?

## 🗂️ Datasets and Benchmarks

This is the canonical dataset catalog. Access symbols describe the linked artifact, not every upstream source from which the dataset was derived.

| Resource | Best for | Contains | Facets | Access |
| --- | --- | --- | --- | --- |
| [PeerRead](https://github.com/allenai/PeerRead) | Review generation, score prediction, aspect modeling | Papers, reviews, scores, decisions | 🎯 ⚖️ | 🟦 ✅ |
| [NLPeer](https://github.com/UKPLab/nlpeer) | Cross-domain review modeling and guided reading | Papers, reviews, decisions, revisions | 🎯 🧱 | 🟦 ✅ |
| [MOPRD](https://arxiv.org/abs/2212.04972) | Multidisciplinary, multi-round workflows | Manuscript versions, reviews, rebuttals, meta-reviews, decisions | 🧩 🧱 | 🟦 📄 |
| [F1000RD](https://github.com/UKPLab/f1000rd) | Pragmatic roles, intertextual links, revision histories | Open-review articles, reviews, versions, links | 🧩 🧱 | 🟦 ✅ |
| [AMPERE](https://xinyuhua.github.io/Resources/naacl19/) | Review argument mining | Reviews, proposition spans, argument roles | 🧩 | 🟦 📦 |
| [DISAPERE](https://github.com/nnkennard/DISAPERE) | Review-rebuttal discourse and linking | Reviews, rebuttals, discourse/aspect/polarity labels, links | 🧩 🧱 ⚖️ | 🟦 ✅ |
| [MReD](https://arxiv.org/abs/2110.07474) | Meta-review generation | Reviews, meta-reviews, structural labels | 🧱 | 🟦 📄 |
| [Peer Review Analyze](https://doi.org/10.1371/journal.pone.0259238) | Purpose, section, aspect, and sentiment analysis | Reviews with multilayer sentence labels | 🎯 🧱 💬 | 🟦 ⚠️ |
| [ReAct](https://github.com/gtmdotme/ReAct) | Actionability and comment function | Review comments, actionability/function labels | 🧩 | 🟦 ✅ |
| [RevUtil](https://github.com/bodasadallah/RevUtil) | Review utility | Comments, actionability, grounding, verifiability, helpfulness | 🧩 💬 | 🟦 ✅ |
| [ReviewCritique](https://github.com/jiangshdd/ReviewCritique) | Deficiency detection | Papers, reviews, deficiency labels, explanations | 🧩 | 🟦 ✅ |
| [LazyReview](https://github.com/UKPLab/acl2025-lazy-review) | Lazy-thinking and critique failure modes | Review sentences, cognitive-deficiency categories | 🧩 ⚖️ | 🟦 ✅ |
| [SubstanReview](https://github.com/YanzhuGuo/SubstanReview) | Claim-evidence grounding | Review claims and supporting evidence links | 🧩 | 🟦 ✅ |
| [ARIES](https://arxiv.org/abs/2306.12587) | Review-to-edit alignment | Review comments and manuscript edits | 🧩 🧱 | 🟦 📄 |
| [CASIMIR](https://arxiv.org/abs/2403.00241) | Revision intent and version alignment | Paper versions, aligned sentences, revision intents, reviews | 🧱 | 🟦 📄 |
| [HedgePeer](https://github.com/Tirthankar-Ghosal/HedgePeer-Dataset) | Uncertainty and calibration language | Reviews, hedge cues, hedge spans | ⚖️ | 🟦 ✅ |
| [ASAP-Review](https://aclanthology.org/2023.ijcnlp-srw.6/) | Aspect-informed score prediction | Review comments and reported aspect/sentiment annotations | 🎯 💬 | 🟦 ⚠️ |
| [CiteTracked](https://pure.itu.dk/portal/da/publications/0270dbc3-5fa8-4b2c-8e65-3a867f5f8cb4) | Longitudinal review-impact analysis | ML papers, review text, citation counts | 🎯 | 🟦 📄 |
| [GenReview](https://anonymous.4open.science/r/gen_review) | Human versus controlled LLM-review comparison | Human and positive/neutral/negative generated reviews | 💬 ⚖️ | 🟦 📦 |
| [arXivEdits](https://arxiv.org/abs/2210.15067) | General scientific revision modeling | Aligned arXiv versions, edits, revision intents | 🧱 | 🟦 📄 |

## ⚙️ Systems and Methods

### ✍️ Review Generation and Critique

- 🟪 ✅ [ReviewAdvisor](https://github.com/neulab/ReviewAdvisor) - Aspect-aware extract-then-generate baseline for summary, originality, soundness, comparison, and replicability.
- 🟪 ✅ [ReviewRobot](https://github.com/EagleW/ReviewRobot) - Explainable review generation using paper, related-work, and background knowledge graphs.
- 🟪 📄 [Automated Focused Feedback Generation](https://arxiv.org/abs/2405.20477) - Planner-investigator-reviewer-controller workflow for targeted manuscript weaknesses.
- 🟪 📄 [MARG](https://arxiv.org/abs/2401.04259) - Leader-worker and aspect-specialist agents for long-paper review generation.
- 🟪 ✅ [OpenReviewer](https://arxiv.org/abs/2412.11948) - Open scientific-review model for structured critique of machine-learning papers.
- 🟪 📄 [ReviewAgents](https://arxiv.org/abs/2503.08506) - Multiple reviewer agents plus an area-chair agent for review and meta-review synthesis.
- 🟪 ✅ [TreeReview](https://github.com/YuanChang98/tree-review) - Dynamic question-tree decomposition with answer sufficiency checks.
- 🟪 ✅ [STRICTA](https://github.com/UKPLab/acl2025-stricta) - Human-correctable READ-EXTRACT-INFER workflow for critical assessment.
- 🟪 🌐 [DeepReview](https://ai-researcher.net/) - Staged novelty verification, retrieval-grounded reviewing, and reliability checking.

### 🔍 Review Quality and Facet Evaluation

- 🟪 ✅ [Identifying Aspects in Peer Reviews](https://github.com/UKPLab/emnlp2025-aspects-in-reviews) - Paper Aspect Prediction and Review Aspect Prediction for expected versus observed review coverage.
- 🟨 📄 [Mind the Blind Spots](https://arxiv.org/abs/2502.17086) - Focus-level comparison of review targets and evaluation aspects.
- 🟨 📄 [Aspect-Based Sentiment Analysis of Scientific Reviews](https://arxiv.org/abs/2006.03257) - Aspect-conditioned sentiment and reviewer-disagreement modeling.
- 🟨 📄 [Peer Reviews of Peer Reviews](https://doi.org/10.1371/journal.pone.0320444) - Randomized experiments on feedback about reviewing behavior and quality.
- 🟨 📄 [Can Large Language Models Provide Useful Feedback on Research Papers?](https://arxiv.org/abs/2310.01783) - Large-scale human/LLM feedback comparison. ([Project](https://github.com/Weixin-Liang/LLM-scientific-feedback))
- 🟨 📄 [Is Your Paper Being Reviewed by an LLM?](https://arxiv.org/abs/2502.19614) - Benchmark for detecting AI-generated peer reviews.

### 🧩 Argument, Rebuttal, and Interaction

- 🟪 ✅ [APE](https://github.com/LiyingCheng95/ArgumentPairExtraction) - Joint argument-span extraction and review-rebuttal pairing.
- 🟪 ✅ [MLMC](https://github.com/TianyuTerry/MLMC) - Attention-guided cross-sequence model for argument-pair extraction.
- 🟨 📄 [Argument Mining Driven Analysis of Peer Reviews](https://arxiv.org/abs/2012.07743) - PRO/CON/NON modeling relative to paper acceptability.
- 🟩 ✅ [When Reviewers Lock Horns](https://github.com/sandeep82945/Contradiction-in-Peer-Review) - Contradiction and disagreement detection across reviews.
- 🟪 📄 [DEFEND](https://arxiv.org/abs/2603.27360) - Human-in-the-loop, evidence-grounded rebuttal reasoning and drafting.

### 🧑‍⚖️ Meta-Review and Decision Support

- 🟪 ✅ [AgentReview](https://github.com/Ahren09/AgentReview) - Simulation of reviewer commitment, knowledgeability, intention, discussion, and decision drift.
- 🟪 ✅ [Auto-PRE](https://github.com/cjj826/Auto-PRE) - Configurable reviewer-agent framework for evaluating language-generation systems.
- 🟪 ✅ [ReviewGraph](https://github.com/relic-yuexi/ReViewGraph) - Heterogeneous graph reasoning over simulated reviewer-author debates.

> Decision-support systems should expose evidence, uncertainty, and reviewer disagreement while leaving final judgments to accountable human chairs and editors.

### 👥 Reviewer Matching and Editorial Workflow

- 🟩 🌐 [OpenReview](https://openreview.net/) - Peer-review platform with public APIs, assignments, discussions, rebuttals, and review data. ([API Documentation](https://docs.openreview.net/))
- 🟩 ✅ [OpenReview Matcher](https://github.com/openreview/openreview-matcher) - Minimum-cost-flow assignment under affinities and constraints.
- 🟥 🔒 [Prophy Referee Finder](https://www.prophy.ai/referee-finder) - Commercial reviewer discovery using publication records, semantic matching, and conflict signals.

### 🛡️ Robustness and Integrity

- 🟨 📄 [Are We There Yet?](https://arxiv.org/abs/2412.01708) - Tests manipulation, incompleteness, prestige bias, and other risks of LLM reviewing.
- 🟪 ✅ [Breaking the Reviewer](https://github.com/Lin-TzuLing/Breaking-the-Reviewer) - Adversarial attacks against automated paper-reviewing systems.
- 🟨 📄 [Stop Automating Peer Review Without Rigorous Evaluation](https://arxiv.org/abs/2605.03202) - Studies review homogenization and score gaming through paper rewriting.

## 🧱 Infrastructure and Building Blocks

### 📥 Scientific Document Parsing and Scholarly Retrieval

- 🟩 ✅ [GROBID](https://github.com/kermitt2/grobid) - Converts scholarly PDFs into structured TEI XML.
- 🟩 ✅ [CERMINE](https://github.com/CeON/CERMINE) - Extracts metadata, references, and text from scholarly PDFs.
- 🟩 ✅ [Nougat](https://github.com/facebookresearch/nougat) - Neural PDF-to-markup model for academic documents.
- 🟩 ✅ [Science Parse](https://github.com/allenai/science-parse) - Metadata and bibliography parser retained as a reference implementation.
- 🟩 🌐 [Semantic Scholar Academic Graph API](https://api.semanticscholar.org/api-docs/graph) - Paper, author, citation, recommendation, and embedding endpoints.
- 🟩 🌐 [OpenAlex](https://docs.openalex.org/) - Open scholarly graph for works, authors, institutions, concepts, and citations.
- 🟩 🌐 [Crossref REST API](https://www.crossref.org/documentation/retrieve-metadata/rest-api/) - DOI metadata and bibliographic normalization.
- 🟩 🌐 [OpenCitations](https://opencitations.net/) - Open citation data and APIs.
- 🟩 🌐 [arXiv API](https://info.arxiv.org/help/api/) - Preprint metadata and search.
- 🟩 🌐 [ACL Anthology](https://aclanthology.org/) - Open computational-linguistics papers, metadata, and PDFs.
- 🟩 🌐 [Open Research Knowledge Graph](https://orkg.org/) - Structured comparison of research contributions. ([API](https://orkg.org/about/19/API))
- 🟦 📦 [S2ORC](https://arxiv.org/abs/1911.02782) - Structured scholarly text, citations, figures, tables, and metadata.
- 🟩 🌐 [Unpaywall](https://unpaywall.org/products/api) - Legally available open-access locations for scholarly works.
- 🟩 ✅ [Sentence Transformers](https://github.com/UKPLab/sentence-transformers) - Embeddings and reranking for reviewer matching and literature retrieval.

### 🔍 Evaluation Frameworks and Judge Models

- 🟪 ✅ [YESciEval](https://arxiv.org/abs/2505.14279) - Configurable scientific-domain LLM-as-a-judge framework with evaluator qualification.
- 🟪 ✅ [Prometheus](https://github.com/prometheus-eval/prometheus-eval) - Open rubric-conditioned evaluator models.
- 🟨 📄 [G-Eval](https://arxiv.org/abs/2303.16634) - Rubric and chain-of-thought-based LLM evaluation method.
- 🟩 ✅ [DeepEval](https://github.com/confident-ai/deepeval) - Unit-testing framework for LLM applications.
- 🟩 ✅ [Ragas](https://github.com/explodinggradients/ragas) - Retrieval relevance, grounding, and faithfulness evaluation.
- 🟩 ✅ [TruLens](https://github.com/truera/trulens) - Tracing and feedback functions for grounded LLM applications.
- 🟩 ✅ [Phoenix](https://github.com/Arize-ai/phoenix) - Tracing and evaluation for retrieval, agents, and judges.

### General RAG and Agent Frameworks

These are reusable building blocks, not peer-review-specific systems.

- 🟩 ✅ [LlamaIndex](https://github.com/run-llama/llama_index) - Data and retrieval framework for literature-grounded assistants.
- 🟩 ✅ [Haystack](https://github.com/deepset-ai/haystack) - Retrieval, document processing, and production RAG pipelines.
- 🟩 ✅ [LangChain](https://github.com/langchain-ai/langchain) - Retrieval, tools, structured output, and agent orchestration.
- 🟩 ✅ [DSPy](https://github.com/stanfordnlp/dspy) - Optimization of modular language-model programs.
- 🟩 ✅ [AutoGen](https://github.com/microsoft/autogen) - Multi-agent application framework.
- 🟩 ✅ [CrewAI](https://github.com/crewAIInc/crewAI) - Role-based agent orchestration.
- 🟩 ✅ [Semantic Kernel](https://github.com/microsoft/semantic-kernel) - SDK for model calls, tools, memory, and agents.

## 🏛️ Policies, Ethics, and Governance

- 🟥 📄 [COPE Ethical Guidelines for Peer Reviewers](https://publicationethics.org/resources/guidelines-new/cope-ethical-guidelines-peer-reviewers) - Confidentiality, conflicts, objectivity, timeliness, and accountability.
- 🟥 📄 [Nature Portfolio Artificial Intelligence Policy](https://www.nature.com/nature-portfolio/editorial-policies/ai) - AI authorship, generated content, and reviewer confidentiality.
- 🟥 📄 [ACM Policy on Authorship](https://www.acm.org/publications/policies/new-acm-policy-on-authorship) - Generative AI, authorship responsibility, disclosure, and publication integrity.
- 🟥 📄 [ICLR Code of Ethics](https://iclr.cc/public/CodeOfEthics) - Ethics requirements relevant to confidential and responsible reviewing.
- 🟥 📄 [NeurIPS Code of Ethics](https://neurips.cc/public/EthicsGuidelines) - Ethics guidance for authors, reviewers, and organizers.

## 📚 Surveys and Field Studies

- 🟨 📄 [Can AI Be a Good Peer Reviewer?](https://arxiv.org/abs/2604.27924) - Survey of review generation, rebuttal, meta-review, revision, evaluation, and governance.
- 🟨 📄 [What Can Natural Language Processing Do for Peer Review?](https://arxiv.org/abs/2405.06563) - Task and dataset survey spanning the review workflow. ([Companion Resources](https://github.com/OAfzal/nlp-for-peer-review))
- 🟨 📄 [Can We Automate Scientific Reviewing?](https://arxiv.org/abs/2102.00176) - Foundational analysis of aspect-aware review generation and evaluation.
- 🟨 📄 [Challenges, Experiments, and Computational Solutions in Peer Review](https://doi.org/10.1145/3528086) - Reviewer assignment, review quality, incentives, bias, and conference experiments.
- 🟨 📄 [Reviewer Assignment Problem: A Scoping Review](https://arxiv.org/abs/2305.07887) - Reviewer-matching methods, criteria, representations, and evaluation.

<!--lint disable awesome-list-item-->

## ✅ Evaluation Checklist

- **Coverage:** Does the review inspect the manuscript aspects that matter for its type and venue?
- **Grounding:** Are critiques linked to manuscript passages, experiments, references, or retrieved evidence?
- **Utility:** Are comments actionable, specific, verifiable, and helpful?
- **Structure:** Are summary, strengths, weaknesses, requests, and conclusions organized and traceable?
- **Tone:** Is feedback professional without hiding legitimate criticism?
- **Calibration:** Are uncertainty, confidence, and decision relevance represented appropriately?
- **Human agreement:** Has the system been validated by qualified reviewers rather than only model judges?
- **Robustness:** Is it stable under repeated runs, rewrites, adversarial text, and prompt injection?
- **Governance:** Are confidentiality, provenance, licensing, disclosure, and accountability explicit?
- **Reproducibility:** Are models, prompts, retrieval sources, rubrics, and versions documented?

## 🔭 Open Gaps

- Multidisciplinary, multilingual, and non-conference review corpora remain limited.
- Few datasets connect reviews, rebuttals, revisions, editorial discussion, and decisions end to end.
- Novelty, significance, and methodological validity still require strong domain expertise.
- Review-quality benchmarks need better grounding, calibration, fairness, and long-document tests.
- Multi-agent systems need reproducibility checks across runs and model versions.
- Reviewer matching needs transparent conflict, workload, diversity, seniority, and recency evaluation.
- More datasets need clear licenses, ethical release documentation, and machine-readable provenance.

<!--lint enable awesome-list-item-->

## 🔗 Related Awesome Lists

- [Awesome Peer Review](https://github.com/formula12/Awesome-Peer-Review#readme) - Broader bibliography of computational peer-review research.
- [Awesome Scientific Language Models](https://github.com/yuzhimanhua/Awesome-Scientific-Language-Models#readme) - Scientific language models and datasets.
- [Awesome LLM Evaluation](https://github.com/CSHaitao/Awesome-LLMs-as-Judges#readme) - LLM judges, evaluator bias, robustness, and benchmarking.
- [Awesome RAG](https://github.com/hymie122/RAG-Survey#readme) - Retrieval-augmented generation methods and benchmarks.
- [Awesome AI Agents](https://github.com/e2b-dev/awesome-ai-agents#readme) - Agent frameworks and applications.
- [Awesome LLM](https://github.com/Hannibal046/Awesome-LLM#readme) - General large-language-model research and engineering.

## 🤝 Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md). Add each resource to one canonical catalog location and use the visual symbols from the legend.

## ✨ Acknowledgements

This catalog was developed from original literature review and taxonomy research, including the two-level, five-family evaluation taxonomy summarized above.

The initial repository structure and editorial work were assisted by [OpenAI Codex](https://openai.com/codex/). Resource selection, interpretation, and maintenance remain human-led.

<!--lint enable double-link table-pipe-alignment-->
