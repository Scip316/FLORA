# Project FLORA (Food, Land, Optimisation, Research and Agriculture)

## Research into farming choices

1. Assess the potential effects of food and the chemicals used in its production on human health.
2. Recommend alternative farming products that may reduce documented health risks while maintaining farming effectiveness.
3. Develop a crop rotation planning system with suitable product recommendations.

## How it works

| Task | Input | Purpose | Pipeline |
|---|---|---|---|
| **Food Assessment** | Region, season, fruit type, and known pesticides, fertilisers or other chemicals used | Assess whether the chemicals used may directly or indirectly affect human health, based on available evidence. | T1_Pipeline |
| **Product Substitution** | Current fertilisers, pesticides and other farming inputs, with crop and usage details where known | Compare replacement products that achieve the same farming outcome with lower documented human-health risks and acceptable trade-offs. | T1_Pipeline |
| **Crop Rotation Planning** | Region, season, previous three crops, desired crops for the next three cycles, and optionally available fertiliser stock | Use historical data to recommend a three-cycle crop rotation plan and suitable products, informed by documented health risks. | T2_Pipeline |

Crop Rotation Planning offers two modes: 
1. **cost-efficient**, which aims to use a compatible set of products across all three cycles
2.  **crop-specific optimisation**, which selects products for each crop's requirements.

## Repository structure

```text
code_template/   Shared Python functions
T1_Pipeline/    Food Assessment and Product Substitution
T2_Pipeline/    Crop Rotation Planning
app/            Future web interface
data/           Excel templates, inputs and results
research/       Sources, evidence and exploratory analysis
test_cases/     Example inputs and expected results
docs/           Project plans and documentation
```

## Documentation

- [Project plan](docs/PROJECT_FLORA.md)
- [T1 — Food Assessment and Product Substitution](docs/T1_FOOD_ASSESSMENT.md)
- [T2 — Crop Rotation Planning](docs/T2_PLANT_PLANNING.md)
- [Workflow and TODO](docs/TODO.md)
