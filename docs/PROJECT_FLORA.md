# Project FLORA

**Agricultural research and decision support**  
*Agricultural research, food science and cultivation optimisation platform*

This document defines FLORA's overall scope, shared knowledge and scientific requirements. Detailed pipeline requirements are in [T1 — Food Assessment and Product Substitution](T1_FOOD_ASSESSMENT.md) and [T2 — Crop Rotation Planning](T2_PLANT_PLANNING.md). Implementation order, progress and remaining tasks belong in [workflow and TODO](TODO.md).

## 1 Project overview

### 1.1 Background

The project originated from questions about natural radioactivity in bananas: whether activity varies by cultivar, size, weight, geographical origin or sample population. It expands to other fruits and vegetables, chemical and pesticide impacts, biological engineering, and agricultural optimisation.

### 1.2 Objectives

- Understand how agriculture operates today before proposing improvements.
- Identify existing workflows, datasets, scientific models, software and unresolved problems.
- Build a shared, evidence-based scientific knowledge base in Python.
- Recommend suitable crops, fertilisers and three-cycle planting plans.
- Optimise costs, yield, resource reuse and other farming objectives.
- Assess potential impacts of cultivation practices on produce composition, quality and safety.
- Make T1's main application a comparison of farming choices: can the same farming outcome be achieved with lower documented risks to human health and acceptable trade-offs? Use supported findings to influence T2's choices.

### 1.3 Scope and components

| Component | Purpose |
|---|---|
| FLORA Core | Research, data and scientific computational engines |
| FLORA Cultivate | Crop Rotation Planning and resource optimisation |
| FLORA Vitality | Food Assessment and Product Substitution |

The research covers conventional and soilless agriculture. Hydroponics is the initial priority for crop sequencing; support for soil-based rotation can be added using method-specific rules after research. All implementation is code-based, primarily Python, using existing data and validated models rather than requiring original physical experiments.

### 1.4 Development principles

- Research first; implementation second.
- Reuse validated existing models where appropriate rather than reinventing them.
- Conduct EDA only when useful.
- Separate measured observations, modelled estimates, research-based inferences and unknowns.
- Do not sacrifice agronomic or safety constraints for cost savings.
- Treat missing data as unknown, not zero or evidence of safety.

### 1.5 Research and application scope

- Existing agricultural workflows, datasets and solutions, including opportunities for reuse.
- Data quality, coverage and limitations, with exploratory data analysis (EDA) where useful.
- Evidence-backed substance reactions and interactions, their causes, conditions and impacts. Nitrate–chloride interactions are a research question, not an assumed harmful direct reaction.
- Plant identities, properties and cultivation requirements.
- Fertiliser and plant recommendations supported by evidence and the selected objective.
- Three-cycle crop plans, product recommendations and compatible use of existing fertiliser stock.
- Farming methods, cultivation systems, soil types and hydroponics, with method-specific requirements.

### 1.6 Web application vision

T1's primary endpoint is human health, including evidence about cancer and harmful changes to human cells where relevant. Crop damage and changes in produce properties are separate findings that may inform this assessment; they are not substitutes for evidence of human harm. Investigate direct application, irrigation water, environmental exposure, substance interactions and transformation products where evidence supports them.

T1's Product Substitution task compares current fertilisers, pesticides and other farming inputs with replacement products for the same crop and purpose, considering documented human-health risks, effectiveness, nutritional effects, cost and short- and long-term trade-offs. Its Food Assessment task explains potential human-health effects of known growing inputs. T2 uses applicable T1 comparisons to inform product and crop choices; an alternative must not be labelled safer solely because evidence about it is missing.

The web application has two tabs backed by two pipelines: T1, Food Assessment and Product Substitution (FLORA Vitality); and T2, Crop Rotation Planning (FLORA Cultivate). Food Assessment serves the general public; Product Substitution findings also inform farmers' choices in T2.

| Task | User inputs | Intended output |
|---|---|---|
| T1: Food Assessment | Fruit or vegetable type, growing location, season, known agricultural inputs and conditions | Evidence-supported potential human-health effects, with sources and uncertainty |
| T1: Product Substitution | Current fertilisers, pesticides and other farming inputs, with crop and usage details where known | Replacement product comparisons covering documented human-health risks, farming effectiveness, nutrition, costs, time horizon and trade-offs where data permit |
| T2: Crop Rotation Planning | Desired crops, last three crops planted, land area, geographical region, temperature, current and upcoming seasons, available fertilisers and selected cost optimisation method | A crop rotation or method-appropriate crop sequencing plan for the next three growing cycles, with fertiliser recommendations, inventory reuse, additional purchases and applicable T1 findings |

Detailed inputs, processing and outputs are defined in the pipeline specifications. Document section numbers organise the subject matter; delivery order and priorities are tracked in [workflow and TODO](TODO.md).

## 2 Current State of Agriculture

This section defines the farming-method research coverage. The subset needed for each supported pipeline scenario depends on its crop, region and farming purpose.

### 2.1 Current agricultural operations

#### 2.1.1 End-to-end lifecycle

- Market demand, production planning and crop selection.
- Site preparation, seeds, germination and transplantation.
- Irrigation, fertilisation, pest and disease management.
- Monitoring, intervention, harvesting and quality testing.
- Storage, packaging, transportation and distribution.
- Cleaning, maintenance, waste management and preparation for the next crop.

#### 2.1.2 Current decision-making

- How farmers select crops, fertilisers, pesticides and planting schedules.
- How crop rotation and crop sequencing are currently planned.
- How farmers manage inventory, budgets, labour, water and energy.
- How decisions differ by farm size, region, climate and production method.

### 2.2 Farming methods

#### 2.2.1 Soil-based agriculture

- Conventional, organic, regenerative and raised-bed farming.
- Soil types: sandy, clay, silt, loam and other relevant classifications.
- Soil fertility, pH, drainage, salinity, nutrient retention and crop rotation.

#### 2.2.2 Hydroponics

- Nutrient film technique (NFT), deep water culture (DWC), drip, Kratky and ebb-and-flow systems.
- Open versus recirculating nutrient systems; substrates and root-zone conditions.
- Nutrient monitoring, pH, electrical conductivity (EC), oxygenation and water quality.
- Crop changeovers, sanitation, nutrient carryover and equipment compatibility.

#### 2.2.3 Other cultivation systems

- Aeroponics and aquaponics.
- Greenhouses, indoor and vertical farming, controlled environment agriculture (CEA).
- Precision agriculture and automation as approaches that can overlap with cultivation methods.

#### 2.2.4 Comparison framework

- Suitable crops, climate, land and infrastructure requirements.
- Capital and operating costs, labour, water, electricity and nutrients.
- Yield per area and time, quality, environmental impacts and failure risks.
- Existing technology, commercial adoption, data availability and limitations.

### 2.3 Evidence of current practice

- Prioritise 2020–2026 evidence for the current-state baseline; update as research progresses.
- Retain older foundational literature and the longest useful historical datasets.
- Examine actual commercial farm case studies, government and university guidance, industry surveys and scientific publications.
- Distinguish commercially established practices from pilot projects and emerging research.

### 2.4 Deliverables

- As-Is agricultural workflow maps and farming-method comparison.
- Evidence-backed description of current technologies, economics and operational problems.
- Prioritised research questions and initial scope decisions.

## 3 Existing Solutions and Gap Analysis

### 3.1 Existing workstreams

#### 3.1.1 Software and scientific models

- Farm management software, crop scheduling, nutrient dosing and environmental control.
- Crop growth simulation, chemical equilibrium, food composition and risk assessment.
- Optimisation algorithms, AI, sensor systems and decision-support tools.
- Open-source repositories, APIs and commercial solutions.

#### 3.1.2 Evaluation

- Compare features, scientific validation, adoption, costs, licences and Python integration.
- Identify what can be reused, integrated, improved or must be developed.
- Investigate whether three-cycle planning, inventory reuse and integrated quality assessment already exist.

### 3.2 Candidate resources (to verify)

- AquaCrop / AquaCrop-OSPy, PCSE / WOFOST, DSSAT and APSIM.
- Crop Ontology, USDA FoodData Central, PubChem and PHREEQC.
- NASA POWER, SoilGrids, FAOSTAT and Codex Alimentarius.
- OR-Tools and other mathematical optimisation libraries.

### 3.3 Deliverables

- Solution registry, feature comparison and evidence-backed gap analysis.
- Reuse-versus-build decisions and feasibility assessment.

## 4 Data Gathering and Research Inventory

Data collection begins with current-state research and continues throughout the project.

### 4.1 Data domains

- Plant taxonomy, cultivars, growth, nutrition and historical yield.
- Chemical properties, interactions, fertilisers, pesticides and residues.
- Climate, geography, soil, water, hydroponic conditions and farming methods.
- Crop sequencing, disease, genetics, food composition and natural radioactivity.
- Economics, market demand, resources, regulations and food safety standards.

### 4.2 Research registries

| Registry | Contents |
|---|---|
| Research | Papers, guidance and supporting documentation |
| Dataset | Datasets, APIs, historical records and coverage |
| Solution | Software, algorithms, repositories and models |
| Gap | Unresolved problems, evidence and potential improvements |

### 4.3 Source metadata

- Source URL, publisher, publication date, retrieval date and licence.
- Geographic and temporal coverage, units, granularity and update frequency.
- Methodology, reliability, uncertainty, limitations and applicable crops or conditions.
- Access method, file format and integration feasibility.

## 5 Data Processing and EDA

### 5.1 Data engineering

- Collect and preserve raw data; standardise processed data separately.
- Harmonise units, crop identifiers, chemical identifiers, dates and geographical references.
- Validate schemas, duplicates, missing values and conflicting sources.

### 5.2 Exploratory data analysis (where needed)

- Distributions, outliers, missingness, correlations and coverage.
- Compare species, cultivars, regions, seasons and farming methods.
- Identify bias, confounding variables and insufficient sample sizes.
- Do not interpret correlation as causation.

### 5.3 Deliverables

- Reproducible Python ingestion and cleaning pipelines, data dictionary and EDA findings.

## 6 Scientific Knowledge Base (FLORA Core)

### 6.1 Chemical and substance interactions

#### 6.1.1 Interaction types

- Direct reactions, precipitation, solubility, stability and pH effects.
- Nutrient antagonism and synergy, salinity, toxicity and biological interactions.
- Chemical–chemical, chemical–plant, chemical–soil, chemical–water and environmental interactions.
- Fertiliser–fertiliser, fertiliser–pesticide and pesticide–plant compatibility.
- Potential dietary exposure and human health implications.

#### 6.1.2 Interaction records

- Substance identities, interaction mechanism, concentration range and conditions.
- Affected species, cultivar, growth stage and cultivation method.
- Cause, observed impact, severity, uncertainty and supporting references.
- Example research question: under what conditions does chloride affect nitrate uptake? Do not assume that mixing the ions causes a harmful direct reaction.

### 6.2 Plant properties

#### 6.2.1 Identification and growth

- Species, family, cultivar, seed characteristics, root structure and plant size.
- Germination, maturity, harvest duration, yield and crop history compatibility.

#### 6.2.2 Cultivation requirements

- Temperature, humidity, light, water, macro- and micronutrients.
- Soil, substrate, pH, EC and suitable hydroponic systems.
- Salinity tolerance, disease susceptibility and environmental stress.

#### 6.2.3 Produce properties

- Nutrition, mineral composition, weight, maturity and natural radioactivity.
- Genetics, selective breeding, bioengineering and cultivar-specific differences.
- Quality, shelf life, production cost and market value.

### 6.3 Fertilisers and pesticides

- Product identity, active ingredients, composition, nutrient concentration and cost.
- Crop suitability, documented application constraints, compatibility and persistence.
- Residues, regulatory limits, authorised uses and pre-harvest intervals.
- Distinguish product inventory from previously used nutrient solutions.

### 6.4 Environmental and farming knowledge

- Climate, soil, water, equipment, growing methods, resource use and costs.
- Crop disease, pathogens, sanitation and crop changeover requirements.

## 7 Computational Engines

### 7.1 Scientific calculations

- Crop and environmental suitability, nutrient requirements and compatibility checks.
- Nutrient balance and carryover modelling where measurements support it.
- Crop growth, yield, resource consumption and cost estimation.
- Produce composition and exposure assessment using validated methods.

### 7.2 Optimisation framework

- Hard constraints: crop suitability, capacity, budget where specified, agronomic requirements and safety.
- Soft objectives: cost, yield, profit, quality, inventory reuse, sustainability and risk.
- Compare multi-objective or multi-phase optimisation approaches.
- Report infeasible scenarios and explain trade-offs.

## 8 T1: Food Assessment and Product Substitution (FLORA Vitality)

### 8.1 Inputs

For the initial public-facing tab, start with fruit or vegetable type and collect growing location and other details where known. Allow users to mark information as unknown; explain how missing information limits the assessment rather than inventing inputs or treating the food as safe or unsafe. The following fields describe the fuller assessment when information is available.

- Fruit or vegetable type, species, cultivar, size, weight and maturity.
- Country, region, farm and cultivation method.
- Fertiliser and pesticide identity, composition, amount, frequency and application dates.
- Soil, water, climate, pollution and biological or genetic factors.
- Harvest dates, storage, transport and laboratory results when available.

### 8.2 Assessment domains

#### 8.2.1 Natural food properties

- Natural radioactivity, including potassium-40; distinguish total activity from activity per unit mass.
- Compare bananas initially, then other fruits and vegetables across cultivars and origins where data permit.
- Nutritional composition, minerals, vitamins and physical quality.

#### 8.2.2 Agricultural and environmental impacts

- Fertiliser effects, nutrient accumulation and chemical interactions.
- Potential impacts of excessive fertiliser or pesticide usage, assessed using application amounts, timing and relevant measurements or validated models.
- Pesticide residues, potential exposure and regulatory comparison.
- Heavy metals, environmental contaminants, pathogens and biological hazards.
- Genetics, breeding, bioengineering, maturity and post-harvest effects.

### 8.3 Processing and outputs

- Compare current products or practices with alternatives for the same crop and farming purpose. State the human-health endpoint, exposure assumptions, effectiveness, nutritional effects, costs, time horizon and evidence gaps where applicable.
- Distinguish chemical hazard, measured or estimated exposure, and supported risk conclusions. Treat cancer and mutation hypotheses as questions requiring evidence, not established outcomes or prevention claims.
- Record supported comparisons in a form T2 can use, including applicable crops, conditions, constraints, trade-offs, evidence and uncertainty.
- Retrieve baseline produce properties and relevant scientific evidence.
- Evaluate documented cultivation conditions and agricultural inputs.
- Estimate impacts only where validated models and sufficient inputs exist.
- Report measured values, estimates, potential impacts and unknowns separately.
- Compare applicable regulatory limits with suitable measurements or qualified estimates.
- Return quality and safety findings, uncertainties and recommendations for further testing.

Knowing a fertiliser, pesticide or country of origin alone does not establish actual residue levels or food safety. This system is not a replacement for laboratory testing.

## 9 T2: Crop Rotation Planning (FLORA Cultivate)

### 9.1 Inputs

- Last three crops and planting dates; desired or excluded crops.
- Land area or growing capacity, country, region and farming method.
- Current temperature, current and future seasons, climate and environmental controls.
- Soil or substrate conditions, water quality and hydroponic system details.
- Existing fertiliser inventory, nutrient solution measurements, budget and equipment.
- Labour, electricity, water, market demand and selected optimisation objective.

### 9.2 Processing

1. Filter suitable crops for the specified growing conditions.
2. Evaluate crop history and method-specific constraints.
3. Generate feasible sequences for the next three growing cycles.
4. Estimate nutrient requirements and select compatible fertilisers.
5. Compare inventory use, purchases, operational costs and expected outcomes.
6. Rank plans and explain assumptions, trade-offs and uncertainties.

### 9.3 Fertiliser reuse

- Inventory reuse: share unused stock across cycles to reduce purchasing costs.
- Formulation reuse: select crops with compatible nutrient requirements.
- Solution reuse: assess residual nutrient composition, contamination and sanitation before considering reuse. EC alone is insufficient to establish individual nutrient concentrations.

### 9.4 Farming-method distinctions

- Initial crop sequencing implementation: hydroponics, including equipment compatibility, solution management and sanitation.
- Potential soil-based extension: soil fertility, nutrient depletion, soil-borne disease and conventional rotation rules.

### 9.5 Outputs

- Three-cycle plan with crops, planting and harvest schedules and estimated duration.
- Recommended fertiliser types, inventory utilisation and additional purchases.
- Estimated cost, yield, profit, resource consumption and savings against a defined baseline.
- Alternative cost-effective, maximum-yield, maximum-profit, quality, sustainability, resource-reuse, minimum-risk and balanced plans where supported by data.
- Constraints, warnings, evidence and missing information.

## 10 Integration and Validation

### 10.1 Workflow integration

- Crop Rotation Planning generates candidate cultivation scenarios.
- Food Assessment evaluates potential human-health implications, and Product Substitution compares replacement inputs.
- Use T1's supported human-health comparisons to influence T2's product and crop selection, alongside agronomic requirements and the farmer's objective. Preserve the conditions and uncertainties attached to those findings.
- Keep independent assessments available for already harvested produce.

### 10.2 Validation

- Compare predictions with published studies, actual farm records and measured results.
- Benchmark against current farming practices and existing software.
- Validate units, constraints, uncertainty, geographic applicability and edge cases.
- Avoid unsupported claims of optimality, savings or safety.

## 11 Python Application

Deliver a web application backed by Python, where users submit farm or produce details and view the results of the two workflows.

### 11.1 Application features

- Tab 1 (initial priority): compare farming choices for lower documented human-health risks with acceptable effectiveness, nutrition, cost and long-term trade-offs; retain public-facing produce assessment, source traceability and uncertainty reporting. Do not infer a safety verdict solely from chemical use, origin or bioengineering status.
- Tab 2 (later stage): farmer-facing input interface, three-cycle planning and alternative plan comparison.
- Visualisations, cost breakdowns and exportable results.

### 11.2 Candidate technology stack

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

### 11.3 Implementation approach

- Terminal-first Python implementation: `T1_Pipeline/` and `T2_Pipeline/` each accept Excel inputs stored under `data/` and produce reviewable results before the web app is built.
- Use `code_template/` for shared reusable functions, `research/` for evidence and exploratory work, `test_cases/` for input examples and expected results, and `docs/` for detailed project documentation.
- Keep task-specific logic in its respective pipeline. Reserve `app/` for future implementation until both pipelines work; it currently contains only its purpose README. The root README documents the agreed folder structure.
- Create modules only when needed; avoid duplicate implementations.
- Introduce machine learning only when data and a defined prediction task justify it.
