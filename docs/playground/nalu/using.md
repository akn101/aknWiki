---
sidebar_position: 2
title: Using Nalu
---

# Using Nalu

A model run takes a location, a date, and a selection of variables.

## Running a model

1. Set the reef location in the location selector.
2. Set the reference date, for example `09/03/2025`.
3. Enter the environmental and biological variables, or upload an existing
   dataset.
4. Tick the variables the run should include.
5. Set **Use New Model** according to the modelling method required.
6. Select **Generate**.

## Location and date

| Input | Detail |
|-------|--------|
| Location | Selects and edits the reef being modelled. Used to give context to the environmental parameters |
| Date | Sets the reference date for the model |

## Environmental variables

| Variable | Meaning |
|----------|---------|
| **Temperature** | Sea surface or water column temperature |
| **Salinity** | Salt concentration of the water |
| **Water Turbidity** | Clarity of the water |
| **Water Current** | Speed and direction of water movement |
| **Sedimentation** | Level of sediment deposition on the reef |

## Biological variables

| Variable | Meaning |
|----------|---------|
| **Coral Disease Species** | The pathogen or disease type being modelled |
| **Drupella Density** | Population density of Drupella, a corallivorous snail that stresses coral |
| **Parrotfish Density** | Density of parrotfish, which graze algae |
| **Butterflyfish Density** | Density of butterflyfish, an indicator of reef health |
| **Total Coral Cover** | Percentage of the reef area covered by coral |
| **Coral Density** | Number of coral colonies per unit area |

## Controls

| Control | Effect |
|---------|--------|
| Variable checkboxes | Select which variables the run includes |
| **Use New Model** | Switches between modelling methods |
| **Generate** | Runs the predictive analysis over the current inputs |

## Output

**Generate** produces a prediction of coral disease spread for the location
and period supplied. The prediction is rendered in the browser.

The output includes a predicted growth rate or spread area, a risk assessment
for the location and period, and a visual or tabular summary.

## Related

- [Overview](overview.md) covers capabilities and intended use.
