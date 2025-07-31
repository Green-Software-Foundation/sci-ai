# SCI Report Template and Guidance

## Instructions
This template provides a structured format for reporting Software Carbon Intensity (SCI) calculations. Fill in each section according to the guidance provided. Replace all `[PLACEHOLDER]` text with your specific information.

---

# [YOUR APPLICATION NAME] SCI REPORT

**SCI:** `[ENTER YOUR SCI SCORE WITH FUNCTIONAL UNIT]`
> **Guidance:** Enter your overall SCI score with functional unit. For example: `0.129 gCO2e/visit` or `2.4 gCO2e/request`

**Breakdown:**
```
[Component 1]: [SCI Score] [functional unit]
[Component 2]: [SCI Score] [functional unit]  
[Component 3]: [SCI Score] [functional unit]
[Component N]: [SCI Score] [functional unit]
```
> **Guidance:** List your top-level component breakdown. You have complete flexibility in how you break down your system, but you **must include all software components that are material** to your SCI calculation. These should be **one level deep** from your overall SCI score. The component SCI scores **must sum to your total SCI score**. Examples of components might be: Development, Servers, Network, User Devices, Database, API Gateway, etc.

**Application Name:** `[YOUR APPLICATION NAME]`

**Application Version:** `[VERSION NUMBER]`

**Application Description:** `[CLEAR DESCRIPTION OF YOUR SOFTWARE]`

> **Guidance:** Provide a clear description that software generalists can understand. Be specific about version numbers, deployment details, etc.

**Application URL:** `[URL TO YOUR APPLICATION OR DOCUMENTATION]`


**Organization Name:** `[YOUR ORGANIZATION]`

**Organization URL:** `[YOUR ORGANIZATION'S WEBSITE]`


**Accountable Organization:** `[ORGANIZATION RESPONSIBLE FOR THIS MEASUREMENT]`

**Accountable Person:** `[NAME AND TITLE OF RESPONSIBLE PERSON]`

**Accountable Contact:** `[EMAIL ADDRESS]`


**Measurement Date:** `[END DATE OF MEASUREMENT PERIOD]`

**Measurement Timespan:** `[START DATE] - [END DATE]`

**Measurement Manifest File:** `[LINK TO YOUR IMP FILE]`

**Measurement Visualizer Link:** `[LINK TO IF VISUALIZER FOR YOUR MANIFEST]`


## Coefficients

> **Guidance:** Include all key coefficients that are material to your calculation. You don't need to be exhaustive, but include coefficients you believe are important for others to understand your methodology. Each coefficient must have a name, description, value, unit, and source (ideally with a link).

| Coefficient | Description | Value | Unit | Source |
|-------------|-------------|-------|------|--------|
| `[coefficient-name]` | `[Clear description of what this coefficient represents]` | `[numerical value]` | `[unit of measurement]` | `[source with link if possible]` |
| `[coefficient-name-2]` | `[Clear description of what this coefficient represents]` | `[numerical value]` | `[unit of measurement]` | `[source with link if possible]` |

**Example:**
| Coefficient | Description | Value | Unit | Source |
|-------------|-------------|-------|------|--------|
| grid-intensity | Carbon intensity of electricity grid (global average) | 765.49 | gCO₂e/kWh | [Cloud Carbon Footprint](https://www.cloudcarbonfootprint.org) |

## Summary

`[PROVIDE AN EXECUTIVE SUMMARY OF YOUR CALCULATION]`

> **Guidance:** Write a clear executive summary explaining your approach, key findings, and how your SCI score compares to relevant benchmarks if available. This should be accessible to non-technical audiences.

## Functional Unit

**Functional Unit:** `[YOUR CHOSEN FUNCTIONAL UNIT]`

**Functional Unit Rationale:** `[EXPLANATION OF WHY THIS FUNCTIONAL UNIT WAS CHOSEN]`

> **Guidance:** Explain your choice of functional unit (e.g., per visit, per request, per user, per transaction). Justify why this unit is appropriate for your application and how the functional unit value was sourced, measured, or modeled.

## Key Insights

> **Guidance:** This is a subjective section to surface interesting insights you discovered from your measurement. What surprised you? What were the main contributors to emissions? What optimization opportunities did you identify?

- `[Key insight 1]`
- `[Key insight 2]`
- `[Key insight 3]`


## Methodologies

> **Guidance:** A methodology is a technique you use to generate an impact value (energy, embodied carbon, carbon intensity, operational carbon, or direct carbon). Every methodology must be categorized as either **sourced** (from third-party/supplier data), **measured** (directly measured by you), or **modeled** (estimated using proxies through models).

### Carbon (C)
> Use this section if you have methodologies that directly compute carbon emissions

#### `[Methodology Name]`
**Method:** `sourced` / `measured` / `modeled` *(choose one)*

**Description:** `[Detailed description of this methodology]`

**Key Coefficients:** `[Reference any coefficients from your coefficients table]`

### Operational Carbon (O)
> Use this section for methodologies that compute operational carbon emissions

#### `[Methodology Name]`
**Method:** `sourced` / `measured` / `modeled` *(choose one)*

**Description:** `[Detailed description of this methodology]`

**Key Coefficients:** `[Reference any coefficients from your coefficients table]`

### Embodied Carbon (M)
> Use this section for methodologies that compute embodied carbon emissions

#### `[Methodology Name]`
**Method:** `sourced` / `measured` / `modeled` *(choose one)*

**Description:** `[Detailed description of this methodology]`

**Key Coefficients:** `[Reference any coefficients from your coefficients table]`

### Energy (E)
> Use this section for methodologies that compute energy consumption

#### `[Methodology Name]`
**Method:** `sourced` / `measured` / `modeled` *(choose one)*

**Description:** `[Detailed description of this methodology]`

**Key Coefficients:** `[Reference any coefficients from your coefficients table]`

### Grid Carbon Intensity (I)
> Use this section for methodologies that determine carbon intensity of electricity

#### `[Methodology Name]`
**Method:** `sourced` / `measured` / `modeled` *(choose one)*

**Description:** `[Detailed description of this methodology]`

**Key Coefficients:** `[Reference any coefficients from your coefficients table]`

### Functional Unit (R)
> Describe how you obtained your functional unit values

#### `[Methodology Name]`
**Method:** `sourced` / `measured` / `modeled` *(choose one)*

**Description:** `[Detailed description of how functional unit values were obtained]`

## Component Breakdown

> **Guidance:** For each component listed in your breakdown section above, provide detailed information. Each component must have its own SCI score that uses the same functional unit as the parent. The methodologies listed should reference the methodologies defined in your Methodologies section above.

### `[Component Name 1]`

**SCI Score:** `[SCI value with functional unit]`
**Calculation Method:** `c` / `om` / `eim` *(choose one)*
> **Guidance:** 
> - **c** = Direct carbon calculation
> - **om** = Operational carbon + Embodied carbon calculation  
> - **eim** = Energy + Grid intensity + Embodied carbon calculation

**Description:** `[Clear description of this component's scope and role]`
> **Guidance:** Explain what this component is, how it differs from other components, and its role in the software system. Readers should understand the component's boundaries and responsibilities.

**Methodologies Used:**
- **Carbon:** `[List methodology names used for carbon calculations]` *(if using 'c' method)*
- **Operational Carbon:** `[List methodology names used for operational carbon]` *(if using 'om' or 'eim' method)*
- **Energy:** `[List methodology names used for energy calculations]` *(if using 'eim' method)*
- **Grid Intensity:** `[List methodology names used for grid intensity]` *(if using 'eim' method)*
- **Embodied Carbon:** `[List methodology names used for embodied carbon]` *(if using 'om' or 'eim' method)*
- **Functional Unit:** `[List methodology names used for functional unit]`

> **Guidance:** List the specific methodology names used for each impact type. These should reference the methodologies defined in your Methodologies section above. You may use multiple methodologies per category if needed.

### `[Component Name 2]`

**SCI Score:** `[SCI value with functional unit]`

**Calculation Method:** `c` / `om` / `eim` *(choose one)*

**Description:** `[Clear description of this component's scope and role]`

**Methodologies Used:**
- **Carbon:** `[List methodology names if using 'c' method]`
- **Operational Carbon:** `[List methodology names if using 'om' method]`
- **Energy:** `[List methodology names if using 'eim' method]`
- **Grid Intensity:** `[List methodology names if using 'eim' method]`
- **Embodied Carbon:** `[List methodology names if using 'om' or 'eim' method]`
- **Functional Unit:** `[List methodology names used for functional unit]`

### `[Continue for each component...]`

---

## Validation Checklist

Before submitting your SCI report, verify:

- [ ] All component SCI scores sum to the total SCI score
- [ ] All functional units are consistent across components and total
- [ ] All coefficients referenced in methodologies are included in the coefficients table
- [ ] All methodologies are categorized as sourced/measured/modeled
- [ ] All methodologies relate to C, O, M, E, I, or R
- [ ] Component descriptions clearly define scope and boundaries
- [ ] At least one level of component breakdown is provided
- [ ] All material components are included in the breakdown

---

## Examples

### Example Coefficient Entry:
```
| storage-to-energy | Conversion from storage in TBh to energy | 1.2 | Wh/TBh | [Cloud Carbon Footprint](https://cloudcarbonfootprint.org) |
```

### Example Methodology Entry:
```
#### Storage Energy
**Method:** modeled
**Description:** We measured the total amount of data stored in terabytes using APIs, then modeled energy consumption by applying the storage-to-energy coefficient. This estimates the ongoing energy cost of keeping data available on disk, scaled to the measurement period duration.
**Key Coefficients:** storage-to-energy
```

### Example Component Entry:
```
### Development
**SCI Score:** 0.0002 gCO₂e/visit
**Calculation Method:** eim
**Description:** Emissions from writing, storing, and managing the website's source code on GitHub.
**Methodologies Used:**
- **Energy:** Storage Energy
- **Grid Intensity:** Global Average Grid Intensity
- **Embodied Carbon:** Server Embodied Carbon - Modeled
- **Functional Unit:** Website Visits

### Servers
**SCI Score:** 0.3917 gCO₂e/visit  
**Calculation Method:** eim
**Description:** Emissions from Netlify builds, origin server storage, and CDN distribution.
**Methodologies Used:**
- **Energy:** CPU Energy, Memory Energy, Storage Energy
- **Grid Intensity:** Global Average Grid Intensity
- **Embodied Carbon:** Server Embodied Carbon - Modeled, Server Embodied Carbon - Baseline
- **Functional Unit:** Website Visits
```