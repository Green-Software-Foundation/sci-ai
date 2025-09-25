# Software Carbon Intensity for AI Specification

## 1. Introduction

This specification extends the Software Carbon Intensity (SCI) methodology to the unique characteristics of Artificial Intelligence (AI) systems. It provides a standardized method for measuring and reporting the carbon emissions associated with AI throughout its lifecycle.

The SCI for AI specification builds upon the core principles established in ISO/IEC 21031:2024 while adding considerations specific to AI systems, including their distinctive architecture, resource requirements, and operational patterns.

This specification aims to:
- Provide a consistent framework for measuring the carbon footprint of AI systems
- Enable meaningful comparisons between different AI implementations
- Guide practitioners in making environmentally responsible decisions in AI development and deployment
- Incentivize carbon efficiency improvements across the AI lifecycle

## 2. Scope

This specification covers a broad spectrum of AI systems, including classical machine learning, generative AI, and agentic AI, and is designed to support current and future developments in the field.

### 2.1 AI Paradigms (Foundational Approaches)
- Machine Learning (ML)
  - Supervised Learning
  - Unsupervised Learning
  - Reinforcement Learning
  - Deep Learning
- Symbolic AI (Classical AI)
- Probabilistic & Bayesian AI
- Evolutionary Algorithms
- Fuzzy Logic
- Hybrid AI (combining multiple paradigms)

### 2.2 Application-Specific AI Solutions
- Predictive Analytics
- Prescriptive Analytics
- Computer Vision
- Natural Language Processing (NLP)
- Speech Recognition/Processing

### 2.3 Emerging AI Technologies
- Generative AI
  - Text Generation (e.g., LLMs)
  - Image Generation
  - Video Generation
  - Music Generation
  - Code Generation
- Agentic AI (Autonomous Decision-Making)

## 3. Normative References

The following documents are referred to in the text in such a way that some or all of their content constitutes requirements of this document:
- ISO/IEC 21031:2024 – Information technology — Software Carbon Intensity (SCI) specification

## 4. Terms and Definitions

For the purposes of this document, the terms and definitions given in ISO/IEC 21031:2024 and the following apply.

ISO and IEC maintain terminological databases for use in standardization at the following addresses:
-	ISO Online browsing platform: available at https://www.iso.org/obp
-	IEC Electropedia: available at http://www.electropedia.org/

T.1  
**Functional Unit**  
Quantified performance characteristic of an AI system that serves as the reference unit for carbon intensity calculation

T.2  
**Consumer**  
Entity that uses AI services and pays for functional units of AI

T.3  
**Provider**  
Entity that develops and delivers AI services, selling functional units of AI

T.4  
**Model Training**  
Process of developing an AI model by exposing it to data and optimizing its parameters to perform a specific task

T.5  
**Inference**  
Process of using a trained AI model to make predictions or generate outputs based on input data

T.6
**Token**
A token is a fundamental unit of data that a model uses to process information. For example in text, tokens typically represent parts of words, or characters.

T.7  
**Parameter**  
Individual, adjustable value that defines a part of an AI model's structure and behavior

T.8  
**FLOP (Floating Point Operation)**  
Basic computational operation used as a measure of computational work in AI systems

## 5. AI Lifecycle Stages
For the purpose of measuring carbon emissions, the AI lifecycle is divided into the following stages:

### 5.1 Inception
The Inception stage involves defining the AI problem, assessing whether AI is the appropriate solution, engaging with end-users, and establishing performance objectives and computational constraints.

### 5.2 Design and Development
The Design and Development stage includes data collection from various sources, preprocessing (cleaning and normalizing), generating synthetic data when appropriate to reduce the need for excessive data collection, model selection, feature engineering, distributed training setup, evaluation metric definition, resource allocation, benchmarking, and computational resource optimization.

### 5.3 Deployment
The Deployment stage involves incorporating the AI model into larger systems, designing component interactions, connecting with external applications, and testing for integration errors before deployment.

### 5.4 Operation and Monitoring
The Operation and Monitoring stage includes model deployment for inference, orchestration of autonomous workflows and models (e.g., in Agentic AI), integration of model tools and services, monitoring performance metrics, implementing maintenance protocols, and applying FinOps practices across edge devices, data centers, and cloud environments.

### 5.5 Runtime Operations
The Runtime Operations stage includes model deployment for inference, orchestration of autonomous workflows and models (e.g., in Agentic AI), integration of model tools and services, monitoring performance metrics, implementing maintenance protocols, and applying practices, like FinOps, across edge devices, data centers, and cloud environments.

### 5.6 End of Life
The End of Life stage involves decommissioning AI systems no longer maintained in runtime environments and properly handling associated resources and data.

## 6. Persona-Based Software Boundary Definition

The SCI for AI specification defines boundaries based on two primary personas, each with different spheres of control and agency over the AI system's carbon footprint.

### 6.1 Consumer Boundary

The Consumer boundary SHALL include all components related to the Operation and Monitoring lifecycle stage, including but not limited to:

- API & Inference
- Orchestration
- Scaling
- Observability & Monitoring
- Data & Feature Management
- Storage & Artifacts
- UX & Client-side
- Model Tool & Service Connectors
  

### 6.2 Provider Boundary

The Provider boundary SHALL include all components related to the following lifecycle stages:
- Design and Development
- Deployment
- Retirement

This includes:
- Project Scoping & Planning Systems
- Data Collection Systems
- Data Preprocessing & Cleaning Systems
- Synthetic Data Generation
- Model Development & Training Infrastructure
- Feature Engineering Systems
- Distributed Training Systems
- Model Evaluation & Benchmarking
- Optimization & Efficiency Analysis
- System Integration & Orchestration
- Testing & Validation Systems
- Model Tool Systems

## 7. AI Life Cycle Coverage

### 7.1 Inception (Provider)

Systems used in the Inception stage SHALL be included in the Provider SCI calculation when material; they MAY be included when not material.

### 7.2 Design and Development (Provider)

All carbon emissions associated with systems used in the Design and Development stage SHALL be included in the Provider SCI calculation, including:
- Data collection, preprocessing, and cleaning systems
- Synthetic data generation
- Compute, storage, and networking resources for model training
- Distributed training infrastructure
- Model selection and benchmarking systems
- Evaluation frameworks

Emissions from model training SHALL be calculated over the entire training duration, including but not limited to, accounting for all epochs, steps, parameter updates, intermediate runs, and early stopping phases. 

### 7.3 Deployment (Provider)

All carbon emissions associated with Deployment SHALL be included in the Provider SCI calculation.

### 7.4 Operation and Monitoring (Consumer)

All carbon emissions associated with systems used in the Operation and Monitoring stage SHALL be included in the Consumer SCI calculation.

### 7.5 Retirement

Systems used in the Retirement stage SHALL be included in the SCI calculation when material; they MAY be included when not material.

## 8. Functional Units

### 8.1 Consumer Functional Units

Consumer functional units represent the measurable unit of AI service consumption used to normalize carbon emissions within the Consumer boundary. The functional unit SHOULD align with how the AI service is delivered, consumed, or billed.

The table below provides **suggested examples** of commonly used functional units. Given the diversity of AI system types and consumption models, these examples are indicative and not exhaustive.

| AI System Type                          | Suggested Functional Unit            |
|-----------------------------------------|---------------------------------------|
| Large Language Models (LLMs)            | Per Token                            |
| Video Generation                        | Per Second             |
| Image Generation                        | Per Image                            |
| Agentic AI                              | Per Workflow Execution               |
| OCR / Document Analysis                 | Per Page Processed                   |
| Classical Machine Learning (e.g., Classification) | Per Inference                  |
| Machine Translation                     | Per Character Translated    |
| Speech Recognition                      | Per Second of Audio Processed         |
| Text-to-Speech                          | Per Character of Text Processed         |

Note:
Where an AI service involves multiple model calls, tool invocations, or service integrations, emissions SHOULD account for all triggered operations — including model executions, tool usage, retrieval steps, model-to-model exchanges, and any other impacts considered material.

### 8.2 Provider Functional Units

Provider functional units SHALL align with one of the following metrics to normalize carbon emissions during AI model training. The choice of unit SHOULD reflect the primary optimization focus of the provider’s system design, training strategy, or architecture. Each unit supports different efficiency objectives and carbon reduction strategies.

| Functional Unit        | Description                                               | Efficiency Focus                      |
|------------------------|-----------------------------------------------------------|----------------------------------------|
| Per FLOP               | Carbon emissions per floating point operation             | Algorithmic & hardware efficiency      |
| Per Training Token     | Carbon emissions per token in training data               | Data quality & curation efficiency     |
| Per Parameter          | Carbon emissions per billion model parameters             | Model architecture efficiency          |

#### 8.2.1 Guidance on Functional Unit Selection

- **Per FLOP** is best suited for evaluating compute efficiency and incentivizes algorithmic improvements and optimized hardware utilization.  
- **Per Training Token** aligns with data-centric strategies and encourages deduplication, curation, and synthetic augmentation.  
- **Per Parameter** emphasizes compact, purposeful model designs, especially when adjusted for activation sparsity.

#### 8.2.2 Reporting Expectations

Providers SHALL clearly state:
- The chosen functional unit and the rationale behind its selection
- Whether emissions are normalized using gross or *effective* values (see explanation below)
- Any key strategies, assumptions, or methodologies that are either material to the reported results or potentially valuable for others to adopt (e.g., pruning, sparse activation, synthetic data use)

> **Explanation**:  
> - **Gross values** refer to total quantities without adjustment — e.g., total parameters in the model, total tokens in a raw dataset, or total theoretical FLOPs.  
> - **Effective values** account for actual usage or meaningful contributions — e.g., active parameters used per inference (for sparse models), deduplicated or curated tokens, or utilized FLOPs during computation.  
>  
> Reporting *effective* values gives a more realistic picture of efficiency by recognizing carbon savings from optimizations like pruning, deduplication, or sparse activations.

This flexible approach allows providers to transparently highlight their optimization focus while avoiding misleading comparisons.

> Reporting **multiple functional units MAY be encouraged**, especially when feasible, to provide a **comprehensive view** of efficiency across compute, data, and model design dimensions.

**Example (Multi-Metric Reporting):**

An organization training a language model might report:
- **Carbon per FLOP**: 0.45 gCO₂e / 10¹² FLOPs  
- **Carbon per Training Token**: 0.18 gCO₂e / 1,000 tokens  
- **Carbon per Parameter**: 20 kgCO₂e / billion parameters  

These values reflect respective gains from switching to energy-efficient hardware, curating training datasets, and pruning inactive model weights.

## 9. Implementation Examples

This section provides examples of how to apply the SCI for AI specification in real-world scenarios, demonstrating how to combine software boundaries and functional units to calculate meaningful SCI scores.

### 9.1 Large Language Model (LLM) Example

For a typical Large Language Model service, two separate SCI scores should be calculated and reported:

#### 9.1.1 Consumer SCI Calculation

**Functional Unit**: Per Token

**Boundary**: Operation and Monitoring (inference services, API infrastructure, monitoring systems)

**Calculation Method**:
1. Measure all operational carbon within the Consumer boundary over a defined period (e.g., one week):
   - Carbon emitted of inference servers
   - Carbon emitted of API gateways and load balancers
   - Carbon emitted of monitoring and observability systems
   - Carbon emitted of caching and data storage
2. Calculate embodied carbon for all hardware within the Consumer boundary over the defined period.
3. Sum operational and embodied emissions to get total Consumer carbon (C)
4. Count the total number of tokens processed during the same period (R)
5. Calculate Consumer SCI: `SCI = C / R`

**Example**:
- Total Consumer operational carbon: 5,000 kg CO₂e/week
- Total Consumer embodied carbon: 1,500 kg CO₂e/week
- Total tokens processed: 50 billion tokens/week
- Consumer SCI = 6,500 kg CO₂e / 50 billion tokens = 130 kg CO₂e/billion tokens

#### 9.1.2 Provider SCI Calculation

**Functional Unit**: Per FLOP, Per Parameter, or Per Training Token (example uses Per FLOP)

**Boundary**: Design and Development, Deployment, Retirement

**Calculation Method**:
1. Measure all operational carbon within the Provider boundary:
   - Carbon emitted during data collection and processing
   - Carbon emitted during model training
   - Carbon emitted during model optimization and testing
   - Carbon emitted during system integration
2. Calculate embodied emissions for all hardware within the Provider boundary
3. Sum operational and embodied carbon to get total Provider carbon emissions (C)
4. Calculate the total number of FLOPs used (R)
5. Calculate Provider SCI: `SCI = C / R`

**Example**:
- Total Provider operational emissions: 180,000 kg CO₂e
- Total Provider embodied emissions: 20,000 kg CO₂e
- Total FLOPs: 5 × 10²² FLOPs
- Provider SCI = 200,000 kg CO₂e / (5 × 10²² FLOPs) = 4 × 10⁻¹⁸ kg CO₂e/FLOP = 4 g CO₂e/10¹⁵ FLOPs

#### 9.1.3 Reporting

For an LLM the following SCI values can be reported:
- **Consumer SCI**: 0.13 g CO₂e/million tokens
- **Provider SCI**: 4 g CO₂e/10¹⁵ FLOPs

### 9.2 Computer Vision Model Example

For a computer vision model used for image classification:

#### 9.2.1 Consumer SCI Calculation

**Functional Unit**: Per Inference

**Boundary**: Operation and Monitoring

**Example**:
- Total Consumer emissions: 3,200 kg CO₂e/month
- Total inferences: 40 million/month
- Consumer SCI = 0.08 g CO₂e/inference

#### 9.2.2 Provider SCI Calculation

**Functional Unit**: Per Parameter

**Boundary**: Inception, Design and Development, Deployment, Retirement

**Example**:
- Total Provider emissions: 75,000 kg CO₂e
- Total parameters: 2.5 billion
- Provider SCI = 3000 kg CO₂e/billion parameters

#### 9.2.3 Reporting

For a computer vision model the following SCI values can be reported:
- **Consumer SCI**: 0.08 g CO₂e/inference
- **Provider SCI**: 30 kg CO₂e/billion parameters
