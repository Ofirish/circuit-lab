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
- 🧩 Connected to [Control Block Lab](https://control-block-lab-ofir.surge.sh): header button, and Export → "Open as block diagram" for known op-amp templates.
- Single self-contained `index.html`, no build step.

## Run locally
Open `index.html` in a browser.

## Deploy
```
npx --yes surge . circuit-lab-ofir.surge.sh
```
If deploying from a Claude session fails (network blocked), hand the file to Grok Bot / Ofir; never paste Surge secrets into chat.

## Link format shared with Control Block Lab — `ofir-lab-link/v1`
Save/Load JSON uses the shared envelope (the old `circuit-lab/1` files still load):
```json
{ "schema": "ofir-lab-link/v1", "app": "circuit-lab", "kind": "circuit",
  "title": "…", "template": "…", "notes": {"he": "…", "en": "…"},
  "data": { "parts": [...], "wires": [...] }, "createdAt": "ISO date" }
```
- Deep link: `https://circuit-lab-ofir.surge.sh/#link=<base64url(JSON)>`; the hash is cleared after import.
- Unknown top-level fields are preserved on load → save (the user is told how many).
- A `block-diagram` file loaded here offers to open it in Control Block Lab instead.
- Offline: Export → "Download block-diagram link file", then Load JSON in the other app.

Circuit → block templates (analogy only, one op-amp): non-inverting amp (β = R1/(R1+Rf)), voltage follower (β = 1), inverting amp (K = Rf/(Rin+Rf), β = Rin/(Rin+Rf)). Other circuits show a bilingual "no mapping yet" message.
