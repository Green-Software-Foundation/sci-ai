# SCI Calculation Guidance for Practitioners

## Introduction

This guidance document helps practitioners understand how to calculate Software Carbon Intensity (SCI) scores, particularly if you're new to the SCI specification. We'll cover the key concepts with practical examples and real-world methodologies.

The SCI formula is: **SCI = (Energy × Grid Carbon Intensity + Embodied Carbon) ÷ Functional Unit**

However, there are multiple ways to approach this calculation depending on what data you have available and how detailed you want to be.

---

## Understanding Methodologies

A **methodology** is any technique you use to generate an impact value needed for your SCI calculation. Impact values include:
- **Carbon (C)**: Aggregate carbon emissions
- **Operational Carbon (O)**: Carbon from operating the software system, for example energy consumption
- **Embodied Carbon (M)**: Carbon from manufacturing/maintaining hardware
- **Energy (E)**: Energy consumption in kWh
- **Grid Carbon Intensity (I)**: Carbon intensity of electricity (gCO₂e/kWh)

Every methodology must be categorized as **sourced**, **measured**, or **modeled**.

### Sourced Methodologies

**Sourced** means you obtained the value from a third-party provider, academic paper, or existing data source.

#### Example 1: Microsoft Carbon Dashboard
You can source operational carbon directly from cloud provider dashboards:

**Methodology Name:** Microsoft Azure Carbon Dashboard  
**Method:** Sourced  
**Description:** Operational carbon emissions were extracted directly from the Microsoft Azure Sustainability Dashboard for our specific subscription and time period. The dashboard provides location-based emissions calculations for all Azure services consumed.  
**Source:** [Microsoft Azure Sustainability Dashboard](https://docs.microsoft.com/en-us/azure/carbon-optimization/)  
**Typical Values:** Varies by service and region, typically 0.1-0.8 kg CO₂e per service unit

#### Example 2: Published Grid Intensity Data
**Methodology Name:** WattTime  
**Method:** Sourced  
**Description:** Hourly grid carbon intensity values for the UK electricity grid were obtained from the WattTime API.  
**Source:** [WattTime API](https://www.watttime.org/)  
**Typical Values:** 50-300 gCO₂e/kWh depending on time of day and renewable generation

#### Example 3: Academic Research Coefficient
**Methodology Name:** Network Transfer Energy Coefficient  
**Method:** Sourced  
**Description:** Energy consumption for data transfer was calculated using the 0.001 kWh/GB coefficient from the Sustainable Web Design methodology.  
**Source:** Frick, T. (2016). [Sustainable Web Design](https://sustainablewebdesign.org/)  
**Typical Values:** 0.001 kWh/GB for network transfer energy

### Measured Methodologies

**Measured** means you directly observed or metered the value using monitoring tools or devices.

#### Example 1: Kepler for Energy Measurement
**Methodology Name:** Kepler Energy Monitoring  
**Method:** Measured  
**Description:** Real-time energy consumption was measured using Kepler, which uses eBPF to monitor CPU, memory, and GPU energy usage at the container level. Measurements were collected every 30 seconds and aggregated over the measurement period.  
**Source:** [Kepler (Kubernetes Energy Meter)](https://sustainable-computing.io/)  
**Implementation:** Deployed as DaemonSet in Kubernetes cluster, exports metrics to Prometheus  
**Typical Values:** 0.1-50 Watts per container depending on workload

#### Example 2: Smart Meter Energy Data
**Methodology Name:** Building Energy Meter  
**Method:** Measured  
**Description:** Energy consumption for on-premises servers was measured using smart meters installed at the server rack level, providing 5-minute interval readings.  
**Source:** Direct measurement via Schneider Electric IoT energy meters  
**Typical Values:** 200-2000 Watts per rack depending on server utilization

#### Example 3: Cloud Provider API Measurements
**Methodology Name:** AWS CloudWatch Energy Metrics  
**Method:** Measured  
**Description:** Energy consumption data was retrieved from AWS CloudWatch metrics, which provides direct measurements from the underlying hardware infrastructure.  
**Source:** [AWS CloudWatch](https://docs.aws.amazon.com/cloudwatch/)  
**Typical Values:** Varies by instance type, 10-500 Watts per instance

### Modeled Methodologies

**Modeled** means you estimated the value using proxy observations passed through mathematical models or formulas.

#### Example 1: CPU Utilization to Energy Model
**Methodology Name:** Teads CPU Power Curve  
**Method:** Modeled  
**Description:** Energy consumption was estimated from CPU utilisation using a power curve and multiplied by the TDP, the thermal design power of the processor.  
**Source:** Teads Engineering. [Building an AWS EC2 Carbon Emissions Dataset](https://medium.com/teads-engineering/building-an-aws-ec2-carbon-emissions-dataset-3f0fd76c98ac)  
**Key Coefficients:** TDP values from processor specifications (e.g., 205W for Intel Xeon)  
**Typical Accuracy:** ±10% for CPU utilization above 20%

#### Example 2: Memory Usage to Energy Model
**Methodology Name:** Cloud Carbon Footprint Memory Model  
**Method:** Modeled  
**Description:** Memory energy consumption was estimated using the coefficient 0.000392 kWh/GBh (kilowatt-hours per gigabyte-hour). This converts memory usage over time into energy consumption.  
**Source:** [Cloud Carbon Footprint Methodology](https://www.cloudcarbonfootprint.org/docs/methodology)  
**Formula:** Energy = Memory_GB × Time_Hours × 0.000392  
**Typical Values:** 0.001-0.1 kWh per GB of memory per hour

#### Example 3: Storage to Energy Model
**Methodology Name:** SSD Energy Consumption Model  
**Method:** Modeled  
**Description:** Energy consumption for data storage was estimated using 1.2 Wh/TBh (watt-hours per terabyte-hour), representing the ongoing energy cost of keeping data available on SSD storage.  
**Source:** [Cloud Carbon Footprint Storage Model](https://www.cloudcarbonfootprint.org/docs/methodology#storage)  
**Formula:** Energy = Storage_TB × Time_Hours × 0.0012  
**Typical Values:** 0.1-10 Wh per TB per hour

### Best Practices for Methodologies

1. **Citation is Critical**: Always provide verifiable sources for your methodologies
2. **Document Assumptions**: Clearly state any assumptions or limitations
3. **Specify Accuracy**: If known, provide accuracy ranges or confidence intervals
4. **Version Control**: Note version numbers or publication dates for sources
5. **Reproducibility**: Provide enough detail for others to replicate your approach

---

## Component Breakdown Approaches

When breaking down your SCI calculation into components, you have several calculation approaches available. Choose the approach that best fits your available data and desired level of detail.

### Approach 1: Aggregate Carbon (C Method)

Use this when you have a single carbon emissions value for your component.

**When to Use:**
- You have total carbon emissions from a supplier dashboard
- Your component aggregates many sub-components and you only have the total
- You're using published carbon footprint data

**Formula:** `Component SCI = Total Carbon ÷ Functional Unit`

**Example:**
```
Component: Third-Party API Service
Total Carbon: 15.2 kg CO₂e/month (from supplier report)
Functional Unit: 50,000 API calls/month
Component SCI = 15.2 kg CO₂e ÷ 50,000 calls = 0.304 g CO₂e/call
```

### Approach 2: Using Disclosed SCI Scores (C Method)

Use this when you can find published SCI scores for similar services or components.

**When to Use:**
- Published SCI scores exist for your component type
- Industry benchmarks or certified values are available
- You're using standardized services (e.g., CDN, cloud storage)

**Process:**
1. Find relevant published SCI score
2. Normalize the functional unit to match yours
3. Apply to your usage volume

**Example:**
```
Component: Content Delivery Network
Published SCI: 0.5 g CO₂e/GB (from CDN provider)
Your data transfer: 100 GB/month
Your functional unit: 10,000 visits/month
Data per visit: 100 GB ÷ 10,000 visits = 0.01 GB/visit
Component SCI = 0.5 g CO₂e/GB × 0.01 GB/visit = 0.005 g CO₂e/visit
```

### Approach 3: Operational + Embodied (OM Method)

Use this when you have operational carbon from suppliers but need to add embodied carbon.

**When to Use:**
- Cloud provider gives you operational emissions (O)
- You need to add embodied carbon for complete picture
- You have energy data and grid intensity, giving you operational carbon

**Formula:** `Component SCI = (Operational Carbon + Embodied Carbon) ÷ Functional Unit`

**Example:**
```
Component: Database Server
Operational Carbon: 8.5 kg CO₂e/month (from AWS dashboard)
Embodied Carbon: 1.2 kg CO₂e/month (from server lifecycle model)
Functional Unit: 25,000 queries/month
Component SCI = (8.5 + 1.2) kg CO₂e ÷ 25,000 queries = 0.388 g CO₂e/query
```

### Approach 4: Energy + Intensity + Embodied (EIM Method)

Use this for maximum transparency and control over your calculation.

**When to Use:**
- You want full visibility into your calculation
- You have detailed monitoring data available
- You need to optimize specific aspects (energy vs. embodied)
- No suitable operational carbon data is available

**Formula:** `Component SCI = (Energy × Grid Intensity + Embodied Carbon) ÷ Functional Unit`

**Example:**
```
Component: Web Server
Energy: 450 kWh/month (from monitoring tools)
Grid Intensity: 250 g CO₂e/kWh (regional grid data)
Embodied Carbon: 0.8 kg CO₂e/month (server lifecycle model)
Functional Unit: 100,000 requests/month

Operational Carbon = 450 kWh × 250 g CO₂e/kWh = 112.5 kg CO₂e
Total Carbon = 112.5 + 0.8 = 113.3 kg CO₂e
Component SCI = 113.3 kg CO₂e ÷ 100,000 requests = 1.133 g CO₂e/request
```

### Choosing Your Approach

| Available Data | Recommended Approach | Example Use Case |
|---------------|---------------------|------------------|
| Total carbon only | **Approach 1 (C Method)** | Supplier provides total carbon footprint |
| Published SCI scores | **Approach 2 (Disclosed SCI)** | Using a database that has published a SCI score |
| Two separate values for operational carbon and embodied data from different methodologies | **OM Method** | Cloud dashboard + embodied carbon model |
| Fine-grained information running your own infrastructure (energy, embodied, grid intensity) | **EIM Method** | When you own your own infrastructure and know the energy, embodied and grid intensity |

---

## Worked Example: GSF Website

Let's walk through the GSF Website calculation to see these concepts in practice.

### Overall Structure
- **Total SCI:** 0.129 gCO₂e/visit
- **Method:** EIM (Energy + Intensity + Embodied)
- **Components:** Development, Servers, Network, User

### Component 1: Development (EIM Method)
**What it includes:** GitHub repository storage and source code management

**Methodologies Used:**
- **Energy:** Storage Energy (modeled using 1.2 Wh/TBh coefficient)
- **Grid Intensity:** Global Average (sourced from Cloud Carbon Footprint)
- **Embodied Carbon:** Server hardware model (modeled using Azure L-series specs)

**Calculation:**
```
Storage: 0.8 MB → Energy via coefficient → 0.0000096 kWh/month
Grid Intensity: 765.49 gCO₂e/kWh
Embodied: Server model → 1.49 g CO₂e/month
Visits: 50,000/month
Result: 0.0002 gCO₂e/visit
```

### Component 2: Servers (EIM Method)
**What it includes:** Netlify builds, origin server, CDN distribution

**Methodologies Used:**
- **Energy:** CPU Energy (measured via monitoring), Memory Energy (measured), Storage Energy (modeled)
- **Grid Intensity:** Global Average (sourced)
- **Embodied Carbon:** Mix of modeled (Netlify) and baseline (CDN/Origin)

**Calculation:**
```
CPU Energy: Measured utilization → Power curve → 156 kWh/month
Memory Energy: Measured usage → CCF coefficient → 12 kWh/month  
Storage Energy: Modeled via coefficient → 0.5 kWh/month
Total Energy: 168.5 kWh/month
Operational: 168.5 × 765.49 = 129,005 g CO₂e/month
Embodied: Server models + CDN baseline = 691 g CO₂e/month
Total: 129,696 g CO₂e/month ÷ 50,000 visits = 2.59 g CO₂e/visit
```

### Component 3: Network (EIM Method)
**What it includes:** Data transfer from servers to users

**Methodologies Used:**
- **Energy:** Network Transfer Energy (measured site size × SWD coefficient)
- **Grid Intensity:** Global Average (sourced)
- **Embodied Carbon:** None (assumed negligible)

### Component 4: User (EIM Method)
**What it includes:** End-user device energy and embodied emissions

**Methodologies Used:**
- **Energy:** User Device Energy (modeled using device rendering coefficient)
- **Grid Intensity:** Global Average (sourced)
- **Embodied Carbon:** Device specifications (sourced from Apple reports)

### Lessons for Your Calculation

1. **Start with what you have** - Don't let perfect be the enemy of good; use available data and clearly document limitations
2. **Mix methods appropriately** - Combine measured, sourced, and modeled approaches where it makes sense
3. **Include user impacts** - These are often larger than server-side emissions but frequently overlooked
4. **Document everything** - The GSF example provides extensive methodology documentation that enables reproduction and improvement

---

## Getting Started Checklist

Before beginning your SCI calculation:

- [ ] **Define your system boundary** - What software components will you include?
- [ ] **Choose your functional unit** - What unit best represents value delivered to users?
- [ ] **Inventory your data sources** - What monitoring, dashboards, or APIs do you have access to?
- [ ] **Identify your components** - How will you break down your system (at least one level deep)?
- [ ] **Select calculation approaches** - Which components will use C, OM, or EIM methods?
- [ ] **Document your methodologies** - Prepare citations and sources for all coefficients and models
- [ ] **Plan for validation** - How will you verify your results make sense?

Remember: The goal is not perfection, but transparency and continuous improvement. Start with the data you have, document your assumptions clearly, and refine your approach over time.

---

## Additional Resources

- [SCI Specification](https://sci.greensoftware.foundation/) - Official specification document
- [Cloud Carbon Footprint](https://www.cloudcarbonfootprint.org/) - Open source methodology and tools
- [Sustainable Web Design](https://sustainablewebdesign.org/) - Web-specific carbon calculation methods
- [Green Software Foundation](https://greensoftware.foundation/) - Community and additional resources
- [Boavizta](https://boavizta.org/) - Environmental impact assessment tools and data