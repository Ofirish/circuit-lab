# Circuit Lab – מעבדת מעגלים

Drag-and-drop DC circuit builder (Hebrew/English): resistors, sources, op-amps, capacitors, inductors, meters.
Computes node voltages, currents and power per part (MNA solver), warns on overloaded resistors, saturated op-amps and floating nodes.

Live test build: https://circuit-lab-ofir.surge.sh

- Drop a part on a wire → inserted in series; parts on the same line are auto-spaced so you can branch from the gaps.
- Copy / export: schematic + values table (paste into Word/email), text with step-by-step formulas, SVG, PNG, Print/PDF, JSON save/load.
- ▶ Play: animated current flow (direction + speed by magnitude); faulty parts glow red.
- Faults tab: each problem explained (why it happens) with step-by-step fixes and one-tap fixes with computed values.
- ✨ Tidy: straightens lines, evens spacing, re-routes wires; verifies connectivity is unchanged (otherwise does nothing).
- Table tab: all parts and values, editable, with live results.
- Single self-contained `index.html`, no build step.

## Deploy
```
npx surge . circuit-lab-ofir.surge.sh
```
