# FLORA — Workflow and TODO

**Last updated:** 24 November 2026  
**Current stage:** Planning and documentation; research and pipeline implementation have not started.

## 1 Purpose

T1 asks whether the same farming outcome can be achieved with lower documented risks to human health and acceptable trade-offs. T2 uses supported T1 findings alongside farm conditions and costs to select crops and products for three growing cycles.

Develop both as terminal-based Python pipelines with Excel inputs first. Build the two-tab web app after the pipelines work. Detailed requirements live in the [project plan](PROJECT_FLORA.md), [T1 specification](T1_FOOD_ASSESSMENT.md) and [T2 specification](T2_PLANT_PLANNING.md).

## 2 Delivery order

T1 scope and evidence → shared data and Excel inputs → T1 pipeline → T1-to-T2 findings → T2 pipeline → web app.

Research is iterative. Complete the evidence needed for the first supported comparison before implementing its conclusions; broader topics can continue later. Do not wait for answers to every cancer or chemical-interaction question before delivering a narrowly supported assessment.

## 3 Completed setup

- [x] Agree on FLORA's purpose, two workstreams and T1-first priority.
- [x] Establish the repository folders and their purpose descriptions.
- [x] Document terminal-first delivery with Excel inputs and shared functions in `code_template/`.
- [x] Consolidate detailed specifications under `docs/` and provide a concise root README.

## 4 Delivery milestones

### 4.1 Define and research the first T1 comparison — next priority

**Purpose:** Choose a question that available evidence can actually answer.

- [ ] Review existing food-assessment and alternative-comparison tools; record reuse opportunities and gaps.
- [ ] Select an initial crop, region, farming purpose, current practice and candidate alternatives based on evidence availability.
- [ ] Define the human-health endpoints, what counts as an equivalent farming outcome and which trade-offs to compare.
- [ ] Inventory data sources, licences, geographic coverage and validated assessment methods.
- [ ] Compare existing tools for evidence quality, required inputs and gaps; verify candidate resources before adopting them.
- [ ] Record relevant product ingredients, application conditions, water or environmental pathways, interactions and transformation products where supported.
- [ ] Separate evidence of human harm from plant damage, produce changes and hypotheses requiring further research.
- [ ] Record why each current or alternative practice is used, including effectiveness, nutrition, cost and short- and long-term evidence gaps.

**Done when:** A documented comparison has traceable sources, defined applicability and an explicit statement of what can and cannot be concluded. If evidence is insufficient, narrow the question or document the gap before implementing a comparison.

### 4.2 Prepare shared data and the T1 Excel input

**Purpose:** Make research usable through consistent, reproducible records.

- [ ] Define identifiers and fields for plants, products, ingredients, interactions and evidence.
- [ ] Preserve original source data and create documented cleaning and validation steps.
- [ ] Conduct EDA where needed to assess coverage, missing values, units or conflicting observations.
- [ ] Compare species, cultivars, regions and sample sizes where relevant; retain bananas as the starting research interest for natural radioactivity without limiting the entire assessment to bananas.
- [ ] Define T1 Excel sheets, columns, units, required values and how unknown information is represented.
- [ ] Create a small input template under `data/` and representative cases under `test_cases/`.
- [ ] Define the T1 result format, including findings, alternative comparisons, evidence, assumptions and limitations.
- [ ] Record data and assessment-rule versions so results can be traced and reproduced.

**Done when:** A representative input can be mapped to documented evidence records, and missing or invalid information has defined handling. Spreadsheet structure and result format are documented; no invented values hide gaps.

### 4.3 Implement and check the T1 terminal pipeline

**Purpose:** Produce evidence-backed assessments and comparisons from Excel inputs.

- [ ] Define the supported terminal command and Python dependencies.
- [ ] Implement Excel reading, input checks and identity matching.
- [ ] Implement only assessment and comparison logic supported by the selected evidence and methods.
- [ ] Share genuinely reusable functions through `code_template/`; keep T1-specific behaviour in `T1_Pipeline/`.
- [ ] Write results with source references, applicable conditions, uncertainty and clear missing-data explanations.
- [ ] Check representative comparisons, ambiguous products, missing fields and invalid units against expected outcomes.
- [ ] Document a reproducible example run and its limitations.

**Done when:** T1 runs from the terminal on the documented Excel template and returns checked results. Missing evidence is not treated as evidence of lower risk; no unsupported safe/unsafe score or cancer-prevention claim is produced.

### 4.4 Define the T1-to-T2 exchange

**Purpose:** Let planning use T1 findings without losing their conditions or uncertainty.

- [ ] Define the fields T2 consumes: crop, farming purpose, compared choices, applicable conditions, findings, trade-offs, evidence, uncertainty and versions.
- [ ] Define how T2 handles unsupported, outdated, conflicting or unknown findings.
- [ ] Check that a finding cannot be applied to a different crop, purpose or condition without supporting evidence.

**Done when:** A representative T1 finding can inform a T2 choice with its evidence and limits intact. The file or storage format remains to be selected.

### 4.5 Implement and check the T2 terminal pipeline

**Purpose:** Generate feasible three-cycle plans using farm inputs and applicable T1 findings.

- [ ] Confirm the first hydroponic system, crop set, region and optimisation objective.
- [ ] Review existing farm planning workflows, scheduling software and scientific models for reuse.
- [ ] Gather crop requirements, sequencing constraints, product compatibility, inventory and cost evidence.
- [ ] Conduct EDA where needed to check coverage, missingness, units and variability in planning data.
- [ ] Define the T2 Excel template and result format.
- [ ] Implement suitability checks, crop-history constraints and three-cycle sequence generation.
- [ ] Apply relevant T1 findings to product and crop choices while preserving agronomic constraints.
- [ ] Calculate inventory use, required purchases and supported costs without double-counting stock.
- [ ] Compare alternatives against a stated baseline and explain infeasible scenarios.
- [ ] Validate the simplest feasible planning model before expanding optimisation objectives.
- [ ] Check constraints, nutrient and inventory balances, missing data and expected example plans.
- [ ] Document a reproducible terminal run.

**Done when:** T2 returns checked, feasible plans or clear explanations of why no supported plan can be produced. Used nutrient solution is handled separately from unused stock, with reuse considered only where evidence permits.

### 4.6 Build the web app — later

**Purpose:** Make the working pipelines accessible through two tabs.

- [ ] Confirm that both terminal pipelines meet their completion criteria.
- [ ] Choose the interface and hosting tools based on the working pipelines.
- [ ] Build T1 and T2 forms that reuse the pipeline functions and validation.
- [ ] Display results, evidence, uncertainties and downloads in plain language.
- [ ] Check complete user workflows before release.
- [ ] Add appropriate automated checks, dependency configuration, deployment steps and recovery instructions as implementation and hosting are introduced.

**Done when:** Both tabs reproduce the checked pipeline behaviour and have a documented, repeatable release process.

## 5 Decisions still open

- First supported crop, region, farming purpose and comparison endpoints.
- Evidence sources and validated assessment methods suitable for that scope.
- Excel schemas, result formats and the T1-to-T2 exchange format.
- First T2 objective and supported hydroponic scenario.
- Application framework, database and hosting.

Resolve these at the relevant milestone using repository evidence and research. Keep broader soil-based planning, additional farming methods and expanded assessment topics in scope without treating them as prerequisites for the first release.

## 6 Documentation maintenance

Keep progress, next steps and development checklists in this document. Keep READMEs brief and focused on purpose and scope; maintain detailed requirements in the specifications. Update the relevant specification when requirements change, and mark a TODO complete only when its output exists and has been checked as appropriate. Candidate tools and research hypotheses remain provisional until validated.
