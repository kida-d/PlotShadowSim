# Maiersdorf Plot Sunlight Simulation

> **Confidence summary:** You can trust the **sun geometry** and **plot orientation**: both were calculated exactly and tested. You **cannot yet trust the absolute sun-hour figures**, because they depend on tree, building, and horizon inputs that are still estimates.
>
> Treat the current numbers as a **comparison** (with vs. without the trees, one part of the garden vs. another), **not as a forecast**.

## Practical Note: 3D View

The latest file did not load on your network because the **3D library is blocked there**. The figures below come from the **same calculation code**, which was tested separately from the 3D view.

---

## Why You Can Trust the Geometry

| Part | How it was checked | Accuracy |
|---|---|---|
| **Sun position** | Standard NOAA solar formula. Matches reference values for Maiersdorf: **65.6° at noon on 21 Jun**, **18.8° on 21 Dec**, and sunrise/sunset to the minute. | **±0.5°, ±1 min** |
| **Clock and summer/winter time** | Uses the EU switch dates and the plot's longitude. The approximately **±15-minute variation of real solar time** over the year is included. | **±1 min** |
| **Plot orientation** | Calculated from your GPS points. The street front comes out at **29.96 m**, and your centre point is within **1 m** of the calculated centre, so the points are consistent. Rotation is **27.9°**; the tree border faces **ESE (118°)**. | **±1–2°**, limited by GPS-on-map precision |
| **Shadow geometry** | Exact ray-tracing against the tree and building shapes. Tests behaved correctly: no trees gives **0 h lost**, taller trees give more shade, and rotating the plot moves shadows in the correct direction. | **Exact for the shapes entered** |
| **Sun-hour totals** | Calculated using **10-minute time steps** on a **1 m grid** over the garden. | **±0.1 h** |

---

## Limitations and Their Effect on the Result

| Limitation | Effect | Direction |
|---|---|---|
| **Tree height, width, and spacing are guesses** | The biggest uncertainty. Shadow length is proportional to height. | **Either way** |
| **Hohe Wand horizon not loaded yet** | Evening sun is counted that the ridge actually blocks. | **Too much sun**, especially evenings |
| **Crowns are solid** | Real crowns let roughly **10–30% of light through when in leaf**, and much more when bare. Birches are especially open. | **Too much shade**, mainly for deciduous trees and in winter |
| **Uniform tree row** | Your photo shows a mixed row, not evenly spaced identical trees. | **Either way**, depending on where the gaps are |
| **Only the ESE trees and one neighbouring building are modelled** | The house on the **NNE side** (left in your photo) and any hedges or fences are missing. The NNE house could slightly block summer sunrise. | **Too much sun**, small effect |
| **Tree growth** | The model shows today's geometry. Conifers can add **0.3–0.5 m/year**. **[ASSUMPTION: depends on species.]** | **Too much sun in the future** |
| **Direct sun only, on clear days** | Results represent *possible* sun hours. Clouds reduce the real total significantly, while shaded areas still receive daylight from the open sky. | **Absolute numbers too high; comparisons remain useful** |
| **Flat terrain** | Any slope across the plot is ignored. | **Small effect** |

---

## What the Street View Photo Shows

The photo is taken from the street looking **ESE**, so the trees in the background are the main concern. The red-roofed house on the right is the **SSW neighbour**.

- **Right half of the ESE border:** A dense wall of conifers, **[ASSUMPTION] about 8–12 m** high. They block light all year and are best modelled as solid evergreen.
- **Middle and left:** Birches and other deciduous trees, **[ASSUMPTION] about 10–15 m** high, with gaps between them. They are bare in winter and relatively transparent even in summer.
- **Low hedge along the back fence:** Affects only the first metre or two of the garden.
- **SSW house:** Close to the plot and has a high roof. **[LIKELY] It will matter more in winter than the ESE trees.**
- **Terrain ridge:** The ridge in the background on the left is visible, so loading a terrain horizon is worthwhile.

### Current Tree-Row Model

**[LIKELY]** The current default model, one uniform **15 m evergreen row**, **overstates tree shade on the deciduous section** while roughly representing the conifer section.

A useful way to bracket the real result is to run the simulation twice:

1. **Evergreen scenario:** approximately **10 m** trees.
2. **Deciduous scenario:** approximately **13 m** trees.

The real result should be evaluated against this range rather than treated as a single precise value.

---

## How to Read the Results

### 1. Trust Differences More Than Absolute Numbers

Prefer conclusions such as:

- "The trees cost **2–3 h of morning sun**."
- "The street half gets **3 h more sun** than the tree half."

Avoid overly precise statements such as:

- "The garden gets **13.4 h** of sun."

### 2. Perform a Sensitivity Check

Change the assumed tree height by **±3 m**.

- If your decision stays the same, the uncertainty probably does not matter.
- If the decision changes, measure the trees properly before relying on the result.

### 3. Validate One Real Shadow on Site

In late October, the sun reaches similar elevations to mid-February. Measure one real shadow on site, for example from a fence post, at a recorded time and compare it with the simulation for the same date and time.

If the measured and simulated shadows match, that is a strong practical check of the geometry.

### 4. Think About the Garden in Zones

Most of the expected loss is **morning sun on the ESE half**. The **street half remains sunnier**.

This distinction can guide placement of:

- Patio / terrace
- Vegetable beds
- Children's play area
- Other sun-sensitive garden features

### 5. Plan for the Worst Case

Assume that:

- the trees remain,
- the neighbour does not remove them, and
- the trees continue to grow.

Do not base a purchase decision on vegetation outside your control being removed later.

---

## Bottom Line

**The geometry is solid. The trees, neighbouring buildings, and terrain horizon are what make the absolute sun-hour numbers uncertain.**

Before treating the result as a purchase-decision tool:

- [ ] Measure the important tree heights and approximate crown sizes.
- [ ] Improve the tree-row model to distinguish evergreen and deciduous sections.
- [ ] Add missing neighbouring buildings where relevant.
- [ ] Load the **PVGIS terrain horizon**.
- [ ] Perform at least one **on-site shadow validation** at a known date and time.
- [ ] Repeat the simulation with different plausible tree heights to test sensitivity.

Once those inputs are improved, the simulation should be good enough to support a practical decision about whether the plot's sunlight conditions are acceptable for you.
