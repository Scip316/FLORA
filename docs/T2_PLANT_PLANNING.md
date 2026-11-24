# FLORA Cultivate — Crop Rotation Planning

This specification covers **Tab 2 of Project FLORA**, intended for farmers and growers. Users describe their farm, crop history, desired crops and available resources to receive a plan for the next three growing cycles, including suitable fertilisers and a comparison of feasible approaches.

This workstream is planned for a later stage. [Food Assessment](T1_FOOD_ASSESSMENT.md) is the initial priority. This README describes intended behaviour, not a working optimiser or validated agronomic recommendations. See the [overall project plan](PROJECT_FLORA.md) for shared scope and research phases.

## 1 Purpose and intended experience

The central question is: **What should I grow over the next three cycles, and how can I meet the crops' needs using suitable resources at an acceptable cost?**

A farmer enters farm conditions, the last three crops, desired or excluded crops and available fertiliser stock. The application checks feasibility, generates candidate sequences and compares them against the selected objective. It explains purchases, resource use, costs and trade-offs rather than claiming one plan is universally optimal.

The existing project direction prioritises hydroponic crop sequencing when this workstream begins. Soil-based crop rotation remains a potential extension requiring its own fertility, disease and rotation rules.

## 2 Planned inputs

| Input group | Examples | Intended use |
|---|---|---|
| Crop history | Last three crops, planting dates, harvest dates and known problems | Evaluate relevant sequencing constraints |
| Crop preferences | Desired crops, excluded crops and production goals | Restrict candidate plans to the farmer's needs |
| Farm capacity | Land area, growing spaces, equipment and system capacity | Limit production to available capacity |
| Location and climate | Country, region, temperature, current and upcoming seasons | Evaluate crop and schedule suitability |
| Cultivation method | Hydroponic system, substrate, soil or environmental controls | Apply method-specific requirements |
| Soil and water | Soil or substrate analysis, water quality, pH and nutrient measurements | Support nutrient and suitability calculations |
| Product inventory | Fertiliser identity, formulation, quantity, price and usable condition | Calculate stock use and additional purchases |
| Existing nutrient solution | Volume, measured composition and contamination or sanitation information | Assess whether solution reuse can be considered |
| Economics and operations | Budget, labour, electricity, water, equipment and market assumptions | Estimate operating costs and supported financial outcomes |
| Optimisation preference | Cost, yield, profit, reuse, quality, sustainability, risk or a balanced objective | Rank feasible alternatives |

The initial farm inputs are the last three crops, area or capacity, geographical region, temperature and seasons. Additional calculations require their relevant inputs. Missing required data must be reported rather than silently replaced with invented values.

## 3 Planning and optimisation behaviour

### 3.1 Terminal-first delivery

Implement this task as Python code in `T2_Pipeline/`, using an Excel input template under `data/`. Start with a terminal entry point that validates farm inputs, uses applicable T1 findings, generates supported three-cycle plans and writes results. Define the Excel columns and command when the first supported planning scope is confirmed.

Reuse suitable functions from `code_template/`; keep T2-specific planning logic in `T2_Pipeline/`. Place representative inputs and expected results in `test_cases/`. Build the web interface only after both terminal pipelines work.

### 3.2 Feasibility before ranking

Candidate plans must satisfy applicable crop, climate, equipment, capacity and agronomic constraints. Respect a budget as a hard constraint when the farmer specifies it that way. Cost savings must not override required compatibility or safety conditions.

If no plan satisfies the constraints, return the conflicting requirements and explain which inputs or restrictions need reconsideration. Do not silently remove a requested crop or relax a constraint.

### 3.3 Objectives and alternatives

- **Cost:** Compare purchases and supported operating costs across three cycles.
- **Inventory reuse:** Prefer compatible use of existing stock where this meets crop requirements.
- **Yield or profit:** Compare supported production estimates and explicit market and cost assumptions.
- **Quality, sustainability or resource use:** Use defined metrics when the data support them.
- **Risk or balanced planning:** Explain the criteria, weights and trade-offs used to rank alternatives.

These are candidate objectives, not promises that every mode will be available initially. Describe a result as optimal only within its documented model, constraints, data and solver result.

## 4 Fertiliser selection and reuse

The application should identify products that meet crop requirements and evaluate how they can be used across the planned sequence.

| Reuse type | Meaning | Required distinction |
|---|---|---|
| Inventory reuse | Use remaining unused product across crops or cycles | Track product quantity and nutrient content without double-counting stock |
| Formulation reuse | Choose crops that can use compatible products or formulations | Check each crop's requirements rather than assuming an identical feeding programme |
| Nutrient solution reuse | Consider a previously used solution for a later crop | Require relevant composition, contamination and sanitation evidence |

Do not treat unused fertiliser stock and used nutrient solution as interchangeable resources. Electrical conductivity alone must not be used to invent individual nutrient concentrations. Account for losses, replenishment and carryover only where measurements and an appropriate model support them.

## 5 Farming-method distinctions

For hydroponics, research system compatibility, root-zone conditions, nutrient management, water quality, sanitation and changeover requirements. Generate sequences using those constraints rather than automatically importing soil rotation rules.

For a later soil-based extension, research soil fertility, nutrient depletion and carryover, soil-borne disease, crop families and local rotation guidance. Document how those rules differ from hydroponic sequencing before enabling them.

Research may compare conventional and organic practices, soil types, greenhouse production, vertical farming, aquaponics and aeroponics. Support in the optimiser depends on validated method-specific data and rules; researching a method does not mean the application already supports it.

## 6 Data and shared knowledge

Reuse the shared FLORA Core plant, product, substance, interaction and evidence records also needed by Food Assessment. Keep farm inventory and planning scenarios separate from reference knowledge.

Planned planning-specific records include:

- Crop requirements by cultivar, growth stage, method and environmental conditions.
- Growth duration, harvest windows, yield evidence and sequencing constraints.
- Site capacity, equipment, water, substrate or soil conditions and crop history.
- Inventory quantities, product composition, prices, currency and price dates.
- Resource consumption, labour requirements and operational cost assumptions.
- Candidate plans, constraint evaluations, objective values and calculation provenance.

All reference records need source metadata, units, coverage and limitations. A shared interaction record must state whether it concerns direct mixing, nutrient availability, plant uptake, environmental effects or consumer exposure.

## 7 Planned workflow

1. Validate farm inputs, product identities, quantities and units.
2. Identify crops suitable for the environment, method and farmer's preferences.
3. Apply crop-history, timing, equipment and changeover constraints.
4. Generate feasible sequences for the next three growing cycles.
5. Estimate nutrient needs using suitable crop and method data.
6. Allocate compatible inventory and calculate additional purchases without exceeding available stock.
7. Estimate costs and other supported outcomes using explicit assumptions.
8. Rank alternatives against the selected objective and explain trade-offs and uncertainty.

## 8 Expected output

- A three-cycle schedule with crop choices, planting and harvest windows and estimated durations.
- Fertiliser recommendations and the basis for their selection.
- Stock consumed, stock remaining and required additional purchases.
- Cost breakdowns and supported estimates of yield, profit and resource use.
- Savings only against an explicitly defined, comparable baseline.
- Alternative feasible plans, constraints, assumptions and evidence.
- Clear infeasibility or missing-data explanations when a plan cannot be supported.

For example, a farmer may want to grow a desired crop while using fertiliser left from an earlier cycle. The system should compare whether that stock can meet the proposed crops' requirements, what supplementation would be needed and how the total cost compares with a defined alternative. This is intended behaviour, not a claim that reuse always saves money.

## 9 Relationship to Food Assessment

Plant Planning uses supported comparisons from FLORA Vitality to influence crop, fertiliser and other farming choices. T1 evaluates whether alternatives can achieve the same farming outcome with lower documented risks to human health and acceptable trade-offs. T2 applies those findings only to the crops, conditions and uses they support, alongside agronomic constraints, availability, costs and the farmer's objective.

Retain T1's evidence and uncertainty in the plan explanation. Missing human-health evidence must remain unknown and must not be rewarded as a safer choice. Planned product use must remain distinct from measured residues or consumer exposure. Public food assessment must also remain usable independently of this planning tab.

## 10 Implementation constraints

The optimisation and application libraries listed in the overall plan remain candidates. Select tools based on the validated problem and integration needs; machine learning is not a prerequisite.

## 11 Initial release criteria

- Each recommended crop and sequence is supported for the declared method and conditions.
- Inventory quantities, nutrient units, area and time calculations remain consistent.
- Plans satisfy all declared hard constraints or explicitly report infeasibility.
- Cost comparisons use a stated baseline, currency, dates and assumptions.
- Unmeasured nutrient carryover and unsupported reuse are not invented.
- Users can understand why a plan was selected and where uncertainty affects it.
