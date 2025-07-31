# GREEN SOFTWARE FOUNDATION WEBSITE SCI REPORT

**SCI:** `0.129 gCO2e/visit`

**Breakdown:**
- Development: `0.0002 gCO2e/visit`
- Servers: `0.3917 gCO2e/visit`
- Network: `0.0192 gCO2e/visit`
- User: `3.5737 gCO2e/visit`

--

**Application Name:** Green Software Foundation Website

**Application Version:** 1.1

**Application Description:** This is the main website for the Green Software Foundation, providing information about sustainable software practices, specifications, and community resources.

--

**Application URL:** https://greensoftware.foundation

**Organization Name:** Green Software Foundation

**Organization URL:** https://greensoftware.foundation

--

**Accountable Organization:** Green Software Foundation

**Accountable Person:** Joseph Cook, Head of R&D, GSF

**Accountable Contact:** joseph@greensoftware.foundation

--

**Measurement Date:** Aug 31 2024

**Measurement Timespan:** Aug 1 2024 - Aug 31 2024

**Measurement Manifest File:** https://raw.githubusercontent.com/Green-Software-Foundation/if-db/refs/heads/main/manifests/gsf-website/gsf-website-output.yml

**Measurement Visualizer Link:** https://viz.if.greensoftware.foundation/?url=https%3A%2F%2Fraw.githubusercontent.com%2FGreen-Software-Foundation%2Fif-db%2Frefs%2Fheads%2Fmain%2Fmanifests%2Fgsf-website%2Fgsf-website-output.yml

## Coefficients

| Coefficient | Description | Value | Unit | Source |
|-------------|-------------|-------|------|--------|
| grid-intensity | Carbon intensity of electricity grid (global average) | 765.49 | gCO₂e/kWh | [Cloud Carbon Footprint](https://www.cloudcarbonfootprint.org/) |
| storage-to-energy | Conversion from storage in TBh to energy | 1.2 | Wh/TBh | [Cloud Carbon Footprint](https://www.cloudcarbonfootprint.org/) |
| cpu-tdp | Thermal design power of processor used in CPU modeling | 205 | W | [Boavizta](https://boavizta.org/) |
| memory-to-energy | Conversion from memory usage in GBh to energy | 0.000392 | kWh/GBh | [Cloud Carbon Footprint](https://www.cloudcarbonfootprint.org/) |
| network-transfer-to-energy | Conversion from data transferred (GB) to energy | 0.001 | kWh/GB | [Sustainable Web Design](https://sustainablewebdesign.org/) |
| user-device-energy | Conversion from data rendered (GB) on devices to energy | 0.081 | kWh/GB | [Sustainable Web Design](https://sustainablewebdesign.org/) |
| iphone-embodied-carbon | Embodied carbon of iPhone 13 Pro | 54 | kg CO₂e | [Apple Environmental Report](https://www.apple.com/environment/) |
| macbook-embodied-carbon | Embodied carbon of MacBook Pro 13" M1 | 149.85 | kg CO₂e | [Apple Environmental Report](https://www.apple.com/environment/) |
| baseline-server-embodied | Embodied carbon of a default server (unscaled) | 1,000,000 | g CO₂e | [Cloud Carbon Footprint](https://www.cloudcarbonfootprint.org/) |

## Summary

We calculated the Software Carbon Intensity (SCI) score for the Green Software Foundation website using a bottom-up approach — estimating the emissions of each system component individually, rather than relying on broad top-down averages. The result was an SCI score of **0.129 gCO₂e per visit**, significantly lower than the global website average of 0.8 gCO₂e per visit. The calculation revealed that user device embodied carbon was the dominant contributor to emissions, highlighting the importance of including user-side impacts in software carbon assessments.

## Functional Unit

**Functional Unit:** visits

**Functional Unit Rationale:** The functional unit for this measurement was visits, sourced directly from Google Analytics. This choice allows us to compare performance across time and against other websites without penalizing growth. We used a full month of visit data and relied on Cloudflare to filter bot traffic, ensuring that only real human visits were counted. This unit is widely used in web analytics and enables meaningful comparison with other websites regardless of their implementation details.

## Key Insights

- The **embodied carbon of end-user devices** was the dominant source of emissions, contributing 3.5737 gCO₂e/visit out of the total 0.129 gCO₂e/visit
- Server-related emissions were significant, particularly during the Netlify build process, but still much smaller than user device impacts
- Networking and development emissions were minimal by comparison, each contributing less than 0.02 gCO₂e/visit
- The bottom-up approach enabled component-level visibility that top-down models like Sustainable Web Design cannot provide
- Including user-side emissions provides a much more complete and transparent picture of the full carbon cost of delivering digital services

## Methodologies

### Carbon (C)
*No direct carbon methodologies were used in this calculation.*

### Operational Carbon (O)
*No separate operational carbon methodologies were used. Operational carbon was calculated as Energy × Grid Intensity.*

### Embodied Carbon (M)

#### Server Embodied Carbon - Modeled
**Method:** modeled
**Description:** For components like GitHub and Netlify, we modeled representative server hardware using specifications from Azure's L-series VMs. These specs (e.g., 30TB SSD, 160 CPUs, 1280 GB RAM) were passed through the SciEmbodied model to estimate embodied emissions based on hardware manufacturing and expected lifespan.
**Key Coefficients:** baseline-server-embodied

#### Server Embodied Carbon - Baseline  
**Method:** modeled
**Description:** For simpler or less quantifiable infrastructure such as CDN or origin servers, we sourced a baseline value from Cloud Carbon Footprint. This was scaled by the proportion of the server's lifespan and storage used by the application.
**Key Coefficients:** baseline-server-embodied

#### User Device Embodied Carbon
**Method:** sourced  
**Description:** We sourced Apple's publicly reported figures for iPhone and MacBook devices from official Apple Environmental Reports. These were weighted based on the 90% mobile / 10% desktop user split observed in Google Analytics and scaled by the time users spent on the website (e.g., 40 seconds out of a 4-year device lifespan).
**Key Coefficients:** iphone-embodied-carbon, macbook-embodied-carbon

### Energy (E)

#### Storage Energy
**Method:** modeled
**Description:** For storage components such as GitHub or content delivery servers, we measured the total amount of data stored in terabytes using APIs, then modeled energy consumption by applying the storage-to-energy coefficient. This estimates the ongoing energy cost of keeping data available on disk, scaled to the measurement period duration.
**Key Coefficients:** storage-to-energy

#### CPU Energy  
**Method:** modeled
**Description:** CPU energy was calculated using directly measured utilization data collected from monitoring tools (htop). We used the thermal design power (TDP) as a baseline, which was adjusted using a utilization-to-power curve based on published research. This allowed us to estimate the real power draw of a server CPU under load, then convert to kilowatt-hours by scaling to the active time duration.
**Key Coefficients:** cpu-tdp

#### Memory Energy
**Method:** modeled  
**Description:** Memory energy was estimated using directly measured memory utilization data from monitoring tools. We calculated the amount of memory used over time, in gigabyte-hours (GBh), then applied the memory-to-energy coefficient. This represents the energy consumed by RAM while it remains active.
**Key Coefficients:** memory-to-energy

#### Network Transfer Energy
**Method:** modeled
**Description:** To account for the energy used when transferring data from the website to end users, we measured the size of the website's static assets (HTML, JavaScript, images, etc.) using the Google PageSpeed API. We multiplied this by the network-transfer-to-energy coefficient following the Sustainable Web Design model.
**Key Coefficients:** network-transfer-to-energy

#### User Device Energy  
**Method:** modeled
**Description:** We modeled the energy used by end-user devices when visiting the site. Using the same static asset size measurement, we applied the user-device-energy coefficient, reflecting the greater energy demands of rendering content on devices like smartphones and laptops. This estimate follows the Sustainable Web Design model.
**Key Coefficients:** user-device-energy

### Grid Carbon Intensity (I)

#### Global Average Grid Intensity
**Method:** sourced
**Description:** To convert energy use into carbon emissions, we sourced a global average grid intensity from Cloud Carbon Footprint. This figure was applied consistently across all energy calculations, regardless of where the servers or users were located, providing a standardized baseline for comparison.
**Key Coefficients:** grid-intensity

### Functional Unit (R)

#### Website Visits
**Method:** sourced
**Description:** The reference value used to normalize emissions was the number of website visits, directly measured daily via Google Analytics. Cloudflare filters were applied to exclude bot traffic, ensuring human-only data was used. Visit data was collected at daily resolution and integrated into the calculation.


## Component Breakdown

### Development

**SCI Score:** 0.0002 gCO₂e/visit  
**Calculation Method:** eim  
**Description:** Emissions from writing, storing, and managing the website's source code on GitHub. This includes the carbon footprint of repository storage, version control operations, and the infrastructure required to maintain the codebase throughout the development lifecycle.

**Methodologies Used:**
- **Energy:** Storage Energy
- **Grid Intensity:** Global Average Grid Intensity  
- **Embodied Carbon:** Server Embodied Carbon - Modeled
- **Functional Unit:** Website Visits

### Servers

**SCI Score:** 0.3917 gCO₂e/visit  
**Calculation Method:** eim  
**Description:** Emissions from Netlify builds, origin server storage, and CDN distribution. This encompasses the backend infrastructure that builds, stores, and serves the website — including build machines, origin servers, and the content delivery network used to deliver content to end users globally.

**Methodologies Used:**
- **Energy:** CPU Energy, Memory Energy, Storage Energy
- **Grid Intensity:** Global Average Grid Intensity
- **Embodied Carbon:** Server Embodied Carbon - Modeled, Server Embodied Carbon - Baseline  
- **Functional Unit:** Website Visits

### Network

**SCI Score:** 0.0192 gCO₂e/visit  
**Calculation Method:** eim  
**Description:** Emissions from data transmission across the internet from servers to end users. This includes the energy consumed by network infrastructure — such as routers, switches, and data links — to deliver the website's static content with each visit.

**Methodologies Used:**
- **Energy:** Network Transfer Energy
- **Grid Intensity:** Global Average Grid Intensity
- **Embodied Carbon:** None (assumed negligible)
- **Functional Unit:** Website Visits

### User

**SCI Score:** 3.5737 gCO₂e/visit  
**Calculation Method:** eim  
**Description:** Emissions from user-side device energy use and embodied emissions from device manufacturing. This includes the carbon cost of using smartphones, laptops, or other devices during a website visit — an often overlooked but significant part of the full carbon footprint of digital services.

**Methodologies Used:**
- **Energy:** User Device Energy
- **Grid Intensity:** Global Average Grid Intensity  
- **Embodied Carbon:** User Device Embodied Carbon
- **Functional Unit:** Website Visits