# Project EDEN

**Environmental Data and Evaluation Network**  
*Agricultural research, food science and cultivation optimisation platform*

## 0. Overall

### 0.1 Background

The project originated from questions about natural radioactivity in bananas: whether activity varies by cultivar, size, weight, geographical origin or sample population. It expands to other fruits and vegetables, chemical and pesticide impacts, biological engineering, and agricultural optimisation.

### 0.2 Objectives

- Understand how agriculture operates today before proposing improvements.
- Identify existing workflows, datasets, scientific models, software and unresolved problems.
- Build a shared, evidence-based scientific knowledge base in Python.
- Recommend suitable crops, fertilisers and three-cycle planting plans.
- Optimise costs, yield, resource reuse and other farming objectives.
- Assess potential impacts of cultivation practices on produce composition, quality and safety.

### 0.3 Scope and components

| Component | Purpose |
|---|---|
| EDEN Core | Research, data and scientific computational engines |
| EDEN Cultivate | Plant planning and resource optimisation |
| EDEN Vitality | Produce quality and safety assessment |

The research covers conventional and soilless agriculture. Hydroponics is the initial priority for crop sequencing; support for soil-based rotation can be added using method-specific rules after research. All implementation is code-based, primarily Python, using existing data and validated models rather than requiring original physical experiments.

### 0.4 Development principles

- Research first; implementation second.
- Reuse validated existing models where appropriate rather than reinventing them.
- Conduct EDA only when useful.
- Separate measured observations, modelled estimates, research-based inferences and unknowns.
- Do not sacrifice agronomic or safety constraints for cost savings.
- Treat missing data as unknown, not zero or evidence of safety.

### 0.5 Project workstream

1. Gather data and conduct research to identify existing agricultural workstreams, workflows and solutions.
2. Conduct exploratory data analysis (EDA) where needed to understand the available data and its limitations.
3. Compile an evidence-backed list of reactions and interactions between substances, including their causes, conditions and impacts. Investigate nitrate and chloride as an example without assuming that mixing them causes a direct chemical reaction.
4. Identify the plants being considered and record their respective properties and cultivation requirements.
5. Recommend suitable fertilisers and plants, optimising against the user's selected objective and the available evidence.
6. Develop a web application where users specify what they want to plant and receive a plan for the next three growing cycles, with cost-effective or optimal methods such as using compatible fertilisers already in stock across crops and cycles.
7. Research agriculture and farming methods, including cultivation systems, soil types and hydroponics, to support method-specific recommendations.

### 0.6 Web application vision

The web application has two tabs: Tab 1, Food Assessment (EDEN Vitality), for the general public; and Tab 2, Plant Planning (EDEN Cultivate), for farmers. The existing workflow numbers below identify the detailed specifications, not the tab order or implementation priority.

| Workflow | User inputs | Intended output |
|---|---|---|
| 1: Plant Planning | Desired crops, last three crops planted, land area, geographical region, temperature, current and upcoming seasons, available fertilisers and selected cost optimisation method | A crop rotation or method-appropriate crop sequencing plan for the next three growing cycles, with fertiliser recommendations, inventory reuse, additional purchases and estimated costs |
| 2: Health of Fruits and Vegetables | Fruit or vegetable type, growing location, fertilisers and pesticides used, application details and other relevant growing or handling factors | Evidence-supported assessment of potential impacts on the produce, including excessive chemical usage, with uncertainties and further testing needs |

Prioritise Tab 1, Food Assessment, for initial research and implementation. Users enter the fruit or vegetable type, growing location and any known fertiliser, pesticide or bioengineering details to explore evidence-supported potential concerns. Tab 2, Plant Planning, remains in scope for a later stage because it requires more farm-specific inputs. Detailed inputs, processing and outputs are described in Phases 6 and 7; phase numbering does not dictate implementation order.

## Phase 0 — Current State of Agriculture (Highest Priority)

### 0.1 Current agricultural operations

#### 0.1.1 End-to-end lifecycle

- Market demand, production planning and crop selection.
- Site preparation, seeds, germination and transplantation.
- Irrigation, fertilisation, pest and disease management.
- Monitoring, intervention, harvesting and quality testing.
- Storage, packaging, transportation and distribution.
- Cleaning, maintenance, waste management and preparation for the next crop.

#### 0.1.2 Current decision-making

- How farmers select crops, fertilisers, pesticides and planting schedules.
- How crop rotation and crop sequencing are currently planned.
- How farmers manage inventory, budgets, labour, water and energy.
- How decisions differ by farm size, region, climate and production method.

### 0.2 Farming methods

#### 0.2.1 Soil-based agriculture

- Conventional, organic, regenerative and raised-bed farming.
- Soil types: sandy, clay, silt, loam and other relevant classifications.
- Soil fertility, pH, drainage, salinity, nutrient retention and crop rotation.

#### 0.2.2 Hydroponics

- Nutrient film technique (NFT), deep water culture (DWC), drip, Kratky and ebb-and-flow systems.
- Open versus recirculating nutrient systems; substrates and root-zone conditions.
- Nutrient monitoring, pH, electrical conductivity (EC), oxygenation and water quality.
- Crop changeovers, sanitation, nutrient carryover and equipment compatibility.

#### 0.2.3 Other cultivation systems

- Aeroponics and aquaponics.
- Greenhouses, indoor and vertical farming, controlled environment agriculture (CEA).
- Precision agriculture and automation as approaches that can overlap with cultivation methods.

#### 0.2.4 Comparison framework

- Suitable crops, climate, land and infrastructure requirements.
- Capital and operating costs, labour, water, electricity and nutrients.
- Yield per area and time, quality, environmental impacts and failure risks.
- Existing technology, commercial adoption, data availability and limitations.

### 0.3 Evidence of current practice

- Prioritise 2020–2026 evidence for the current-state baseline; update as research progresses.
- Retain older foundational literature and the longest useful historical datasets.
- Examine actual commercial farm case studies, government and university guidance, industry surveys and scientific publications.
- Distinguish commercially established practices from pilot projects and emerging research.

### 0.4 Deliverables

- As-Is agricultural workflow maps and farming-method comparison.
- Evidence-backed description of current technologies, economics and operational problems.
- Prioritised research questions and initial scope decisions.

## Phase 1 — Existing Solutions and Gap Analysis

### 1.1 Existing workstreams

#### 1.1.1 Software and scientific models

- Farm management software, crop scheduling, nutrient dosing and environmental control.
- Crop growth simulation, chemical equilibrium, food composition and risk assessment.
- Optimisation algorithms, AI, sensor systems and decision-support tools.
- Open-source repositories, APIs and commercial solutions.

#### 1.1.2 Evaluation

- Compare features, scientific validation, adoption, costs, licences and Python integration.
- Identify what can be reused, integrated, improved or must be developed.
- Investigate whether three-cycle planning, inventory reuse and integrated quality assessment already exist.

### 1.2 Candidate resources (to verify)

- AquaCrop / AquaCrop-OSPy, PCSE / WOFOST, DSSAT and APSIM.
- Crop Ontology, USDA FoodData Central, PubChem and PHREEQC.
- NASA POWER, SoilGrids, FAOSTAT and Codex Alimentarius.
- OR-Tools and other mathematical optimisation libraries.

### 1.3 Deliverables

- Solution registry, feature comparison and evidence-backed gap analysis.
- Reuse-versus-build decisions and feasibility assessment.

## Phase 2 — Data Gathering and Research Inventory

Data collection begins in Phase 0 and continues throughout the project.

### 2.1 Data domains

- Plant taxonomy, cultivars, growth, nutrition and historical yield.
- Chemical properties, interactions, fertilisers, pesticides and residues.
- Climate, geography, soil, water, hydroponic conditions and farming methods.
- Crop sequencing, disease, genetics, food composition and natural radioactivity.
- Economics, market demand, resources, regulations and food safety standards.

### 2.2 Research registries

| Registry | Contents |
|---|---|
| Research | Papers, guidance and supporting documentation |
| Dataset | Datasets, APIs, historical records and coverage |
| Solution | Software, algorithms, repositories and models |
| Gap | Unresolved problems, evidence and potential improvements |

### 2.3 Source metadata

- Source URL, publisher, publication date, retrieval date and licence.
- Geographic and temporal coverage, units, granularity and update frequency.
- Methodology, reliability, uncertainty, limitations and applicable crops or conditions.
- Access method, file format and integration feasibility.

## Phase 3 — Data Processing and EDA

### 3.1 Data engineering

- Collect and preserve raw data; standardise processed data separately.
- Harmonise units, crop identifiers, chemical identifiers, dates and geographical references.
- Validate schemas, duplicates, missing values and conflicting sources.

### 3.2 Exploratory data analysis (where needed)

- Distributions, outliers, missingness, correlations and coverage.
- Compare species, cultivars, regions, seasons and farming methods.
- Identify bias, confounding variables and insufficient sample sizes.
- Do not interpret correlation as causation.

### 3.3 Deliverables

- Reproducible Python ingestion and cleaning pipelines, data dictionary and EDA findings.

## Phase 4 — Scientific Knowledge Base (EDEN Core)

### 4.1 Chemical and substance interactions

#### 4.1.1 Interaction types

- Direct reactions, precipitation, solubility, stability and pH effects.
- Nutrient antagonism and synergy, salinity, toxicity and biological interactions.
- Chemical–chemical, chemical–plant, chemical–soil, chemical–water and environmental interactions.
- Fertiliser–fertiliser, fertiliser–pesticide and pesticide–plant compatibility.
- Potential dietary exposure and human health implications.

#### 4.1.2 Interaction records

- Substance identities, interaction mechanism, concentration range and conditions.
- Affected species, cultivar, growth stage and cultivation method.
- Cause, observed impact, severity, uncertainty and supporting references.
- Example research question: under what conditions does chloride affect nitrate uptake? Do not assume that mixing the ions causes a harmful direct reaction.

### 4.2 Plant properties

#### 4.2.1 Identification and growth

- Species, family, cultivar, seed characteristics, root structure and plant size.
- Germination, maturity, harvest duration, yield and crop history compatibility.

#### 4.2.2 Cultivation requirements

- Temperature, humidity, light, water, macro- and micronutrients.
- Soil, substrate, pH, EC and suitable hydroponic systems.
- Salinity tolerance, disease susceptibility and environmental stress.

#### 4.2.3 Produce properties

- Nutrition, mineral composition, weight, maturity and natural radioactivity.
- Genetics, selective breeding, bioengineering and cultivar-specific differences.
- Quality, shelf life, production cost and market value.

### 4.3 Fertilisers and pesticides

- Product identity, active ingredients, composition, nutrient concentration and cost.
- Crop suitability, documented application constraints, compatibility and persistence.
- Residues, regulatory limits, authorised uses and pre-harvest intervals.
- Distinguish product inventory from previously used nutrient solutions.

### 4.4 Environmental and farming knowledge

- Climate, soil, water, equipment, growing methods, resource use and costs.
- Crop disease, pathogens, sanitation and crop changeover requirements.

## Phase 5 — Computational Engines

### 5.1 Scientific calculations

- Crop and environmental suitability, nutrient requirements and compatibility checks.
- Nutrient balance and carryover modelling where measurements support it.
- Crop growth, yield, resource consumption and cost estimation.
- Produce composition and exposure assessment using validated methods.

### 5.2 Optimisation framework

- Hard constraints: crop suitability, capacity, budget where specified, agronomic requirements and safety.
- Soft objectives: cost, yield, profit, quality, inventory reuse, sustainability and risk.
- Compare multi-objective or multi-phase optimisation approaches.
- Report infeasible scenarios and explain trade-offs.

## Phase 6 — Workflow 1: Plant Planning (EDEN Cultivate)

### 6.1 Inputs

- Last three crops and planting dates; desired or excluded crops.
- Land area or growing capacity, country, region and farming method.
- Current temperature, current and future seasons, climate and environmental controls.
- Soil or substrate conditions, water quality and hydroponic system details.
- Existing fertiliser inventory, nutrient solution measurements, budget and equipment.
- Labour, electricity, water, market demand and selected optimisation objective.

### 6.2 Processing

1. Filter suitable crops for the specified growing conditions.
2. Evaluate crop history and method-specific constraints.
3. Generate feasible sequences for the next three growing cycles.
4. Estimate nutrient requirements and select compatible fertilisers.
5. Compare inventory use, purchases, operational costs and expected outcomes.
6. Rank plans and explain assumptions, trade-offs and uncertainties.

### 6.3 Fertiliser reuse

- Inventory reuse: share unused stock across cycles to reduce purchasing costs.
- Formulation reuse: select crops with compatible nutrient requirements.
- Solution reuse: assess residual nutrient composition, contamination and sanitation before considering reuse. EC alone is insufficient to establish individual nutrient concentrations.

### 6.4 Farming-method distinctions

- Initial crop sequencing implementation: hydroponics, including equipment compatibility, solution management and sanitation.
- Potential soil-based extension: soil fertility, nutrient depletion, soil-borne disease and conventional rotation rules.

### 6.5 Outputs

- Three-cycle plan with crops, planting and harvest schedules and estimated duration.
- Recommended fertiliser types, inventory utilisation and additional purchases.
- Estimated cost, yield, profit, resource consumption and savings against a defined baseline.
- Alternative cost-effective, maximum-yield, maximum-profit, quality, sustainability, resource-reuse, minimum-risk and balanced plans where supported by data.
- Constraints, warnings, evidence and missing information.

## Phase 7 — Workflow 2: Health of Fruits and Vegetables (EDEN Vitality)

### 7.1 Inputs

For the initial public-facing tab, start with fruit or vegetable type and collect growing location and other details where known. Allow users to mark information as unknown; explain how missing information limits the assessment rather than inventing inputs or treating the food as safe or unsafe. The following fields describe the fuller assessment when information is available.

- Fruit or vegetable type, species, cultivar, size, weight and maturity.
- Country, region, farm and cultivation method.
- Fertiliser and pesticide identity, composition, amount, frequency and application dates.
- Soil, water, climate, pollution and biological or genetic factors.
- Harvest dates, storage, transport and laboratory results when available.

### 7.2 Assessment domains

#### 7.2.1 Natural food properties

- Natural radioactivity, including potassium-40; distinguish total activity from activity per unit mass.
- Compare bananas initially, then other fruits and vegetables across cultivars and origins where data permit.
- Nutritional composition, minerals, vitamins and physical quality.

#### 7.2.2 Agricultural and environmental impacts

- Fertiliser effects, nutrient accumulation and chemical interactions.
- Potential impacts of excessive fertiliser or pesticide usage, assessed using application amounts, timing and relevant measurements or validated models.
- Pesticide residues, potential exposure and regulatory comparison.
- Heavy metals, environmental contaminants, pathogens and biological hazards.
- Genetics, breeding, bioengineering, maturity and post-harvest effects.

### 7.3 Processing and outputs

- Retrieve baseline produce properties and relevant scientific evidence.
- Evaluate documented cultivation conditions and agricultural inputs.
- Estimate impacts only where validated models and sufficient inputs exist.
- Report measured values, estimates, potential impacts and unknowns separately.
- Compare applicable regulatory limits with suitable measurements or qualified estimates.
- Return quality and safety findings, uncertainties and recommendations for further testing.

Knowing a fertiliser, pesticide or country of origin alone does not establish actual residue levels or food safety. This system is not a replacement for laboratory testing.

## Phase 8 — Integration and Validation

### 8.1 Workflow integration

- Plant Planning generates candidate cultivation scenarios.
- Produce Health evaluates potential quality and safety implications.
- Feed supported findings back into the optimiser to refine plans.
- Keep independent assessments available for already harvested produce.

### 8.2 Validation

- Compare predictions with published studies, actual farm records and measured results.
- Benchmark against current farming practices and existing software.
- Validate units, constraints, uncertainty, geographic applicability and edge cases.
- Avoid unsupported claims of optimality, savings or safety.

## Phase 9 — Python Application

Deliver a web application backed by Python, where users submit farm or produce details and view the results of the two workflows.

### 9.1 Application features

- Tab 1 (initial priority): public-facing produce assessment covering potential chemical and bioengineering concerns, source traceability and uncertainty reporting. Do not infer a safety verdict solely from chemical use, origin or bioengineering status.
- Tab 2 (later stage): farmer-facing input interface, three-cycle planning and alternative plan comparison.
- Visualisations, cost breakdowns and exportable results.

### 9.2 Candidate technology stack

| Purpose | Candidate tools |
|---|---|
| Processing | Pandas, NumPy, optionally Polars |
| Storage | DuckDB, Parquet |
| Collection and validation | Requests, HTTPX, Pandera, Pydantic |
| Scientific analysis | SciPy, Statsmodels |
| Optimisation | OR-Tools, Pyomo |
| Geospatial analysis | GeoPandas, Rasterio |
| Machine learning (if justified) | Scikit-learn, XGBoost, PyTorch |
| Visualisation and application | Matplotlib, Plotly, Streamlit, FastAPI |

### 9.3 Implementation approach

- Modular Python repository with data, research, notebooks, source code, application and tests.
- Create modules only when needed; avoid duplicate implementations.
- Introduce machine learning only when data and a defined prediction task justify it.

## Immediate next step

Begin research for Tab 1: identify existing consumer food-assessment workflows, suitable datasets and validated assessment methods. Establish what can be explained from fruit or vegetable type, growing location and known agricultural inputs, and what requires application records or measurements. Prioritise plant properties, fertiliser and pesticide composition, chemical interactions, bioengineering evidence and uncertainty reporting. Use the relevant work in Phases 0–4 and 7 before committing to assessment algorithms or application development; defer detailed crop-planning and optimisation work for Tab 2.

**Status:** Planning document; research and validation are not yet complete. Candidate resources are leads, not verified dependencies or findings.
