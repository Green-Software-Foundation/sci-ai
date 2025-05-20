# Software Carbon Intensity for AI - Rationale and FAQ

## Overview

This document provides the rationale behind key decisions in the Software Carbon Intensity (SCI) for AI specification and answers frequently asked questions about its design, methodology, and implementation.

The SCI for AI specification is designed to be comprehensive, fair and actionable. By adopting a persona-based approach with clear boundaries and functional units, it provides a practical framework for measuring and reducing the carbon footprint of AI systems throughout their lifecycle.

## Frequently Asked Questions

### General Questions

#### Why do we need a specific SCI standard for AI?

AI systems have unique characteristics compared to traditional software:
- They often involve resource-intensive training phases
- They can have vastly different usage patterns during inference
- Their architecture and deployment models are evolving rapidly
- They create complex questions around the attribution of historical emissions (particularly from training)

The core SCI specification provides an excellent foundation, but AI-specific guidance is needed to ensure consistent measurement, meaningful comparisons, and proper incentivization of carbon-efficient practices across the AI lifecycle.

#### How does SCI for AI relate to the original SCI specification?

SCI for AI builds upon and extends the original SCI specification. It maintains all core principles from the original specification while adding AI-specific considerations for:
- Software boundaries
- Functional units
- Allocation methodologies
- Life cycle coverage

Nothing in SCI for AI contradicts or supersedes the original SCI specification; it simply provides clearer guidance for AI practitioners.

### Philosophy and Purpose

#### What is the fundamental philosophy behind SCI for AI?

The SCI for AI is fundamentally an action-oriented metric designed to drive real-world carbon reductions. Its core philosophy is simple:

**A good metric must incentivize the right actions by the right actors.**

This means:
1. **Agency-Aligned**: The metric holds personas accountable only for emissions they can control
2. **Decision-Focused**: It provides information that directly supports carbon-reduction decisions
3. **Systemically Effective**: It drives long-term, systemic improvements in carbon efficiency

As a guiding principle: *If a metric doesn't help you make decisions (which requires having agency to act on those decisions), it's a poor metric.*

#### How does SCI for AI ensure it drives action?

SCI for AI is designed to be both **comparable** and **actionable**:

**Comparable**: The metric enables meaningful comparisons between:
- Different AI systems serving similar functions
- Different versions of the same AI system over time
- Different deployment configurations of the same AI system

**Actionable**: The metric supports clear target-setting and improvement tracking:
- Providers can set efficiency targets for their next model version (e.g., "reduce SCI by 10%")
- Consumers can select AI services based on both cost and carbon intensity
- Engineers can quantify the carbon impact of specific architectural or deployment changes

Without both properties, a metric may be interesting but fails to drive systematic carbon reductions. For example, a metric that only measures total emissions without normalization might show that all new models are "worse" as they grow in capability, providing no path for improvement beyond "make smaller models" - which conflicts with the goal of advancing AI capabilities.

#### Why is the persona-based approach critical to making SCI for AI actionable?

The persona-based approach directly connects responsibility with agency:

1. It recognizes that different stakeholders control different parts of the AI lifecycle
2. It creates metrics that align with existing organizational boundaries and decision-making
3. It prevents dilution of responsibility that occurs when everyone is collectively responsible for everything
4. It enables each persona to set relevant, achievable targets within their sphere of control

When metrics align with agency, they become powerful tools for driving change rather than just measuring it.

### Persona-Based Approach

#### Why does the specification use a persona-based approach?

The persona-based approach (Consumer vs. Provider) addresses a fundamental reality: different stakeholders have different spheres of control and agency over an AI system's carbon footprint. By separating measurements based on personas:

1. Each persona is held accountable only for emissions they can control
2. The resulting metrics are more actionable and relevant
3. It creates clearer incentives for carbon reduction where actual agency exists
4. It acknowledges the reality of how AI systems are developed and deployed today

If a single metric tried to combine everything, it would dilute accountability and create a metric that's less useful for driving improvements.

#### Why assign particular lifecycle stages to specific personas?

The lifecycle stages are assigned to personas based on their typical control and agency:

- **Providers** (companies that build AI systems) control the emissions from Prepare, Data Engineering, Model Training, System Integration, and End of Life stages.
- **Consumers** (organizations and individuals who use AI systems) control the emissions from Runtime Operations.

This alignment ensures that each persona's SCI score reflects only the emissions they can reasonably influence or control.

### Functional Units

#### Why use different functional units for Consumers and Providers?

**For Consumers:**
- The functional units align with established commercial pricing models (e.g., tokens, seconds, inferences)
- This direct alignment with pricing creates a powerful "cost vs. carbon" comparison
- It reduces cognitive load when making decisions about which AI service to use
- It fits seamlessly with existing FinOps frameworks many organizations already use

**For Providers:**
- Functional units align with neural scaling laws (parameters, training tokens, FLOPs)
- This enables meaningful comparisons between different model versions
- It creates actionable targets for future model improvements
- It addresses the reality that newer, more capable models often require more resources

#### Why not use "total emissions per version" for Providers?

Total emissions per version fails to provide meaningful insights or drive improvements:
- It doesn't enable meaningful comparisons between model versions
- It doesn't provide actionable targets for improvement
- It doesn't account for increasing model capabilities
- It obscures efficiency trends as models grow in size and capability

Looking at the evolution of large language models:

| AI Version | Training Emissions       | Parameters       |
| ---------- | ------------------------ | ---------------- |
| GPT-2      | ~50 metric tons CO₂e     | ~1.5B parameters |
| GPT-3      | ~1,200 metric tons CO₂e  | ~175B parameters |
| GPT-4      | ~20,000 metric tons CO₂e | ~1T parameters   |

Based on total emissions alone, one might conclude that newer models are simply worse for the environment, with no clear path for improvement other than "make smaller models." This insight isn't actionable for organizations committed to advancing AI capabilities.

However, using "emissions per billion parameters" surfaces much more nuanced and actionable insights:

| AI Version | Per Billion Parameters |
| ---------- | ---------------------- |
| GPT-2      | ~33.3 metric tons CO₂e |
| GPT-3      | ~6.86 metric tons CO₂e |
| GPT-4      | ~20 metric tons CO₂e   |

This normalized view reveals that:
1. GPT-3 achieved a dramatic efficiency improvement over GPT-2 (about 5x better per parameter)
2. While GPT-4 was less efficient than GPT-3, it was still significantly more efficient than GPT-2
3. The regression between GPT-3 and GPT-4 identifies a specific opportunity for improvement

These insights enable meaningful target-setting. If you've just finished training GPT-3 at ~6.86 metric tons CO₂e per billion parameters, you can set a concrete target for GPT-4 to maintain or improve upon this efficiency despite its increased scale. Without this normalized metric, setting a meaningful target would be nearly impossible when you know the model will necessarily grow in size and capability.

### Treatment of Training Emissions

#### How are training emissions handled in the specification?

Training emissions are included in the Provider SCI calculation only as direct emissions. This is because:

1. Training is part of the Model Training lifecycle stage, which is assigned to the Provider boundary
2. Providers have direct control over training methodologies, hardware selection, and efficiency optimizations
3. It creates clear accountability for the emissions produced during the creation of AI models

This approach:
- Holds Providers accountable for the efficiency of their training process
- Creates strong incentives for Providers to optimize training methods and infrastructure
- Aligns with the persona-based boundary definitions
- Maintains clear separation of responsibilities between Providers and Consumers

#### Why aren't training emissions amortized to Consumers?

We decided not to include training emissions in the Consumer SCI calculation for several reasons:

1. **Clear Boundaries**: Keeping training emissions solely within the Provider boundary maintains clean, non-overlapping responsibility areas
2. **Agency Alignment**: Consumers typically have no control over how models are trained
3. **Measurement Simplicity**: Separating training from inference creates more straightforward measurement methodologies
4. **Incentive Clarity**: It focuses Consumer attention on what they can control - the efficiency of runtime operations

This doesn't mean training emissions are ignored - they're captured in the Provider SCI score, which Consumers can consider when selecting AI systems alongside the Consumer SCI score.

### Lifecycle Coverage

#### Why include all lifecycle stages in the specification?

The comprehensive lifecycle approach:
- Ensures no significant sources of emissions are overlooked
- Creates appropriate incentives for reducing emissions at each stage
- Aligns with established lifecycle assessment methodologies
- Enables more complete and accurate comparisons between AI systems

#### Why separate Model Training from System Integration?

Model Training is separated as its own lifecycle stage because:
1. It often represents a significant portion of an AI system's carbon footprint
2. It involves unique considerations around resource allocation and optimization
3. It's a key area of focus for emissions reduction efforts
4. It's typically performed separately from other system integration activities

### Comparison to Other Metrics

#### How does SCI for AI compare to metrics like Green AI Index, EcoLogits, and Energy Score?

SCI for AI incorporates the strengths of existing metrics while addressing their limitations:

- Like Green AI Index, it includes comprehensive lifecycle coverage and embodied emissions, but adds clearer allocation methodologies and persona-based boundaries.
- Like EcoLogits, it provides practical, actionable metrics, but extends beyond inference to cover the full lifecycle
- Like Energy Score, it enables fair comparisons, but with broader scope and flexibility

Uniquely, SCI for AI:
- Is developed through a consensus-based process
- Aligns with ISO standards frameworks
- Includes clear IP rights statements
- Provides specific guidance for both open-source and proprietary models
- Covers all lifecycle stages (unlike EcoLogits and Energy Score which focus primarily on inference)
- Unlike Green AI Index it does not allow market-based reporting (energy offsets), maintaining consistency with the core SCI specification's focus on location-based, operational efficiency improvements

#### What are the key limitations of existing metrics that SCI for AI addresses?

**Limited Lifecycle Coverage**:
- **EcoLogits** only addresses inference emissions, excluding the often substantial emissions from training, data engineering, and other lifecycle stages
- **Energy Score** similarly focuses only on GPU energy consumption during inference, ignoring both other components (CPU, RAM, networking) and other lifecycle stages
- Neither approach provides a complete picture of an AI system's carbon footprint

**Inconsistent Treatment of Energy Offsets**:
- **Green AI Index** allows for market-based reporting that includes carbon offsets in its Data Center Index, which can mask actual operational emissions
- This approach is fundamentally at odds with the SCI family of specifications, which explicitly does not allow for market-based reporting or offsets
- SCI for AI maintains the focus on direct operational and embodied emissions that can be reduced through technical improvements rather than financial mechanisms

**Lack of Consensus Development**:
- None of the existing metrics was developed through a multi-stakeholder consensus process
- SCI for AI is being developed collaboratively by the Green Software Foundation with input from a diverse range of organizations across the AI ecosystem

#### How was SCI for AI evaluated against other measurement frameworks?

During development, we agreed to evaluate SCI for AI and existing metrics against a comprehensive rubric covering multiple dimensions:

**Adoption Criteria:**
- **Flexibility**: Can it be applied or extended as the AI ecosystem evolves?
- **Granularity**: Does it break down emissions by component, system stage, or time?
- **Run-Time & Design-Time Applicability**: Can it estimate environmental impact before deployment?
- **Explainability**: How understandable is it to non-technical audiences?
- **Broad Scope**: Does it apply to the full spectrum of AI paradigms and applications?
- **Open Source & Proprietary Applicability**: Can it measure both open models and closed models?

**Pathway to Policy & Certification:**
- **Consensus-Based Development**: Was it developed collaboratively with multiple stakeholders?
- **ISO Compatibility**: Does it align with or aim to become an ISO standard?
- **IPR Considerations**: Was it developed with clear patent policies?
- **Existing Standards Alignment**: Does it align with established practices like LCA or GHG Protocol?

**Lifecycle Coverage:**
- Prepare
- Data Engineering
- Model Training
- System Integration
- Runtime Operations
- End of Life

**Incentivization:**
- Does it encourage infrastructure efficiency improvements?
- Does it reward silicon efficiency improvements?
- Does it promote model architecture optimization?
- Does it incentivize training carbon reduction?
- Does it encourage spatial/temporal shifting to cleaner energy?
- Does it reward appropriate edge device usage?

Here's how SCI for AI compares to other metrics based on these criteria:

| Criteria                          | SCI for AI | Green AI Index | EcoLogits | Energy Score |
| --------------------------------- | ---------- | -------------- | --------- | ------------ |
| **Flexibility**                   | ✅          | ✅              | ❌         | ❌            |
| **Granularity: Component**        | ✅          | ✅              | ❌         | ❌            |
| **Granularity: Time**             | ✅          | ❌              | ❌         | ❌            |
| **Run-Time & Design-Time**        | ✅          | ✅              | ✅         | ❌            |
| **Explainability**                | 4/5         | 3/5             | 3/5        | 4/5           |
| **Broad Scope**                   | ✅          | ✅              | ✅         | ✅            |
| **Open & Proprietary**            | ✅          | ✅              | ✅         | ✅            |
| **Consensus Development**         | ✅          | ❌              | ❌         | ❌            |
| **ISO Compatibility**             | ✅          | ❓              | ❓         | ❌            |
| **IPR Clarity**                   | ✅          | ❌              | ❌         | ❌            |
| **Existing Standards Alignment**  | ✅          | ✅              | ✅         | ❌            |
| **Lifecycle: Prepare**            | ✅          | ❌              | ❌         | ❌            |
| **Lifecycle: Data Engineering**   | ✅          | ❌              | ❌         | ❌            |
| **Lifecycle: Model Training**     | ✅          | ✅              | ❌         | ❌            |
| **Lifecycle: System Integration** | ✅          | ❌              | ❌         | ❌            |
| **Lifecycle: Runtime Operations** | ✅          | ✅              | ☑️*        | ☑️**          |
| **Lifecycle: End of Life**        | ✅          | ❌              | ❌         | ❌            |

*EcoLogits only accounts for computation of GPU-equipped servers, omitting other runtime infrastructure

**Energy Score only measures GPU energy during inference, explicitly excluding CPU, RAM, networking, and storage energy.

#### Why create a new standard instead of adopting an existing one?

None of the existing metrics fully satisfies all requirements for a comprehensive, fair, and actionable carbon measurement standard for AI. SCI for AI builds on their strengths while addressing limitations, particularly in:
- Consensus development
- ISO compatibility
- IPR considerations
- Full lifecycle coverage
- Clear boundaries and allocation methodologies
- Consistency with the core SCI principles of location-based reporting

### Implementation

#### How complex is the implementation of SCI for AI?

The specification balances comprehensiveness with practicality:
- The core calculations are straightforward
- The boundary definitions are clear
- The allocation methodologies are well-defined
- Multiple implementation approaches are possible based on available data

For organizations already familiar with carbon accounting or the core SCI specification, implementing SCI for AI should be relatively straightforward.

#### What data is required to calculate SCI for AI?

The basic data requirements include:
- Energy consumption of components within the relevant boundary
- Carbon intensity factors for energy sources
- Functional unit counts (parameters, tokens, inferences, etc.)
- For embodied emissions: hardware specifications and usage patterns

More detailed measurements will produce more accurate results, but the specification is designed to work with different levels of data granularity.