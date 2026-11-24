# FLORA Vitality — Food Assessment and Product Substitution

This specification covers **Tab 1 of Project FLORA**, the initial project priority. It is intended for the general public: people enter what fruit or vegetable they have, where it was grown and any known agricultural inputs to understand potential concerns about its composition, cultivation and handling.

This README describes the planned research and application behaviour. It does not represent completed research, a working application or validated assessment results. See the [overall project plan](PROJECT_FLORA.md) and the later [Plant Planning workstream](T2_PLANT_PLANNING.md).

## 1 Purpose and intended experience

The main application asks: **Can we achieve the same farming outcome with lower documented risks to human health and acceptable trade-offs?**

Compare the current product or practice with alternatives for a particular crop and purpose. Explain why each option is used and compare farming effectiveness, nutritional effects, costs and short- and long-term human-health evidence where data permit. The public food-assessment experience remains part of this tab: what can the available evidence tell someone about their produce, and what remains unknown?

Here, “harm” primarily means harm to human health. Cancer and harmful changes to human cells are research endpoints to investigate, not assumed consequences of chemical use. Plant damage or altered fruit properties alone do not establish harm to people. Research may cover direct application, irrigation water, environmental exposure, mixtures and transformation products, subject to available evidence.

The tab should explain concerns involving fertilisers, pesticides, chemical interactions, environmental contamination, bioengineering and other relevant factors in plain language. It should distinguish a substance's potential to cause harm from evidence of exposure in the specific food being assessed.

A user starts with a fruit or vegetable type, adds details they know and receives a sourced explanation. Someone who only knows the produce type should still be able to explore general information, with the limited specificity clearly stated. More detailed records or measurements can support a more specific assessment.

## 2 Planned inputs

| Input group | Examples | Intended use |
|---|---|---|
| Produce identity | Fruit or vegetable type; species and cultivar when known | Match relevant plant properties and evidence |
| Origin | Country, region or farm | Select geographically relevant information without assuming origin determines safety |
| Agricultural products | Fertiliser and pesticide names, formulations or known ingredients | Match product records and documented effects |
| Application history | Amount, concentration, frequency, method and dates | Establish whether application-specific assessment is possible |
| Growing conditions | Soil, water, cultivation method and environmental conditions | Identify relevant context and possible exposure pathways |
| Genetics and bioengineering | Known cultivar, trait or modification and supporting information | Retrieve evidence about the specific trait or product |
| Produce and handling details | Size, weight, maturity, harvest date, storage and transport | Support applicable composition and handling assessments |
| Measurements | Laboratory results, sample date, units and test method | Support sample-specific findings where appropriate |

Only produce type is the starting input. Other fields should allow an explicit unknown value. The app must distinguish user-reported information from independently verified records and measurements.

## 3 Assessment scope

### 3.1 Chemical use and interactions

- Research fertiliser and pesticide ingredients, application conditions, persistence and documented effects on produce.
- Investigate excessive usage using available amounts, timing, conditions and evidence; do not infer excess solely from a product name.
- Record direct chemical reactions separately from nutrient interactions, uptake effects, environmental processes and possible dietary exposure.
- Investigate questions such as nitrate–chloride interactions with their relevant conditions and supporting sources, rather than presuming a harmful reaction.
- Explain whether a finding concerns crop health, produce composition, consumer exposure or a combination of these.

### 3.2 Bioengineering and plant properties

- Cover genetics, selective breeding and bioengineering where relevant evidence exists.
- Assess the identified cultivar, trait or product rather than treating bioengineering status as a safety verdict.
- Include nutritional and mineral composition, maturity and physical quality where supported.
- Preserve the original research interest in natural radioactivity in bananas, including variation by cultivar, origin and sample characteristics. Distinguish total activity from activity per unit mass.

### 3.3 Environmental and handling factors

- Investigate documented contaminants, heavy metals, pathogens and other biological hazards where the data support assessment.
- Consider soil, irrigation water, growing method, harvest timing, storage and transport when relevant information is available.
- Keep regional monitoring findings separate from results for a particular item or batch.

## 4 Data and knowledge base

Use the shared FLORA Core concepts rather than building an independent, incompatible catalogue for this tab.

| Record type | Planned contents |
|---|---|
| Plant | Common and scientific names, cultivar, properties and applicable evidence |
| Agricultural product | Name, manufacturer, formulation, market, ingredients, declared concentrations and source documents |
| Substance | Identifier, names, units and evidence-backed properties |
| Interaction | Substances, mechanism, conditions, affected crops, observed impact and uncertainty |
| Application | Product, amount, timing, method, growing context and provenance |
| Measurement | Sample identity, analyte, result, unit, date, method and reporting limits where available |
| Assessment reference | Applicable jurisdiction, crop, substance, criteria, effective date and source |
| Evidence | Source URL, publisher, dates, licence, methodology, coverage and limitations |

Keep product formulations distinct when their composition or market differs. Undisclosed ingredients and unavailable concentrations remain unknown. Do not infer a complete chemical composition from a product's name or a partial label.

## 5 Planned assessment workflow

### 5.1 Terminal-first delivery

Implement this task as Python code in `T1_Pipeline/`, using an Excel input template under `data/`. Start with a terminal entry point that validates the spreadsheet, runs the supported assessment and comparison steps, and writes results. Define the Excel columns and command when the first supported assessment scope is confirmed.

Reuse suitable functions from `code_template/`; keep T1-specific scientific logic in `T1_Pipeline/`. Place representative inputs and expected results in `test_cases/`. The `app/` folder is reserved for future implementation until both T1 and T2 pipelines work; it currently contains only its purpose README.

### 5.2 Assessment steps

1. Validate the inputs, identities and units; identify missing or ambiguous information.
2. Match the produce and named products to supported database records.
3. Retrieve evidence applicable to the crop, location, ingredients and reported conditions.
4. Determine whether the result can be general information, a contextual assessment, a validated estimate or a measurement-based comparison.
5. Perform calculations only when the required inputs and a suitable validated method exist.
6. Return findings with their sources, applicability, uncertainty and unresolved questions.

Product use alone must not be converted into an invented residue concentration. Regulatory comparisons require an applicable reference and suitable result; dietary exposure calculations additionally require the inputs specified by the chosen method.

## 6 Expected output

- A comparison of current and alternative farming choices for the same crop and purpose, stating documented human-health concerns, effectiveness, nutrition, costs, time horizon and unresolved trade-offs where evidence is available.
- Findings for T2 that retain the relevant crop, product, conditions, exposure assumptions, evidence and uncertainty. Missing evidence must not make an alternative appear safer.
- A readable summary of the submitted information and its provenance.
- Relevant plant and product properties.
- Potential concerns, their mechanisms and the conditions under which they apply.
- Clearly separated measured findings, modelled estimates, research-based interpretations and unknowns.
- Applicable comparisons where the supporting data are sufficient.
- Sources, limitations and the additional records or testing needed to resolve important uncertainties.

Do not present an unsupported numerical “unsafe score” or a definitive safe/unsafe label. Missing information is not evidence of safety or harm. The application supports understanding and assessment; it does not replace laboratory testing of a particular item or batch.

## 7 Implementation constraints

The Python application and storage tools in the overall plan remain candidates until research establishes their suitability. Machine learning is optional and requires a defined task and adequate data.

## 8 Initial release criteria

- Supported produce and assessment questions are explicitly documented.
- Every substantive finding is traceable to a source or a documented calculation.
- Unknown products, ambiguous identities and insufficient inputs produce clear limitations.
- Units, sample context, geographic applicability and evidence dates are checked.
- General evidence cannot be mistaken for a measurement of the user's food.
- The interface remains usable by people without agricultural or chemistry expertise.
