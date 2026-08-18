# Software Carbon Intensity for AI Specification

## Introduction

This document extends the Software Carbon Intensity (SCI) methodology specified in ISO/IEC 21031:2024 to address the distinctive architecture, resource requirements, and operational patterns of artificial intelligence (AI) systems. It provides a standardized method for measuring and reporting the carbon emissions associated with AI systems throughout their lifecycle.

This document is intended to:

- provide a consistent framework for measuring the carbon footprint of AI systems;
- enable meaningful comparison between different AI implementations;
- guide practitioners in making environmentally responsible decisions in AI development and deployment;
- incentivize carbon efficiency improvements across the AI lifecycle.

## Scope

This document specifies a method for measuring, calculating, and reporting the carbon intensity of artificial intelligence (AI) systems. It applies to a broad range of AI system types, including classical machine learning, generative AI, and agentic AI, and is intended to remain applicable as new AI paradigms and architectures emerge.

The AI system types addressed by this document are grouped as follows.

### AI paradigms (foundational approaches)
- Machine Learning (ML)
  - Supervised Learning
  - Unsupervised Learning
  - Reinforcement Learning
  - Deep Learning
- Symbolic AI (Classical AI)
- Probabilistic and Bayesian AI
- Evolutionary Algorithms
- Fuzzy Logic
- Hybrid AI (combining multiple paradigms)

### Application-specific AI solutions
- Predictive Analytics
- Prescriptive Analytics
- Computer Vision
- Natural Language Processing (NLP)
- Speech Recognition/Processing

### Emerging AI technologies
- Generative AI
  - Text Generation (e.g., LLMs)
  - Image Generation
  - Video Generation
  - Music Generation
  - Code Generation
- Agentic AI (Autonomous Decision-Making)

## Normative references

The following documents are referred to in the text in such a way that some or all of their content constitutes requirements of this document. For dated references, only the edition cited applies. For undated references, the latest edition of the referenced document (including any amendments) applies.

- ISO/IEC 5338:2023, Information technology — Artificial intelligence — AI system life cycle processes
- ISO/IEC 21031:2024, Information technology — Software Carbon Intensity (SCI) specification
- ISO/IEC 22989:2022, Information technology — Artificial intelligence — Artificial intelligence concepts and terminology

## Terms and definitions

For the purposes of this document, the terms and definitions given in ISO/IEC 21031:2024, ISO/IEC 22989:2022, and the following apply.

ISO and IEC maintain terminological databases for use in standardization at the following addresses:

- ISO Online browsing platform: available at https://www.iso.org/obp
- IEC Electropedia: available at http://www.electropedia.org/

T.1
**functional unit**
quantified performance characteristic of an AI system that serves as the reference unit for carbon intensity calculation

Note 1 to entry: This definition adapts the functional unit concept (denoted R) described in the Functional Unit clause of ISO/IEC 21031:2024 for AI-specific reference units.

T.2
**consumer**
entity that uses AI services and pays for functional units of AI

T.3
**provider**
entity that develops and delivers AI services, selling functional units of AI

T.4
**model training**
process of developing an AI model by exposing it to data and optimizing its parameters to perform specific tasks

T.5
**inference**
process of using a trained AI model to make predictions or generate outputs based on input data

T.6
**token**
atomic unit of text processing in language models, typically representing parts of words or characters

T.7
**parameter**
individual, adjustable value that defines a part of an AI model's structure and behavior

T.8
**floating point operation**
**(FLOP)**
basic computational operation used as a measure of computational work in AI systems

T.9
**gross value**
total quantity of a metric reported without adjustment for actual usage or contribution

T.10
**effective value**
quantity of a metric that reflects actual usage or meaningful contribution rather than an unadjusted total

## Symbols and abbreviated terms

For the purposes of this document, the following symbols and abbreviated terms apply.

| Abbreviation | Full term |
|---|---|
| AI | Artificial Intelligence |
| API | Application Programming Interface |
| CER | Certified Emission Reduction |
| EAC | Electricity Attribute Certificate |
| ERU | Emission Reduction Unit |
| FLOP | Floating Point Operation |
| LLM | Large Language Model |
| M | Allocated embodied emissions |
| NLP | Natural Language Processing |
| O | Operational emissions |
| OCR | Optical Character Recognition |
| PPA | Power Purchase Agreement |
| R | Functional unit |
| REC | Renewable Energy Credit |
| RMU | Removal Unit |
| SCI | Software Carbon Intensity |

## AI lifecycle stages

For the purpose of measuring carbon emissions, the AI lifecycle is divided into the following stages:

### Inception

The Inception stage involves defining the AI problem, assessing whether AI is the appropriate solution, engaging with end-users, and establishing performance objectives and computational constraints.

### Design and development

The Design and Development stage includes data collection from various sources, preprocessing (cleaning and normalizing), generating synthetic data when appropriate to reduce the need for excessive data collection, model selection, feature engineering, distributed training setup, evaluation metric definition, resource allocation, benchmarking, and computational resource optimization.

### Deployment

The Deployment stage involves incorporating the AI model into larger systems, designing component interactions, connecting with external applications, and testing for integration errors before deployment.

### Operation and monitoring

The Operation and Monitoring stage includes model deployment for inference, orchestration of autonomous workflows and models (e.g., in Agentic AI), integration of model tools and services, monitoring performance metrics, implementing maintenance protocols, and applying practices, like FinOps, across edge devices, data centers, and cloud environments.

### Retirement

The Retirement stage involves decommissioning AI systems no longer maintained in runtime environments and properly handling associated resources and data.

## Persona-based software boundary definition

This document defines boundaries based on two primary personas, each with different spheres of control and agency over the AI system's carbon footprint.

### Consumer boundary

The Consumer boundary shall include all components related to the Operation and Monitoring lifecycle stage, including but not limited to:

- API and Inference
- Orchestration
- Scaling
- Observability and Monitoring
- Data and Feature Management
- Storage and Artifacts
- UX and Client-side
- Model Tool and Service Connectors

### Provider boundary

The Provider boundary shall include all components related to the following lifecycle stages:

- Inception
- Design and Development
- Deployment
- Retirement

This includes:
- Project Scoping and Planning Systems
- Data Collection Systems
- Data Preprocessing and Cleaning Systems
- Synthetic Data Generation
- Model Development and Training Infrastructure
- Feature Engineering Systems
- Distributed Training Systems
- Model Evaluation and Benchmarking
- Optimization and Efficiency Analysis
- System Integration and Orchestration
- Testing and Validation Systems
- Model Tool Systems

## AI lifecycle coverage

Per ISO/IEC 21031:2024, an SCI score is calculated as SCI = (O + M) per R, where O is operational emissions, M is allocated embodied emissions, and R is the functional unit. This document applies the SCI methodology separately within the Consumer and Provider boundaries, accounting for O and M arising from systems and activities attributable to each persona across the applicable AI lifecycle stages. The subsections below specify, stage by stage, which emissions are included within each persona boundary and whether their inclusion is mandatory or conditional.

### Inception (Provider)

Systems used in the Inception stage shall be included in the Provider SCI calculation when material; they may be included when not material.

### Design and development (Provider)

All carbon emissions associated with systems used in the Design and Development stage shall be included in the Provider SCI calculation, including:

- Data collection, preprocessing, and cleaning systems
- Synthetic data generation
- Compute, storage, and networking resources for model training stages (including, but not limited to, pre-training, mid-training and post-training)
- Distributed training infrastructure
- Model selection and benchmarking systems
- Evaluation frameworks

Emissions from model training shall be calculated over the entire training duration, including but not limited to, accounting for all epochs, steps, parameter updates, intermediate and test runs, early stopping phases, failed or aborted training runs, hyperparameter tuning and search sweeps, and discarded or superseded model checkpoints.

### Deployment (Provider)

All carbon emissions associated with systems used in the Deployment stage shall be included in the Provider SCI calculation.

### Operation and monitoring (Consumer)

All carbon emissions associated with systems used in the Operation and Monitoring stage shall be included in the Consumer SCI calculation.

### Retirement (Consumer and Provider)

Systems used in the Retirement stage shall be included in the SCI calculation when material; they may be included when not material.

## Functional units

### Consumer functional units

Consumer functional units represent the measurable unit of AI service consumption used to normalize carbon emissions within the Consumer boundary. The functional unit should align with how the AI service is delivered, consumed, or billed.

Table 1 provides suggested examples of commonly used functional units. Given the diversity of AI system types and consumption models, these examples are indicative and not exhaustive.

**Table 1 — Suggested consumer functional units by AI system type**

| AI System Type | Suggested Functional Unit |
|---|---|
| Large Language Models (LLMs) | Per Token |
| Video Generation | Per Second |
| Image Generation | Per Image |
| Agentic AI | Per Workflow Execution |
| OCR/Document Analysis | Per Page Processed |
| Classical Machine Learning (e.g., Classification) | Per Inference |
| Machine Translation | Per Character Translated |
| Speech Recognition | Per Second of Audio Processed |
| Text-to-Speech | Per Character of Text Processed |

NOTE   Where an AI service involves multiple model calls, tool invocations, or service integrations, this can include model executions, tool usage, retrieval steps, model-to-model exchanges, and any other operations considered material.

### Provider functional units

Provider functional units shall align with one of the following metrics shown in Table 2, to normalize carbon emissions during AI model training. The choice of unit should reflect the primary optimization focus of the provider's system design, training strategy, or architecture. Each unit supports different efficiency objectives and carbon reduction strategies.

**Table 2 — Provider functional units and efficiency focus**

| Functional Unit | Description | Efficiency Focus |
|---|---|---|
| Per FLOP | Carbon emissions per floating point operation | Algorithmic and hardware efficiency |
| Per Training Token | Carbon emissions per token in training data | Data quality and curation efficiency |
| Per Billion Parameters | Carbon emissions per billion model parameters | Model architecture efficiency |

#### Guidance on functional unit selection

- Per FLOP is best suited for evaluating compute efficiency and incentivizes algorithmic improvements and optimized hardware utilization.
- Per Training Token aligns with data-centric strategies and encourages deduplication, curation, and synthetic augmentation.
- Per Billion Parameters emphasizes compact, purposeful model designs, especially when adjusted for activation sparsity.

#### Reporting expectations

Providers shall clearly state:

- the chosen functional unit and the rationale behind its selection;
- whether emissions are normalized using gross or effective values (see below);
- any key strategies, assumptions, or methodologies that are either material to the reported results or potentially valuable for others to adopt (e.g., pruning, sparse activation, synthetic data use).

Gross values refer to total quantities without adjustment — e.g., total parameters in the model, total tokens in a raw dataset, or total theoretical FLOPs. Effective values account for actual usage or meaningful contributions — e.g., active parameters used per inference (for sparse models), deduplicated or curated tokens, or utilized FLOPs during computation.

NOTE   Reporting effective values gives a more realistic picture of efficiency by recognizing carbon savings from optimizations like pruning, deduplication, or sparse activations.

This flexible approach allows providers to transparently highlight their optimization focus while avoiding misleading comparisons.

Providers may report multiple functional units where feasible, to give a comprehensive view of efficiency across compute, data, and model design dimensions.

EXAMPLE   An organization training a language model might report:
- 0,45 g CO₂e per 10¹² FLOPs, reflecting gains from switching to energy-efficient hardware;
- 0,18 g CO₂e per 1 000 training tokens, reflecting curation of the training dataset; and
- 20 kg CO₂e per billion parameters, reflecting pruning of inactive model weights.

## Implementation examples

This section provides examples of how to apply the SCI for AI specification in real-world scenarios, demonstrating how to combine software boundaries and functional units to calculate meaningful SCI scores.

### Large language model (LLM) example

For a typical Large Language Model service, two separate SCI scores should be calculated and reported:

#### Consumer SCI calculation

**Functional Unit**: Per Token

**Boundary**: Operation and Monitoring (inference services, API infrastructure, monitoring systems)

**Calculation Method**:

1. Measure all operational carbon within the Consumer boundary over a defined period (e.g., one week):
   - Carbon emitted of inference servers
   - Carbon emitted of API gateways and load balancers
   - Carbon emitted of monitoring and observability systems
   - Carbon emitted of caching and data storage
2. Calculate embodied carbon for all hardware within the Consumer boundary over the defined period.
3. Sum operational and embodied emissions to get total Consumer carbon (C).
4. Count the total number of tokens processed during the same period (R).
5. Calculate Consumer SCI: `SCI = C / R`.

EXAMPLE
- Total Consumer operational carbon: 5 000 kg CO₂e/week
- Total Consumer embodied carbon: 1 500 kg CO₂e/week
- Total tokens processed: 50 billion tokens/week
- Consumer SCI = 6 500 kg CO₂e ÷ 50 billion tokens = 130 kg CO₂e/billion tokens

#### Provider SCI calculation

**Functional Unit**: Per FLOP, Per Billion Parameters, or Per Training Token (example uses Per FLOP)

**Boundary**: Inception, Design and Development, Deployment, Retirement

**Calculation Method**:

1. Measure all operational carbon within the Provider boundary:
   - Carbon emitted during data collection and processing
   - Carbon emitted during model training
   - Carbon emitted during model optimization and testing
   - Carbon emitted during system integration
2. Calculate embodied emissions for all hardware within the Provider boundary.
3. Sum operational and embodied carbon to get total Provider carbon emissions (C).
4. Calculate the total number of FLOPs used (R).
5. Calculate Provider SCI: `SCI = C / R`.

EXAMPLE
- Total Provider operational emissions: 180 000 kg CO₂e
- Total Provider embodied emissions: 20 000 kg CO₂e
- Total FLOPs used: 5 × 10²² FLOPs
- Provider SCI = 200 000 kg CO₂e ÷ (5 × 10²² FLOPs) = 4 × 10⁻¹⁸ kg CO₂e/FLOP = 4 g CO₂e/10¹⁵ FLOPs

#### Reporting

For an LLM the following SCI values can be reported:

- Consumer SCI: 130 kg CO₂e/billion tokens
- Provider SCI: 4 g CO₂e/10¹⁵ FLOPs

### Computer vision model example

For a computer vision model used for image classification:

#### Consumer SCI calculation

**Functional Unit**: Per Inference

**Boundary**: Operation and Monitoring

EXAMPLE
- Total Consumer emissions: 3 200 kg CO₂e/month
- Total inferences: 40 million/month
- Consumer SCI = 3 200 kg CO₂e ÷ 40 million inferences = 0,08 g CO₂e/inference

#### Provider SCI calculation

**Functional Unit**: Per Billion Parameters

**Boundary**: Inception, Design and Development, Deployment, Retirement

EXAMPLE
- Total Provider emissions: 75 000 kg CO₂e
- Total parameters: 2,5 billion
- Provider SCI = 75 000 kg CO₂e ÷ 2,5 billion parameters = 30 000 kg CO₂e/billion parameters

#### Reporting

For a computer vision model the following SCI values can be reported:

- Consumer SCI: 0,08 g CO₂e/inference
- Provider SCI: 30 000 kg CO₂e/billion parameters

## Exclusions

### General

The focus of this document is elimination, not offsetting. One tonne of carbon eliminated from an AI system's operation is not equivalent to one tonne of carbon that has been offset. The preferable goal is to avoid emitting the carbon in the first place, rather than compensating for it after the fact.

Only actions that eliminate emissions reduce a Consumer or Provider SCI score. An SCI for AI score shall not be reduced through carbon offsets, such as market-based measures.

### Market-based measures

Market-based measures are financial instruments designed to neutralize or offset carbon emissions. Market-based measures include, but are not limited to, the following:

- carbon offsets or credits;
- a Removal Unit (RMU);
- an Emission Reduction Unit (ERU);
- a Certified Emission Reduction (CER);
- Electricity Attribute Certificates (EACs);
- Power Purchase Agreements (PPAs);
- Renewable Energy Credits (RECs).

NOTE   These exclusions apply equally to Consumer and Provider SCI calculations. For example, a provider's use of PPAs or RECs to claim clean energy sourcing for model training does not reduce the Provider SCI score; only genuine reductions in energy consumption, hardware footprint, or grid carbon intensity do.

## Further reading

The Net-Zero STANDARD, Science Based Targets initiative (SBTi), https://sciencebasedtargets.org/net-zero
