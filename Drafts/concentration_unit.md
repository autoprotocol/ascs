#### **Title**
Add `concentration` Unit to `Units` Definitions

#### **Authorship**
Alex Hadik alex@transcriptic.com

#### **Motivation**
We should formalize how we represent concentration so that we have a standard way of defining solution concentrations.

#### **Proposal**
Add an arbitrary `item` "unit" to the `units` definition list. This is used as a catch all for discrete items such as cells, beads, etc.

Add three types of concentration units to the `units` definition list: mass, molarity and arbitrary item. These concentration types will be defined as follows:

- MassConcentration: `milligram/milliliter`, `nanogram/microliter`
- MolarConcentration: `mole/liter`, `millimole/liter`, `micromole/liter`
- ItemConcentration: `item/liter`, `item/milliliter`, `item/microliter`

These units are validated by validating the numerator and denominator units. The numerator must be any valid unit from the following set: (`Mass`, `Matter`, `Volume`, `Item`) The denominator must be a recognized unit from the `Volume` category.

Given this validation approach, it should be noted that the proper format is `singular/singular` as in `milligram/milliliter` - NOT `milligrams/milliliter`.

Put together, the format is `Float:Concentration`.

#### **Compatibility**
Since this is an addition, not a modification, there's no anticipated backwards compatibility issues. The only anticipated concerns are that some undocumented approaches to concentration exist in codebases already. These would ideally need to be refactored to be in alignment with these updates.
