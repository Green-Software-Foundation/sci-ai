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

This specification applies to the following AI paradigms and applications:

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
Atomic unit of text processing in language models, typically representing parts of words, words, or characters

T.7  
**Parameter**  
Individual, adjustable value that defines a part of an AI model's structure and behavior

T.8  
**FLOP (Floating Point Operation)**  
Basic computational operation used as a measure of computational work in AI systems

## 5. AI Lifecycle Stages
For the purpose of measuring carbon emissions, the AI lifecycle is divided into the following stages:

### 5.1 Prepare
The Prepare stage involves defining the AI problem, assessing whether AI is the appropriate solution, engaging with end-users, and establishing performance objectives and computational constraints.

### 5.2 Data Engineering
The Data Engineering stage includes data collection from various sources, preprocessing (cleaning and normalizing), and generating synthetic data when appropriate to reduce the need for excessive data collection.

### 5.3 Model Training
The Model Training stage encompasses model selection, feature engineering, distributed training setup, evaluation metric definition, resource allocation, benchmarking, and computational resource optimization.

### 5.4 System Integration
The System Integration stage involves incorporating the AI model into larger systems, designing component interactions, connecting with external applications, and testing for integration errors before deployment.

### 5.5 Runtime Operations
The Runtime Operations stage includes model deployment for inference, active execution in deployed environments, monitoring performance metrics, implementing maintenance protocols, and applying FinOps practices across edge devices, data centers, and cloud environments.

### 5.6 End of Life
The End of Life stage involves decommissioning AI systems no longer maintained in runtime environments and properly handling associated resources and data.

## 6. Persona-Based Software Boundary Definition

The SCI for AI specification defines boundaries based on two primary personas, each with different spheres of control and agency over the AI system's carbon footprint.

### 6.1 Consumer Boundary

The Consumer boundary SHALL include all components related to the Runtime Operations lifecycle stage, including but not limited to:

- API & Inference
- Orchestration & Scaling
- Observability & Monitoring
- Data & Feature Management
- Storage & Artifacts
- UX & Client-side

### 6.2 Provider Boundary

The Provider boundary SHALL include all components related to the following lifecycle stages:

- Prepare
- Data Engineering
- Model Training
- System Integration
- End of Life/Disposal

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

## 7. AI Life Cycle Coverage

### 7.1 Prepare (Provider)

All carbon emissions associated with systems used in the Prepare stage SHALL be included in the Provider SCI calculation.

### 7.2 Data Engineering (Provider)

All carbon emissions associated with systems used in the Data Engineering stage SHALL be included in the Provider SCI calculation.

### 7.3 Model Training (Provider)

All carbon emissions associated with Model Training SHALL be included in the Provider SCI calculation, including:
- Compute, storage, and networking resources
- Distributed training infrastructure
- Model selection and benchmarking systems
- Evaluation frameworks

### 7.4 System Integration (Provider)

All carbon emissions associated with System Integration SHALL be included in the Provider SCI calculation.

### 7.5 Runtime Operations (Consumer)

All carbon emissions associated with systems used in the Runtime Operations stage SHALL be included in the Consumer SCI calculation.

### 7.6 End of Life (Provider)

All carbon emissions associated with End of Life processes SHALL be included in the Provider SCI calculation.

## 8. Functional Units

### 8.1 Consumer Functional Units

Consumer functional units SHALL align with established commercial pricing units based on the type of AI system:

| AI System Type | Functional Unit |
|----------------|----------------|
| LLM | Per Token |
| Video Generation | Per Second |
| Image Generation | Per Image |
| Agentic AI | Per Execution |
| OCR/Analysis | Per Page |
| Classical ML | Per Inference |

### 8.2 Provider Functional Units

Provider functional units SHALL align with neural scaling laws to enable meaningful comparisons and targets across model versions. One of the following units SHALL be used:

| Functional Unit | Description |
|----------------|-------------|
| Per Parameter | Carbon emissions per billion parameters |
| Per Training Token | Carbon emissions per token in training data |
| Per FLOP | Carbon emissions per floating point operation |

## 9. Implementation Examples

This section provides examples of how to apply the SCI for AI specification in real-world scenarios, demonstrating how to combine software boundaries and functional units to calculate meaningful SCI scores.

### 9.1 Large Language Model (LLM) Example

For a typical Large Language Model service, two separate SCI scores should be calculated and reported:

#### 9.1.1 Consumer SCI Calculation

**Functional Unit**: Per Token

**Boundary**: Runtime Operations (inference services, API infrastructure, monitoring systems)

**Calculation Method**:
1. Measure all operational carbon within the Consumer boundary over a defined period (e.g., one week):
   - Carbon emitted of inference servers
   - Carbon emitted of API gateways and load balancers
   - Carbon emitted of monitoring and observability systems
   - Carbon emitted of caching and data storage
2. Calculate embodied carbon for all hardware within the Consumer boundary
3. Sum operational and embodied emissions to get total Consumer carbon (C)
4. Count the total number of tokens processed during the same period (R)
5. Calculate Consumer SCI: `SCI = C / R`

**Example**:
- Total Consumer operational carbon: 5,000 kg CO₂e/week
- Total Consumer embodied carbon: 1,500 kg CO₂e/week
- Total tokens processed: 50 billion tokens/week
- Consumer SCI = 6,500 kg CO₂e / 50 billion tokens = 0.13 g CO₂e/million tokens

#### 9.1.2 Provider SCI Calculation

**Functional Unit**: Per FLOP, Per Parameter, or Per Training Token (example uses Per FLOP)

**Boundary**: Prepare, Data Engineering, Model Training, System Integration, End of Life

**Calculation Method**:
1. Measure all operational carbon within the Provider boundary:
   - Carbon emitted during data collection and processing
   - Carbon emitted during model training
   - Carbon emitted during model optimization and testing
   - Carbon emitted during system integration
2. Calculate embodied emissions for all hardware within the Provider boundary
3. Sum operational and embodied carbon to get total Provider carbon emissions (C)
4. Calculate the total number of FLOPs used (R)
5. Calculate Provider SCI: `SCI = PC / R`

**Example**:
- Total Provider operational emissions: 180,000 kg CO₂e
- Total Provider embodied emissions: 20,000 kg CO₂e
- Total FLOPs: 5 × 10²² FLOPs
- Provider SCI = 200,000 kg CO₂e / (5 × 10²² FLOPs) = 4 × 10⁻¹⁸ kg CO₂e/FLOP = 4 g CO₂e/10¹⁸ FLOPs

#### 9.1.3 Reporting

The LLM would report both SCI values:
- **Consumer SCI**: 0.13 g CO₂e/million tokens
- **Provider SCI**: 4 g CO₂e/10¹⁸ FLOPs

### 9.2 Computer Vision Model Example

For a computer vision model used for image classification:

#### 9.2.1 Consumer SCI Calculation

**Functional Unit**: Per Inference

**Boundary**: Runtime Operations

**Example**:
- Total Consumer emissions: 3,200 kg CO₂e/month
- Total inferences: 40 million/month
- Consumer SCI = 0.08 g CO₂e/inference

#### 9.2.2 Provider SCI Calculation

**Functional Unit**: Per Parameter

**Boundary**: Prepare, Data Engineering, Model Training, System Integration, End of Life

**Example**:
- Total Provider emissions: 75,000 kg CO₂e
- Total parameters: 2.5 billion
- Provider SCI = 30 kg CO₂e/billion parameters

#### 9.2.3 Reporting

The computer vision model would report both SCI values:
- **Consumer SCI**: 0.08 g CO₂e/inference
- **Provider SCI**: 30 kg CO₂e/billion parameters