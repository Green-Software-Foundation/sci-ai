# Software Carbon Intensity for AI Specification

## Introduction

> ![NOTE] 
> TODO

- Why does this specification exist?
- What is it's intended purpose?
- How this aligns and differs with the overall SCI specifcations (aka we are diving into some aspects of defining R for the area of AI)

## Scope

The SCI for AI aims to measure these core AI Paradigms (Foundational Approaches):

* Machine Learning (ML)
  * Supervised Learning
  * Unsupervised Learning
  * Reinforcement Learning
  * Deep Learning
    * Supports Computer Vision
    * Supports NLP
    * Supports Generative AI
    * Supports Speech Recognition/Processing
  * Predictive Analytics
* Symbolic AI (Classical AI)
* Probabilistic & Bayesian AI
* Evolutionary Algorithms
* Fuzzy Logic
* Hybrid AI (combining multiple paradigms)

And including but not limited to, these application-specific AI solutions
* Predictive Analytics
* Prescriptive Analytics
* Computer Vision
* Natural Language Processing (NLP)

The standard will also be applicable to emerging AI technologies such as:

* Generative AI
  * Text Generation (e.g., GPT)
  * Image Generation (e.g., DALL·E)
  * Video Generation
  * Music Generation
  * Code Generation  
* Agentic AI (Autonomous Decision-Making)


## Normative References

ISO/IEC 21031:2024 – Information technology — Software Carbon Intensity (SCI) specification


##  Terms and Definitions

For the purposes of this document, the following terms and definitions apply.

ISO and IEC maintain terminological databases for use in standardization at the following addresses:
-	ISO Online browsing platform: available at https://www.iso.org/obp
-	IEC Electropedia: available at http://www.electropedia.org/

T.1  
**term**  
explanation



# Existing AI Measurement Metrics

> ![NOTE] 
> This section will likely be removed from the specification eventually. For now keeping it in the same document so all the context of our discusions in one document.

An important first step in the development of the SCI for AI involves an analysis of the current landscape of AI Measurement Metrics. Although the list below is not exhaustive, they are representative of the types of metrics being discussed and developed, we first will provide an overview of each metric and then explore them against the evaluation rubric agreed in the workshop.

## Green AI Index

[GreenAI Index](https://greensoftwarefdn.slack.com/archives/C089TCNMXC0/p1738686822660119)

Created by [Green AI Institute](https://www.greenai.institute/), in 2024. 

The stated aim is to: *“promote transparency, encourage more sustainable practices, incentivize carbon-efficient innovations, and guide policymakers, organizations, and developers in reducing their environmental footprint”.*

The unique selling point for the Green AI Index is that it aligns with regulatory requirements in three major jurisdictions: EU, USA and China. The white paper introducing the index reviews the key regulations in all three of these jurisdictions.

Green AI Index is also interesting because it comes in two variants: the Green AI “Data Center” Index, and the Green AI “AI Model” index. Both aim to conform to the LCA standard (ISO 14040 and 14044).

The Data Center Index focuses on mapping inventory items from the GHG protocol to equivalents that are data center specific, covering scopes 1-3 (upstream and downstream).

The AI model index is most relevant to the SCI4AI. 

The top level division of components is by operational/embodied impacts, i.e. rather than the top level division being by function (training, inference…) it is operational vs embodied.A different set of components are available under each of these top level categories.

They include embodied emissions for training, maintenance and inference phases. The components they calculate embodied emissions for are: GPUs, CPUs, SSDs, HDDs, batteries, wind turbines, and solar panels.


> ![NOTE]
> That **carbon offsets are mentioned as a valid inventory item for the Data Center index** but never mentioned for the Green AI model index they suggest making decisions about this based on the jurisdiction you are operating in.


### Functional Unit

**Emissions per Training Cycle:**
The total carbon emissions (in CO2e) associated with the entire training process of the AI Model, from initial data processing to the final model.

**Emissions per Inference**: 
The carbon emissions (in CO2e) produced by a single inference made by AI Model. This includes the energy consumed during the prediction process and any cooling requirements.

### Impacts

- Carbon emissions (CO2e)
- There is also a water footprint component (m3/L)

### Data Sources

- There is no actual case study provided in the whitepaper
- The data requirements are \*high\* \- lots of very granular direct measurements are required to complete the measurement.

## EcoLogits

[Ecologits](https://ecologits.ai/latest/methodology/llm_inference/)

EcoLogits exposes an API that enables a user to estimate the energy consumption or GHG emissions for a named model. The intended use is not to do a calculator, but to look up precalculated values in their database via the API.

Its a calculation of impacts that is based on bottom-up modeling of the underlying infrastructure and has many assumptions regarding the hardware, the model architecture & deployment.

They exclude any training impacts. 

The unique selling point is the ability to query the energy consumption and emissions of a model by the EcoLogits API.

### Functional Unit
CO2e / request

### Impacts
Carbon emissions (CO2e)

## Energy Score

[AI Energy Score](https://huggingface.github.io/AIEnergyScore/)

Energy Score only considers GPU energy consumption during the inference phase. They use CodeCarbon to measure energy consumption during model runs on HF instances and automatically add the scores to a leaderboard.

The USP is that it uses direct measurements in a very reproducible, repeatable way, making sure the models are benchmarked fairly against one another. The trade off is that to enable this comparability, the application boundary is very narrow.

### Functional Unit
CO2e/1000 requests

### Impacts
Carbon emissions (CO2e)

### Data Sources
Direct measurements made for models run on Hugging Face instances using CodeCarbon.



# Rubric

In order to evaluate both current AI measurement proposals from external bodies and navigate our own exploration of the space we will employ this rubric.

## Adoption

* **Flexibility**: Can it be applied or extended easily as the AI ecosystem evolves.

  * For example agentic AI that calls other APIs on an inference request?

* **Granular**: Component wise, temporal, or just a single figure.

  * Does it give deeper insights into the sources of emissions and areas to focus on for reductions?

* **Run-Time & Design-Time**: 

  * Can you model the score for an AI that doesn't yet exist?

* **Explainability**: The framework should be explainable to ensure stakeholders can comprehend and trust the results.

  * Subjective statement regarding how easy it is to explain the score to non technical stakeholders (1-5, 1 being easy 5 being hard)

* **Broad Scope**:

  * Does the standard support measurement of all different forms of AI as defined in the scope?

* **Open Source & Proprietary**:

  * Can it be used to give a score to an unhosted Llama model? As in can a list of open source models be given a score independent of how they might be hosted.

  * Can it be used to give a score to ChatGPT? As in is this a score that OpenAI might be able to publish for each of their models.

* **Pathway to Policy & Certification**

  * **Consensus**: 

    * A collaborative process was used in the generation of the standard including multiple voices from a variety of organisations and stakeholders.

    * Standards developed through consensus are far more likely to be eventually adopted as policy. We need to demonstrate this isn’t the view of a few organizations with potentially hidden agendas, but a collaborative process involving multiple stakeholders including natural competitors.

  * **ISO**:

    * Does this standard have an intention to be, or a clear pathway to become, an ISO standard?

    * ISO is a further consensus based process involving 175 country bodies. ISO standards are strong signals to policy makers that a standard has gone through a rigorous process of review by many parties and is an industry agreement rather than the position of a few select organizations.

  * **IPR**:

    * Does the standard contain any language regarding the IP implications of adopting it? E.g. W3C and GSF standards offer a promise that the parties involved offer any relevant patents royalty free.

    * This is another concern for policy makers, if they adopt a standard as policy, will in 5 years time a company involved surface and claim royalty fees for a standard that is now mandated by a country.

  * **Alignment to Existing Measurement Standards**:

    * Does this metric align with existing standards such as LCA or GHG?

    * Is the intention to be a guidance to how to meet those standards vs. creating a new standard for a different audience/purpose/goal.

|  | GreenAI Index | EcoLogits | Energy Score | Berthelot et al (2024) LCA |
| :---- | ----- | ----- | ----- | ----- |
| **Flexibility** | ✅ | ❌ | ❌ | ✅ |
| **Granular** |  |  |  |  |
| Component | ✅ | ❌ | ❌ | ✅ |
| Time | ❌ | ❌ | ❌ | ❌ |
| **RunTime & DesignTime**   | ✅ | ✅ | ❌ | ✅ |
| **Explainability (1-5)**  | 3 | 3 | 4 | 3 |
| **Broad Scope**  | ✅ | ✅ | ✅ | ✅ |
| **Open Source & Proprietary** | ✅ | ✅ | ✅ | ✅ |
| **Pathway to certification & policy** |  |  |  |  |
| Consensus | ❌ | ❌ | ❌ | ❌ |
| ISO | ❓ | ❓ | ❌ | ❌ |
| IPR | ❌ | ❌ | ❌ | ❌ |
| Alignment to Existing Measurement Standards (ISO, LCA,GHG) | ✅ | ✅ | ❌ | ✅ |

## Life Cycle

The Green AI Committee at the GSF has previously defined Green AI as *“Green AI focuses on reducing the environmental impact of AI systems throughout their lifecycle. It prioritizes optimizing energy consumption, minimizing resource use, and reducing emissions. This approach emphasizes the standardization of measurement and metrics to ensure transparency, strengthen confidence in AI technologies, and drive continual improvement.”.*

Specifically they defined these life cycle stages which apply to Green AI and the GSF:

* **Prepare**: Problem definition, requirements analysis and engaging with end users and stakeholders.

* **Data Engineering**: Data collection and preprocessing.

* **Model Training**: Identifying evaluation measures, model selection, training and testing

* **System Integration**: Design, develop, and test the distributed end-to-end runtime environment in which the model will be deployed.

* **Runtime Operations**: The execution of the model in a runtime environment, including inference, maintenance, monitoring, consumer edge devices and datacenter/cloud usage.

* **End of Life**: “Un-deploy” the model in the runtime environment. 

The SCI measure SHALL incentivise optimisations at each stage of this lifecycle.

|  | GreenAI Index | EcoLogits | Energy Score | Berthelot et al (2024) LCA |
| :---- | ----- | ----- | ----- | ----- |
| Prepare | ❌ | ❌ | ❌ | ❌ |
| Data Engineering | ❌ | ❌ | ❌ | ❌ |
| Model training | ✅ | ❌ | ❌ | ✅ |
| System integration | ❌ | ❌ | ❌ | ❌ |
| Runtime operations | ✅ | ☑️ | ☑️ | ✅ |
| End of life | ❌ | ❌ | ❌ | ❌ |


## Clarity & Consistency

Clarity brings consistency. With a clear methodology and boundary the standard becomes easy to apply and use. With a clear methodology and boundary there is less room for interpretation of language by different teams and the results of a score will be consistent. The gold standard will be a measure where two different teams can independently measure the same AI by reading the SCI for AI and come up with the same figures.

* **Boundary**: Is the boundary clearly defined, how much room is left for interpretation by different teams. Is it obvious from the standard whether to include software components into the computation or whether to leave it out.

* **Methodology**: It’s not enough to simply include a software component in the boundary, to bring clarity and consistency we must define how to attribute that software components emissions into the functional unit. The common challenges are when there are resources shared amongst many different AI systems, how do you attribute a portion of the emissions to the AI system and functional unit in question? The more complex issue arises from past historical emissions such as training done in the past, what is the exact methodology for attributing past historical emissions into a functional unit. When we included the embodied emissions in the core SCI standard we included also a clear and unambiguous methodology for attributing the past emissions from the manufacture of a hardware device to the current emissions of a functional unit, like so:  `M = TE * (TiR/EL) * (RR/ToR)`

|  | GreenAI Index | EcoLogits | Energy Score | Berthelot et al (2024) LCA |
| :---- | ----- | ----- | ----- | ----- |
| Boundary | ✅ | ✅ | ✅ | ✅ |
| Methodology | ✅ | ✅ | ✅ | ✅ |

## Incentivizations

A measurement standard incentivizes some behaviours and disincentivizes others. For example some measurement standards *incentivise* the purchasing of carbon credits over increasing efficiency in your own value chain. Some measurement standards *disincentivise* time or spatial shifting of compute to take advantage of cleaner energy sources. 

The primary purpose of the SCI series of standards is to incentivize engineering optimizations of a software product to improve efficiency. For the SCI for AI to be a success it must incentivize a set of actions which the group agrees are positive actions to take this include:

* Efficiency improvements to the hosting infrastructure.
* Efficiency improvements in silicon chips.
* Efficiency improvements in the model architecture.
* Reducing the carbon footprint of training.
* Reducing the carbon footprint of data collection and processing.
* Running the AI system at times or in regions with cleaner electricity.
* Running the AI system on edge devices when that is more efficient.
* Leverage pre-trained models and transfer learning.
* Optimising the size of models.
* Use efficient file formats.
* Evaluate tradeoffs between accuracy and efficiency.
* Incentivise the disclosure of data required to perform calcualtions.
* Other Green AI patterns as detailed here: Take from here [https://patterns.greensoftware.foundation/catalog/ai](https://patterns.greensoftware.foundation/catalog/ai)

|  | GreenAI Index | EcoLogits | Energy Score | Berthelot et al (2024) LCA |
| :---- | ----- | ----- | ----- | ----- |
| Efficiency improvements to the hosting infrastructure | ✅ | ❌ | ❌ | ✅ |
| Efficiency improvements in silicon | ✅ | ❌ | ❌ | ✅ |
| Efficiency improvements in the model architecture | ✅ | ✅ | ✅ | ✅ |
| Reducing the carbon footprint of training | ✅ | ❌ | ❌ | ✅ |
| Reducing the carbon footprint of data collection and processing | ❌ | ❌ | ❌ | ❌ |
| Running the AI system at times or in regions with cleaner electricity | ✅ | ☑️ | ❌ | ✅ |
| Running the system on edge devices | ✅ | ❌ | ❌ | ✅ |
| Leverage pre-trained models and transfer learning | ✅ | ❌ | ❌ | ✅ |
| Optimising the size of models | ✅ | ✅ | ✅ | ❌ |
| Use efficient file formats | ✅ | ❌ | ❌ | ❌ |
| Evaluate tradeoffs between accuracy and efficiency | ❓ | ❓ | ❓ | ❓ |


# Software Boundary

When computing an SCI score for AI the software components below SHALL be included in the quantification:

## Training

### Definition 
What do we mean by "training"

### Rationale
Why are we including training.

### Allocation Methodology
This methodology SHALL be used for allocating training emissions to the the functional unit.

TODO

### Considerations
Any other considerations...

# Functional Unit 

TODO

