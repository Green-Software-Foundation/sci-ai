# Software Carbon Intensity for AI Specification

## Introduction

This document extends the Software Carbon Intensity (SCI) methodology specified in ISO/IEC 21031:2024 to address the distinctive architecture, resource requirements, and operational patterns of artificial intelligence (AI) systems. It provides a standardized method for measuring and reporting the carbon emissions associated with AI systems throughout their life cycle.

This document is intended to:

- provide a consistent framework for measuring the carbon footprint of AI systems;
- enable meaningful comparison between different AI implementations;
- guide practitioners in making environmentally responsible decisions in AI development and deployment;
- incentivize carbon efficiency improvements across the AI system life cycle.

## Scope

This document specifies a method for measuring, calculating and reporting the carbon intensity of artificial intelligence (AI) systems, as an extension of ISO/IEC 21031:2024. It specifies AI system life cycle stages, persona-based software boundaries for SCI consumers and SCI providers, and the functional units applicable to each persona.

This document is applicable to a broad range of AI system types, including classical machine learning, generative AI and agentic AI. Annex A lists the AI system types addressed.

This document does not specify:

- the accounting of carbon offsets or other market-based measures;
- environmental impacts other than carbon emissions;
- conformity assessment procedures.

## Normative references

The following documents are referred to in the text in such a way that some or all of their content constitutes requirements of this document. For dated references, only the edition cited applies. For undated references, the latest edition of the referenced document (including any amendments) applies.

- ISO/IEC 21031:2024, Information technology — Software Carbon Intensity (SCI) specification
- ISO/IEC 22989:2022, Information technology — Artificial intelligence — Artificial intelligence concepts and terminology

## Terms and definitions

For the purposes of this document, the terms and definitions given in ISO/IEC 21031:2024, ISO/IEC 22989:2022, and the following apply.

ISO and IEC maintain terminological databases for use in standardization at the following addresses:

- ISO Online browsing platform: available at https://www.iso.org/obp
- IEC Electropedia: available at https://www.electropedia.org/

T.1
**functional unit**
quantified performance characteristic of an AI system that serves as the reference unit for carbon intensity calculation

Note 1 to entry: This definition adapts the functional unit (R) specified in ISO/IEC 21031:2024, Clause [number to be confirmed], to AI-specific reference units.

T.2
**SCI consumer**
entity that uses an AI system during its operation and monitoring stage

T.3
**SCI provider**
entity that conceives, develops, deploys or retires an AI system

Note 1 to entry: An entity can act as both an SCI consumer and an SCI provider.

T.4
**persona**
category of entity, defined by its sphere of control over the carbon emissions of an AI system, for which a distinct software boundary is specified

Note 1 to entry: This document specifies two personas: SCI consumer (T.2) and SCI provider (T.3).

T.5
**software boundary**
set of software components and supporting infrastructure included in the calculation of an SCI score

T.6
**operational emissions**
carbon emissions resulting from the energy consumed by the hardware on which software runs

T.7
**embodied emissions**
share of the carbon emissions from the manufacture and disposal of hardware that is allocated to the software running on that hardware

T.8
**material**
<emission source> of a magnitude such that its omission could change the reported SCI score to an extent that could influence decisions based on that score

T.9
**inference**
process of using a trained AI model to make predictions or generate outputs based on input data

T.10
**token**
unit into which input or output data is segmented for processing by an AI model

Note 1 to entry: In language models, a token commonly represents a word, part of a word or a character. In models that process other modalities, a token can represent, for example, an image patch or a segment of audio.

T.11
**floating-point operation**
**FLOP**
single arithmetic operation, such as an addition or a multiplication, performed on floating-point numbers

Note 1 to entry: "FLOPs" denotes a count of floating-point operations and is distinct from "FLOPS" (floating-point operations per second).

Note 2 to entry: The number of FLOPs for a given workload can vary with the numeric precision used.

T.12
**gross value**
total quantity of a metric reported without adjustment for actual usage or contribution

T.13
**effective value**
quantity of a metric that reflects actual usage or meaningful contribution rather than an unadjusted total

T.14
**agentic AI**
AI system that autonomously plans and executes sequences of actions, which can include invoking tools, services or other AI models, to achieve specified goals

T.15
**market-based measure**
financial instrument intended to neutralize, offset or reallocate carbon emissions

## Symbols and abbreviated terms

For the purposes of this document, the following symbols and abbreviated terms apply.

### Symbols

| Symbol | Meaning |
|---|---|
| C | total carbon emissions within a software boundary (O + M) |
| E | energy consumed by a software system |
| I | region-specific carbon intensity |
| M | embodied emissions allocated to a software system |
| O | operational emissions (E × I) |
| R | functional unit |

### Abbreviated terms

| Abbreviation | Term |
|---|---|
| AI | artificial intelligence |
| API | application programming interface |
| CER | Certified Emission Reduction |
| CO₂e | carbon dioxide equivalent |
| EAC | Electricity Attribute Certificate |
| ERU | Emission Reduction Unit |
| FinOps | financial operations |
| FLOP | floating-point operation |
| LLM | large language model |
| ML | machine learning |
| NLP | natural language processing |
| OCR | optical character recognition |
| PPA | Power Purchase Agreement |
| REC | Renewable Energy Credit |
| RMU | Removal Unit |
| SBTi | Science Based Targets initiative |
| SCI | Software Carbon Intensity |
| UX | user experience |

## AI system life cycle stages

For the purpose of measuring carbon emissions, the AI system life cycle is divided into the following stages.

### Inception

The inception stage involves defining the AI problem, assessing whether AI is the appropriate solution, engaging with end-users, and establishing performance objectives and computational constraints.

### Design and development

The design and development stage includes data collection from various sources, preprocessing (cleaning and normalizing), generating synthetic data when appropriate to reduce the need for excessive data collection, model selection, feature engineering, distributed training setup, evaluation metric definition, resource allocation, benchmarking, and computational resource optimization.

### Deployment

The deployment stage involves incorporating the AI model into larger systems, designing component interactions, connecting with external applications, and testing for integration errors before deployment.

### Operation and monitoring

The operation and monitoring stage includes model deployment for inference, orchestration of autonomous workflows and models (e.g., in agentic AI), integration of model tools and services, monitoring performance metrics, implementing maintenance protocols, and applying practices, such as FinOps, across edge devices, data centers, and cloud environments.

### Retirement

The retirement stage involves decommissioning AI systems no longer maintained in runtime environments and properly handling associated resources and data.

## Persona-based software boundary definition

This document defines software boundaries based on two personas, SCI consumer and SCI provider, each with different spheres of control and agency over the AI system's carbon footprint.

### Consumer boundary

The Consumer boundary shall include all components related to the operation and monitoring stage, including but not limited to:

- API and inference
- Orchestration
- Scaling
- Observability and monitoring
- Data and feature management
- Storage and artifacts
- UX and client-side
- Model tool and service connectors

### Provider boundary

The Provider boundary shall include all components related to the following life cycle stages:

- Inception
- Design and development
- Deployment
- Retirement

This includes:
- Project scoping and planning systems
- Data collection systems
- Data preprocessing and cleaning systems
- Synthetic data generation
- Model development and training infrastructure
- Feature engineering systems
- Distributed training systems
- Model evaluation and benchmarking
- Optimization and efficiency analysis
- System integration and orchestration
- Testing and validation systems
- Model tool systems

## AI system life cycle coverage

In accordance with ISO/IEC 21031:2024, an SCI score is calculated using Formula (1):

SCI = C / R          (1)

where

C = O + M          (2)

O = E × I          (3)

and

- SCI is the Software Carbon Intensity score;
- C is the total carbon emissions within the software boundary;
- O is the operational emissions;
- M is the embodied emissions allocated to the software system;
- E is the energy consumed by the software system;
- I is the region-specific carbon intensity;
- R is the functional unit.

This document applies the SCI methodology separately within the Consumer and Provider boundaries, accounting for O and M arising from systems and activities attributable to each persona across the applicable AI system life cycle stages. The following subclauses specify, stage by stage, which emissions are included within each persona boundary and whether their inclusion is mandatory or conditional.

### Inception (Provider)

Systems used in the inception stage shall be included in the Provider SCI calculation when material; they may be included when not material.

### Design and development (Provider)

All carbon emissions associated with systems used in the design and development stage shall be included in the Provider SCI calculation, including:

- Data collection, preprocessing, and cleaning systems
- Synthetic data generation
- Compute, storage, and networking resources for model training stages (including, but not limited to, pre-training, mid-training and post-training)
- Distributed training infrastructure
- Model selection and benchmarking systems
- Evaluation frameworks

Emissions from model training shall be calculated over the entire training duration, including but not limited to, accounting for all epochs, steps, parameter updates, intermediate and test runs, early stopping phases, failed or aborted training runs, hyperparameter tuning and search sweeps, and discarded or superseded model checkpoints.

### Deployment (Provider)

All carbon emissions associated with systems used in the deployment stage shall be included in the Provider SCI calculation.

### Operation and monitoring (Consumer)

All carbon emissions associated with systems used in the operation and monitoring stage shall be included in the Consumer SCI calculation.

### Retirement (Consumer and Provider)

Systems used in the retirement stage shall be included in the SCI calculation when material; they may be included when not material.

## Functional units

### Consumer functional units

Consumer functional units represent the measurable unit of AI service consumption used to normalize carbon emissions within the Consumer boundary. The functional unit should align with how the AI service is delivered, consumed, or billed.

Table 1 provides suggested examples of commonly used functional units. Given the diversity of AI system types and consumption models, these examples are indicative and not exhaustive.

**Table 1 — Suggested consumer functional units by AI system type**

| AI system type | Suggested functional unit |
|---|---|
| Large language models (LLMs) | Per token |
| Video generation | Per second |
| Image generation | Per image |
| Agentic AI | Per workflow execution |
| OCR/document analysis | Per page processed |
| Classical machine learning (e.g., classification) | Per inference |
| Machine translation | Per character translated |
| Speech recognition | Per second of audio processed |
| Text-to-speech | Per character of text processed |

NOTE   For an AI service that involves multiple model calls, tool invocations or service integrations, a single functional unit can encompass model executions, tool usage, retrieval steps, model-to-model exchanges and other operations performed to deliver that unit.

### Provider functional units

Provider functional units shall be one of the metrics shown in Table 2, to normalize carbon emissions during AI model training. The choice of unit should reflect the primary optimization focus of the SCI provider's system design, training strategy, or architecture. Each unit supports different efficiency objectives and carbon reduction strategies. Guidance on selecting a provider functional unit is given in Annex B.

**Table 2 — Provider functional units and efficiency focus**

| Functional unit | Description | Efficiency focus |
|---|---|---|
| Per FLOP | Carbon emissions per floating-point operation | Algorithmic and hardware efficiency |
| Per training token | Carbon emissions per token in training data | Data quality and curation efficiency |
| Per 10⁹ parameters | Carbon emissions per 10⁹ model parameters | Model architecture efficiency |

#### Reporting expectations

SCI providers shall state:

- the chosen functional unit and the rationale for its selection;
- whether emissions are normalized using gross values (T.12) or effective values (T.13);
- any strategies, assumptions, or methodologies that are material to the reported results (e.g., pruning, sparse activation, synthetic data use).

SCI providers should also state any strategies, assumptions, or methodologies that are potentially valuable for others to adopt.

NOTE 1   Examples of gross values are total parameters in the model, total tokens in a raw dataset, or total theoretical FLOPs. Examples of effective values are active parameters used per inference (for sparse models), deduplicated or curated tokens, or utilized FLOPs during computation.

NOTE 2   Reporting effective values gives a more realistic picture of efficiency by recognizing carbon savings from optimizations such as pruning, deduplication, or sparse activations.

SCI providers may report multiple functional units where feasible, to give a comprehensive view of efficiency across compute, data, and model design dimensions.

EXAMPLE   An organization training a language model might report:
- 0,45 g CO₂e per 10¹² FLOPs, reflecting gains from switching to energy-efficient hardware;
- 0,18 g CO₂e per 1 000 training tokens, reflecting curation of the training dataset; and
- 20 kg CO₂e per 10⁹ parameters, reflecting pruning of inactive model weights.

## Exclusions

### General

The focus of this document is elimination, not offsetting. One tonne of carbon eliminated from an AI system's operation is not equivalent to one tonne of carbon that has been offset. The preferable goal is to avoid emitting the carbon in the first place, rather than compensating for it after the fact, consistent with the mitigation hierarchy set out in [1].

Only actions that eliminate emissions reduce a Consumer or Provider SCI score. An SCI for AI score shall not be reduced through carbon offsets, such as market-based measures.

### Market-based measures

Market-based measures (T.15) include, but are not limited to, the following:

- carbon offsets or credits;
- a Removal Unit (RMU);
- an Emission Reduction Unit (ERU);
- a Certified Emission Reduction (CER);
- Electricity Attribute Certificates (EACs);
- Power Purchase Agreements (PPAs);
- Renewable Energy Credits (RECs).

NOTE   These exclusions apply equally to Consumer and Provider SCI calculations. For example, an SCI provider's use of PPAs or RECs to claim clean energy sourcing for model training does not reduce the Provider SCI score; only genuine reductions in energy consumption, hardware footprint, or grid carbon intensity do.

## Annex A (informative) AI system types

The AI system types addressed by this document are grouped as follows. The groupings are illustrative.

### A.1 AI paradigms (foundational approaches)
- Machine learning (ML)
  - Supervised learning
  - Unsupervised learning
  - Reinforcement learning
  - Deep learning
- Symbolic AI (classical AI)
- Probabilistic and Bayesian AI
- Evolutionary algorithms
- Fuzzy logic
- Hybrid AI (combining multiple paradigms)

### A.2 Application-specific AI solutions
- Predictive analytics
- Prescriptive analytics
- Computer vision
- Natural language processing (NLP)
- Speech recognition/processing

### A.3 Emerging AI technologies
- Generative AI
  - Text generation (e.g., LLMs)
  - Image generation
  - Video generation
  - Music generation
  - Code generation
- Agentic AI (autonomous decision-making)

## Annex B (informative) Guidance on provider functional unit selection

- Per FLOP is best suited for evaluating compute efficiency and incentivizes algorithmic improvements and optimized hardware utilization.
- Per training token aligns with data-centric strategies and encourages deduplication, curation, and synthetic augmentation.
- Per 10⁹ parameters emphasizes compact, purposeful model designs, especially when adjusted for activation sparsity.

Allowing a choice of provider functional unit lets SCI providers transparently highlight their optimization focus while avoiding misleading comparisons.

## Annex C (informative) Implementation examples

This annex provides examples of how to apply this document in real-world scenarios, demonstrating how to combine software boundaries and functional units to calculate meaningful SCI scores.

### C.1 Large language model (LLM) example

For a typical large language model service, two separate SCI scores can be calculated and reported.

#### C.1.1 Consumer SCI calculation

**Functional unit**: Per token

**Boundary**: Operation and monitoring (inference services, API infrastructure, monitoring systems)

**Calculation method**:

1. Measure all operational emissions (O) within the Consumer boundary over a defined period (e.g., one week):
   - Carbon emitted by inference servers
   - Carbon emitted by API gateways and load balancers
   - Carbon emitted by monitoring and observability systems
   - Carbon emitted by caching and data storage
2. Calculate embodied emissions (M) for all hardware within the Consumer boundary over the defined period.
3. Sum operational and embodied emissions to obtain total Consumer carbon emissions (C), using Formula (2).
4. Count the total number of tokens processed during the same period (R).
5. Calculate the Consumer SCI using Formula (1).

EXAMPLE
- Total Consumer operational emissions: 5 000 kg CO₂e/week
- Total Consumer embodied emissions: 1 500 kg CO₂e/week
- Total tokens processed: 50 × 10⁹ tokens/week
- Consumer SCI = 6 500 kg CO₂e ÷ (50 × 10⁹ tokens) = 130 kg CO₂e per 10⁹ tokens

#### C.1.2 Provider SCI calculation

**Functional unit**: Per FLOP, per 10⁹ parameters, or per training token (this example uses per FLOP)

**Boundary**: Inception, design and development, deployment, retirement

**Calculation method**:

1. Measure all operational emissions (O) within the Provider boundary:
   - Carbon emitted during data collection and processing
   - Carbon emitted during model training
   - Carbon emitted during model optimization and testing
   - Carbon emitted during system integration
2. Calculate embodied emissions (M) for all hardware within the Provider boundary.
3. Sum operational and embodied emissions to obtain total Provider carbon emissions (C), using Formula (2).
4. Calculate the total number of FLOPs used (R).
5. Calculate the Provider SCI using Formula (1).

EXAMPLE
- Total Provider operational emissions: 180 000 kg CO₂e
- Total Provider embodied emissions: 20 000 kg CO₂e
- Total FLOPs used: 5 × 10²² FLOPs
- Provider SCI = 200 000 kg CO₂e ÷ (5 × 10²² FLOPs) = 4 × 10⁻¹⁸ kg CO₂e/FLOP = 4 g CO₂e per 10¹⁵ FLOPs

#### C.1.3 Reporting

For an LLM the following SCI values can be reported:

- Consumer SCI: 130 kg CO₂e per 10⁹ tokens
- Provider SCI: 4 g CO₂e per 10¹⁵ FLOPs

### C.2 Computer vision model example

For a computer vision model used for image classification:

#### C.2.1 Consumer SCI calculation

**Functional unit**: Per inference

**Boundary**: Operation and monitoring

EXAMPLE
- Total Consumer emissions: 3 200 kg CO₂e/month
- Total inferences: 40 × 10⁶ per month
- Consumer SCI = 3 200 kg CO₂e ÷ (40 × 10⁶ inferences) = 0,08 g CO₂e/inference

#### C.2.2 Provider SCI calculation

**Functional unit**: Per 10⁹ parameters

**Boundary**: Inception, design and development, deployment, retirement

EXAMPLE
- Total Provider emissions: 75 000 kg CO₂e
- Total parameters: 2,5 × 10⁹
- Provider SCI = 75 000 kg CO₂e ÷ (2,5 × 10⁹ parameters) = 30 000 kg CO₂e per 10⁹ parameters

#### C.2.3 Reporting

For a computer vision model the following SCI values can be reported:

- Consumer SCI: 0,08 g CO₂e/inference
- Provider SCI: 30 000 kg CO₂e per 10⁹ parameters

## Bibliography

[1] The Net-Zero STANDARD, Science Based Targets initiative (SBTi), https://sciencebasedtargets.org/net-zero

[2] ISO/IEC 5338:2023, Information technology — Artificial intelligence — AI system life cycle processes
