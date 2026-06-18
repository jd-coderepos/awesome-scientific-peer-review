# Awesome Scientific Peer Review [![Awesome](https://awesome.re/badge-flat.svg)](https://awesome.re)

[![License: CC BY 4.0](https://img.shields.io/badge/license-CC%20BY%204.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/) [![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)

A curated list of datasets, tools, papers, models, benchmarks, and workflows for AI-assisted scientific peer review.

The list covers systems that assist with reviewing, evaluation, editorial workflows, rebuttals, revision, auditing, and the study of peer review. Generic AI infrastructure is included only where its relevance to scientific reviewing is direct and explained.

> [!IMPORTANT]
> Scientific peer review requires expert judgment, confidentiality, fairness, and accountability. The resources below should support human reviewers and editors, not replace responsible human decision-making.

## Contents

- [Taxonomy](#taxonomy)
- [Surveys and Overviews](#surveys-and-overviews)
- [Core Datasets and Benchmarks](#core-datasets-and-benchmarks)
- [Peer Review Generation and Critique Assistance](#peer-review-generation-and-critique-assistance)
- [Review Analysis and Quality Evaluation](#review-analysis-and-quality-evaluation)
- [Argument Mining, Discourse, and Review-Rebuttal Structure](#argument-mining-discourse-and-review-rebuttal-structure)
- [Meta-Review, Decision Support, and Reviewer Discussion](#meta-review-decision-support-and-reviewer-discussion)
- [Reviewer Matching and Editorial Workflow Tools](#reviewer-matching-and-editorial-workflow-tools)
- [Rebuttal, Author Response, and Revision Support](#rebuttal-author-response-and-revision-support)
- [Scientific Document Parsing and Scholarly Metadata](#scientific-document-parsing-and-scholarly-metadata)
- [Evaluation Frameworks and Judge Models](#evaluation-frameworks-and-judge-models)
- [RAG, Agents, and Workflow Building Blocks](#rag-agents-and-workflow-building-blocks)
- [Educational Resources and Tutorials](#educational-resources-and-tutorials)
- [Policies, Ethics, and Governance](#policies-ethics-and-governance)
- [Related Awesome Lists](#related-awesome-lists)

## Taxonomy

The same resource may address more than one stage or evaluation facet. This list uses two complementary views so that readers can navigate by workflow need and by the quality dimension being modeled.

### Peer Review Workflow Taxonomy

- **Manuscript ingestion and parsing** - Extracting sections, references, figures, tables, equations, and metadata from submissions.
- **Reviewer matching and conflict-of-interest support** - Finding qualified reviewers while checking expertise, workload, relationships, and conflicts.
- **Review generation and critique assistance** - Drafting structured feedback, identifying possible weaknesses, and retrieving supporting literature.
- **Review analysis and quality assessment** - Measuring grounding, coverage, usefulness, professionalism, and reasoning quality in reviews.
- **Meta-review and decision support** - Synthesizing reviews and discussions for human area chairs and editors.
- **Rebuttal and author-response support** - Linking review points to responses and helping authors prepare evidence-grounded replies.
- **Revision and review-to-edit alignment** - Connecting comments to manuscript changes and studying revision intent.
- **Auditing, robustness, bias, and policy** - Testing manipulation resistance, calibration, fairness, confidentiality, and governance.
- **Infrastructure and reusable building blocks** - Scholarly data, retrieval, evaluation, and agent frameworks used to build review assistants.

### Evaluation-Facet Taxonomy

Peer review resources operate at two evaluation levels:

- **Paper review evaluation facets** - Criteria used within reviews to assess a manuscript.
- **Peer review evaluation facets** - Criteria used to assess the review itself.

Across both levels, five facet families recur:

- **Argument facets** - Evaluation, request, fact, reference, quote, substantiation, claim-evidence links, actionability, argument completeness, and review-rebuttal links.
- **Content aspect facets** - Novelty, originality, soundness, correctness, clarity, substance, impact, appropriateness, meaningful comparison, replicability, and methodological validity.
- **Structure facets** - Review organization, summary-strengths-weaknesses-conclusion structure, discourse functions, review-rebuttal interaction, paper-section links, and multi-stage workflows.
- **Sentiment facets** - Politeness, harshness, helpfulness, interpersonal tone, and aspect-conditioned sentiment.
- **Polarity facets** - Strengths versus weaknesses, accept/reject orientation, disagreement, contradiction, hedging, uncertainty, calibration, and bias.

## Surveys and Overviews

- [Can AI Be a Good Peer Reviewer? A Survey of Peer Review Process, Evaluation, and the Future](https://arxiv.org/abs/2604.27924) - Surveys generation, rebuttal, meta-review, revision, evaluation, and governance across the full AI-assisted review workflow.
- [Can We Automate Scientific Reviewing?](https://arxiv.org/abs/2102.00176) - Foundational study of aspect-aware review generation, evaluation criteria, and the limitations of automatically generated scientific feedback.
- [Challenges, Experiments, and Computational Solutions in Peer Review](https://doi.org/10.1145/3528086) - Reviews computational approaches to reviewer assignment, review quality, incentives, bias, and large-conference experimentation.
- [Reviewer Assignment Problem: A Scoping Review](https://arxiv.org/abs/2305.07887) - Synthesizes computational reviewer-matching methods, selection criteria, representations, and evaluation practices.
- [What Can Natural Language Processing Do for Peer Review?](https://arxiv.org/abs/2405.06563) - Maps opportunities and risks for NLP assistance from submission through camera-ready revision. ([Companion Resources](https://github.com/OAfzal/nlp-for-peer-review))

## Core Datasets and Benchmarks

- [ARIES](https://arxiv.org/abs/2306.12587) - Corpus linking peer-review comments to corresponding scientific paper edits, with silver training data and an expert-labeled evaluation set.
- [Aspect-Based Sentiment Analysis of Scientific Reviews](https://arxiv.org/abs/2006.03257) - Dataset and models for manuscript-aspect prediction, aspect-conditioned sentiment, and reviewer disagreement analysis.
- [CASIMIR](https://arxiv.org/abs/2403.00241) - Corpus of multi-version OpenReview papers with sentence alignments, extracted edits, revision intents, and associated reviews.
- [DISAPERE](https://arxiv.org/abs/2110.08520) - Expert-annotated review-rebuttal pairs with discourse functions, aspects, polarity, and cross-document links. ([Data and Code](https://github.com/nnkennard/DISAPERE))
- [F1000RD](https://arxiv.org/abs/2204.10805) - Multidomain corpus for pragmatic tagging, intertextual links, and document-version alignment in open journal peer review. ([Data and Code](https://github.com/UKPLab/f1000rd))
- [GenReview](https://arxiv.org/abs/2510.21192) - Large dataset pairing human reviews with controlled positive, neutral, and negative LLM-generated reviews for ICLR submissions. ([Data](https://anonymous.4open.science/r/gen_review))
- [HedgePeer](https://github.com/Tirthankar-Ghosal/HedgePeer-Dataset) - Dataset of hedge cues and spans for studying uncertainty and reviewer calibration.
- [LazyReview](https://arxiv.org/abs/2504.11042) - Peer-review sentences labeled with fine-grained lazy-thinking patterns for training review-quality diagnostics. ([Data and Code](https://github.com/UKPLab/acl2025-lazy-review))
- [MOPRD](https://arxiv.org/abs/2212.04972) - Multidisciplinary open peer-review dataset containing manuscript versions, reviews, meta-reviews, rebuttals, and editorial decisions.
- [MReD](https://arxiv.org/abs/2110.07474) - Dataset of meta-reviews with sentence-level structural labels for controllable meta-review generation.
- [NLPeer](https://arxiv.org/abs/2211.06651) - Ethically sourced multidomain corpus of papers, reviews, decisions, and revisions in a unified structured representation. ([Data and Code](https://github.com/UKPLab/nlpeer))
- [PeerRead](https://aclanthology.org/N18-1145/) - Foundational dataset of scientific papers, reviews, aspect scores, and acceptance decisions from major computer science venues. ([Data and Code](https://github.com/allenai/PeerRead))
- [Peer Review Analyze](https://doi.org/10.1371/journal.pone.0259238) - Benchmark with sentence-level purpose, significance, sentiment, section correspondence, and manuscript-aspect annotations.
- [ReAct](https://arxiv.org/abs/2210.00443) - OpenReview comment dataset labeled for actionability and functional review-comment types. ([Data](https://github.com/gtmdotme/ReAct))
- [ReviewCritique](https://arxiv.org/abs/2406.16253) - Papers and human/LLM reviews with expert annotations of review deficiencies and explanations. ([Code and Data](https://github.com/jiangshdd/ReviewCritique))
- [RevUtil](https://arxiv.org/abs/2509.04484) - Review comments labeled for actionability, grounding and specificity, verifiability, and helpfulness. ([Data and Code](https://github.com/bodasadallah/RevUtil))
- [SubstanReview](https://arxiv.org/abs/2311.11967) - Expert-annotated peer reviews for extracting review claims and the evidence used to substantiate them. ([Data and Code](https://github.com/YanzhuGuo/SubstanReview))

## Peer Review Generation and Critique Assistance

- [Automated Focused Feedback Generation for Scientific Writing Assistance](https://arxiv.org/abs/2405.20477) - Multi-agent workflow that plans, investigates, reviews, and controls focused feedback about specific manuscript weakness types.
- [DeepReview](https://arxiv.org/abs/2503.08569) - Multi-stage review framework combining structured analysis, literature retrieval, and evidence-based argumentation. ([Project](https://ai-researcher.net/))
- [MARG](https://arxiv.org/abs/2401.04259) - Multi-agent review generation approach that distributes long papers across specialized agents to improve feedback coverage and specificity.
- [OpenReviewer](https://arxiv.org/abs/2412.11948) - Open scientific-review model and system fine-tuned to generate structured, critical feedback for machine-learning papers.
- [ReviewAdvisor](https://github.com/neulab/ReviewAdvisor) - Aspect-aware scientific review generation code, data, and models accompanying early work on automated reviewing.
- [ReviewAgents](https://arxiv.org/abs/2503.08506) - Multi-role reviewer-agent framework trained with structured review reasoning and evaluated on ReviewBench.
- [ReviewRobot](https://arxiv.org/abs/2010.06119) - Explainable review generation system that compares paper, related-work, and background knowledge graphs. ([Code](https://github.com/EagleW/ReviewRobot))
- [STRICTA](https://github.com/UKPLab/acl2025-stricta) - Structured READ-EXTRACT-INFER workflow for reliable critical text assessment with human-correctable intermediate steps.
- [TreeReview](https://arxiv.org/abs/2506.07642) - Hierarchical question-decomposition framework for deep review generation and actionable feedback with lower inference cost. ([Code and Benchmark](https://github.com/YuanChang98/tree-review))

## Review Analysis and Quality Evaluation

- [Are We There Yet? Revealing the Risks of Utilizing Large Language Models in Scholarly Peer Review](https://arxiv.org/abs/2412.01708) - Evaluates manipulation, incompleteness, prestige bias, and other risks in LLM-generated reviews.
- [Breaking the Reviewer](https://arxiv.org/abs/2506.11113) - Tests automated reviewers under textual adversarial attacks and motivates robustness-aware review evaluation. ([Code](https://github.com/Lin-TzuLing/Breaking-the-Reviewer))
- [Can Large Language Models Provide Useful Feedback on Research Papers?](https://arxiv.org/abs/2310.01783) - Large-scale comparison of GPT-generated and human feedback across ICLR and Nature-family papers. ([Project](https://github.com/Weixin-Liang/LLM-scientific-feedback))
- [Identifying Aspects in Peer Reviews](https://github.com/UKPLab/emnlp2025-aspects-in-reviews) - Resources for inducing review-aspect taxonomies and predicting which aspects papers need and reviews cover.
- [Is Your Paper Being Reviewed by an LLM?](https://arxiv.org/abs/2502.19614) - Benchmark of paired AI-written and human reviews for evaluating peer-review-specific AI-text detection.
- [Mind the Blind Spots](https://arxiv.org/abs/2502.17086) - Focus-level framework for comparing how human and LLM reviews allocate attention across manuscript targets and aspects.
- [Peer Reviews of Peer Reviews](https://doi.org/10.1371/journal.pone.0320444) - Randomized experiments on whether feedback about reviewing improves review quality and reviewing behavior.
- [When Reviewers Lock Horns](https://github.com/sandeep82945/Contradiction-in-Peer-Review) - Dataset and models for detecting disagreement and contradiction across reviews of the same paper.

## Argument Mining, Discourse, and Review-Rebuttal Structure

- [APE: Argument Pair Extraction from Peer Review and Rebuttal](https://github.com/LiyingCheng95/ArgumentPairExtraction) - Multi-task approach and resources for extracting linked argumentative spans from reviews and author rebuttals.
- [Argument Mining Driven Analysis of Peer Reviews](https://arxiv.org/abs/2012.07743) - Models PRO, CON, and non-argument spans to analyze decision-oriented reasoning in reviews.
- [Argument Mining for Understanding Peer Reviews](https://arxiv.org/abs/1903.10104) - Introduces AMPERE and its evaluation, request, fact, reference, and quote proposition taxonomy. ([Data](https://xinyuhua.github.io/Resources/naacl19/))
- [Argument Pair Extraction via Attention-Guided Multi-Layer Multi-Cross Encoding](https://github.com/TianyuTerry/MLMC) - Cross-document encoder and code for aligning review arguments with corresponding rebuttal responses.

## Meta-Review, Decision Support, and Reviewer Discussion

- [AgentReview](https://arxiv.org/abs/2406.12708) - LLM-agent simulation framework for studying how reviewer knowledge, commitment, intention, and social influence affect outcomes. ([Code](https://github.com/Ahren09/AgentReview))
- [Auto-PRE](https://arxiv.org/abs/2410.12265) - Automatic peer-review framework for evaluating language-generation systems with configurable reviewer agents. ([Code](https://github.com/cjj826/Auto-PRE))
- [ReviewGraph](https://github.com/relic-yuexi/ReViewGraph) - Heterogeneous graph reasoning over simulated reviewer-author debates for review and decision-support research.

Decision-support systems should expose evidence, uncertainty, and reviewer disagreement while leaving final judgments to accountable human chairs and editors.

## Reviewer Matching and Editorial Workflow Tools

- [OpenReview](https://openreview.net/) - Open peer-review platform with APIs, reviewer assignment infrastructure, discussions, rebuttals, and public review data. ([API](https://docs.openreview.net/))
- [OpenReview Matcher](https://github.com/openreview/openreview-matcher) - Open-source minimum-cost-flow matcher for assigning papers to reviewers under affinity and constraint settings.
- [Prophy Referee Finder](https://www.prophy.ai/referee-finder) - Proprietary reviewer-discovery service using publication records, semantic matching, and conflict signals.

## Rebuttal, Author Response, and Revision Support

- [arXivEdits](https://arxiv.org/abs/2210.15067) - Corpus and extraction framework for sentence alignment, fine-grained edits, and revision intentions across arXiv versions.
- [DEFEND](https://arxiv.org/abs/2603.27360) - Human-in-the-loop framework for evidence-grounded, segment-wise rebuttal reasoning and response drafting.

## Scientific Document Parsing and Scholarly Metadata

- [ACL Anthology](https://aclanthology.org/) - Canonical open collection of computational-linguistics papers, metadata, and PDFs for literature-grounded review tools.
- [arXiv API](https://info.arxiv.org/help/api/) - Programmatic access to preprint metadata for search, related-work retrieval, and submission monitoring.
- [CERMINE](https://github.com/CeON/CERMINE) - Java library for extracting structured metadata, references, and text from scholarly PDFs.
- [Crossref REST API](https://www.crossref.org/documentation/retrieve-metadata/rest-api/) - DOI and publication-metadata API useful for citation verification and bibliographic normalization.
- [GROBID](https://github.com/kermitt2/grobid) - Mature machine-learning library for converting scholarly PDFs into structured TEI XML.
- [Nougat](https://github.com/facebookresearch/nougat) - Neural document-understanding model that converts academic PDFs into structured markup.
- [OpenAlex](https://docs.openalex.org/) - Open scholarly graph and API for papers, authors, institutions, concepts, and citations.
- [OpenCitations](https://opencitations.net/) - Open citation data and APIs for checking reference networks and related literature.
- [Open Research Knowledge Graph](https://orkg.org/) - Infrastructure for representing and comparing research contributions as structured scholarly knowledge. ([API](https://orkg.org/about/19/API))
- [Science Parse](https://github.com/allenai/science-parse) - Research-paper parser for metadata and bibliography extraction; useful as a reference implementation despite limited maintenance.
- [Semantic Scholar Academic Graph API](https://api.semanticscholar.org/api-docs/graph) - Scholarly metadata, citation, recommendation, and embedding endpoints for review grounding.
- [S2ORC](https://arxiv.org/abs/1911.02782) - Large structured corpus of scholarly full text, citations, figures, tables, and metadata.
- [Unpaywall](https://unpaywall.org/products/api) - API for locating legally available open-access versions of scholarly works.

## Evaluation Frameworks and Judge Models

- [DeepEval](https://github.com/confident-ai/deepeval) - Open-source unit-testing framework for rubric-based LLM application evaluation.
- [G-Eval](https://arxiv.org/abs/2303.16634) - Rubric and chain-of-thought-based LLM evaluation approach adaptable to structured review-quality criteria.
- [Phoenix](https://github.com/Arize-ai/phoenix) - Open-source tracing and evaluation platform for inspecting retrieval, agent, and judge behavior.
- [Prometheus](https://github.com/prometheus-eval/prometheus-eval) - Open evaluator models and tooling for reference-aware, rubric-conditioned scoring and feedback.
- [Ragas](https://github.com/explodinggradients/ragas) - Evaluation framework for retrieval-grounded generation, useful for measuring evidence relevance and faithfulness.
- [TruLens](https://github.com/truera/trulens) - Instrumentation and feedback-function framework for evaluating grounded LLM applications.
- [YESciEval](https://arxiv.org/abs/2505.14279) - Scientific-domain LLM-as-a-judge framework with configurable evaluation aspects and evaluator qualification.

## RAG, Agents, and Workflow Building Blocks

- [AutoGen](https://github.com/microsoft/autogen) - Multi-agent application framework for prototyping specialized reviewer, evidence, and synthesis agents.
- [CrewAI](https://github.com/crewAIInc/crewAI) - Role-based agent orchestration framework suitable for experimental review workflows.
- [DSPy](https://github.com/stanfordnlp/dspy) - Framework for optimizing modular language-model programs, including retrieval and evaluation pipelines.
- [Haystack](https://github.com/deepset-ai/haystack) - Open framework for retrieval, document processing, and production RAG pipelines.
- [LangChain](https://github.com/langchain-ai/langchain) - General orchestration framework for retrieval, tools, structured output, and agent workflows.
- [LlamaIndex](https://github.com/run-llama/llama_index) - Data and retrieval framework for building literature-grounded assistants over papers and scholarly metadata.
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel) - SDK for composing model calls, tools, memory, and agent workflows.
- [Sentence Transformers](https://github.com/UKPLab/sentence-transformers) - Embedding and reranking toolkit for reviewer matching, related-work retrieval, and semantic review analysis.

## Educational Resources and Tutorials

- [CS224N: Natural Language Processing with Deep Learning](https://web.stanford.edu/class/cs224n/) - Stanford course covering representation learning, transformers, information extraction, and modern NLP foundations.
- [CS25: Transformers United](https://web.stanford.edu/class/cs25/) - Public Stanford seminar series on transformer research and applications.
- [DeepLearning.AI Short Courses](https://www.deeplearning.ai/short-courses/) - Practical courses on RAG, agents, evaluation, prompt engineering, and LLM application development.
- [fast.ai Practical Deep Learning](https://course.fast.ai/) - Implementation-oriented deep-learning course with transferable lessons for scientific NLP models.
- [Hugging Face LLM Course](https://huggingface.co/learn/llm-course/) - Hands-on course covering transformers, datasets, tokenizers, fine-tuning, and model sharing.
- [LLMs from Scratch](https://github.com/rasbt/LLMs-from-scratch) - Sebastian Raschka's code-centered guide to implementing, training, and fine-tuning language models.
- [nanoGPT](https://github.com/karpathy/nanoGPT) - Compact GPT training implementation for understanding core language-model mechanics.
- [Neural Networks: Zero to Hero](https://github.com/karpathy/nn-zero-to-hero) - Andrej Karpathy's from-first-principles neural-network and language-model course.
- [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) - Visual explanation of transformer internals useful for newcomers building scholarly NLP systems.

## Policies, Ethics, and Governance

- [ACM Policy on Authorship](https://www.acm.org/publications/policies/new-acm-policy-on-authorship) - ACM guidance on generative-AI tools, authorship responsibility, disclosure, and publication integrity.
- [ICLR Code of Ethics](https://iclr.cc/public/CodeOfEthics) - Conference ethics requirements relevant to confidentiality, responsible reviewing, and research integrity.
- [NeurIPS Code of Ethics](https://neurips.cc/public/EthicsGuidelines) - Ethics guidance for authors, reviewers, and organizers in machine-learning research.
- [Nature Portfolio Artificial Intelligence Policy](https://www.nature.com/nature-portfolio/editorial-policies/ai) - Publisher policy covering AI authorship, generative content, and reviewer confidentiality.
- [The COPE Ethical Guidelines for Peer Reviewers](https://publicationethics.org/resources/guidelines-new/cope-ethical-guidelines-peer-reviewers) - Core guidance on confidentiality, conflicts, objectivity, timeliness, and accountability.

## Related Awesome Lists

- [Awesome AI Agents](https://github.com/e2b-dev/awesome-ai-agents#readme) - Agent frameworks, platforms, and applied autonomous-system resources.
- [Awesome LLM](https://github.com/Hannibal046/Awesome-LLM#readme) - Broad collection of large-language-model research and engineering resources.
- [Awesome LLM Evaluation](https://github.com/CSHaitao/Awesome-LLMs-as-Judges#readme) - Research on LLM judges, evaluator bias, robustness, and benchmarking.
- [Awesome Peer Review](https://github.com/formula12/Awesome-Peer-Review#readme) - Broad bibliography of automated and computational scientific peer-review research.
- [Awesome RAG](https://github.com/hymie122/RAG-Survey#readme) - Retrieval-augmented generation papers, benchmarks, and methods.
- [Awesome Scientific Language Models](https://github.com/yuzhimanhua/Awesome-Scientific-Language-Models#readme) - Models and datasets for scientific language understanding and generation.

## Contributing

Contributions are welcome. Please read the [contribution guidelines](CONTRIBUTING.md) before opening a pull request.

## Footnotes

This list curates public resources and does not endorse uploading confidential manuscripts to third-party services. Check the data license, venue policy, privacy conditions, and model provider terms before using any resource in a real review workflow.

The original taxonomy, selection, organization, and descriptive text in this repository are released under the [Creative Commons Attribution 4.0 International License](LICENSE). Please credit this repository when reusing or adapting the curated work. Linked resources remain governed by their own licenses and terms.
