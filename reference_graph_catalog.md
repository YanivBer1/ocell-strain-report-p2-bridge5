# Reference graph catalog — Kraitec B R004/2026

Reviewed 3 October 2026. Source: `reference-report.pdf`, 52 PDF pages, with `reference-text.txt`.

The text extracted from all 52 pages was reviewed. PDF pages 26–32 were rendered and visually inspected, as were annex pages 36–41 and 46–51. Page references below are PDF page numbers, not inferred printed numbering. This catalog records the reference's chart structures and limitations; none of its measured values, material properties, soil descriptions, calibration coefficients, or load conventions has been adopted for P2.

## Experiments must remain separate

The reference is Kraitec B, Yokneam, with a 2026 test, a 0.70 m pile and approximately 16.5 m effective length. Pages 5, 20, 25 and 32 explicitly distinguish **400 tf nominal load for each upper/lower element from 800 tf combined load**. Its displacement and strain plots use the nominal per-element load; its equivalent top-down curve reaches the combined 800 tf.

P2 Bridge 5 is the separate 2020 dataset, with 1.2 m diameter, gauge depths 9.7–28.7 m and recorded maximum load 900. P2's raw column is titled only `Load`; the reference's 400+400 convention does not establish how P2's 900 is defined. Do not halve, double or relabel P2 loads using this reference.

## Main experimental charts

| Figure / PDF page | Family and exact orientation | Series and branches | What can be created from P2 |
| --- | --- | --- | --- |
| Figure 10 / p26 | **Displacement versus nominal load.** X: Load, tonF, left to right, displayed 0–440. Y: signed displacement, mm, increasing upward, displayed −3–16. The horizontal load axis crosses displacement zero. | Three physical displacement quantities: upper plate, pile top, lower plate. Each channel contains the chronological loading and unloading branches on the same axes. Upper channels are positive; the lower channel is negative in the reference convention. Color identifies channel, not stage. Figure's visible legend is incomplete; p25 identifies all three quantities. | Only a **reported instrument-channel change** chart can presently be made: P2 AN:AR minus row 19, with original signs, channel labels and both branches. A reference-equivalent physical-displacement chart remains unverified without calibration, installation mapping, directions, reference-beam corrections and analog/digital averaging evidence. Never obtain displacement by renaming or integrating an incomplete strain profile. |
| Figure 11 / p28 | **Upper-element strain versus nominal load.** X: nominal load, tonF, left to right. Y: micro-strain, increasing upward; visible scale approximately 0–260. The source rendering crops/obscures the lower X-axis/legend area. X quantity is supported by p35's strain-by-load table and the matching lower-element plot. | Five upper reference gauge levels, each with loading and unloading together. Color/marker identifies gauge level. Returns at zero nominal load retain residual strain. | Supported for P2 SG1–SG4 from the existing stage-end gauge means. Share a canvas with lower levels or provide upper/lower/all filters. Maintain all repeated-load stages; do not smooth away turning points or residuals. |
| Figure 12 / p28 | **Lower-element strain versus nominal load.** X: Load, tonF, 0–500; Y: micro-strain, 0–240. | One reference lower level, SG6, with loading and unloading in the same series. | Supported for **all three** P2 lower levels SG5–SG7, rather than copying the reference's single-level selection. This is the same chart family as Figure 11, so upper/lower views can be combined. |
| Figure 13 / p29 | **Axial-force versus depth profiles.** Title says “Stress Level by Loading Steps”, but X unit is TonF, so the plotted quantity is force, not stress. X labels are across the top, 0–450. Y: depth, m, 0–17, **increasing downward**. | Colors/markers identify nominal loading stages 40–400 tf. Upper and lower elements share the canvas, separated by a hydraulic-cell band near 12.5–12.8 m. Reference includes pile-head zero, plate-force and toe endpoints from its own tables/model. It does not display unloading profiles in this figure. | Supported at P2's actual gauge depths as estimated **changes in axial force relative to baseline**, using existing E/A/GF assumptions. P2 may include all 19 stages with loading/unloading styles. Do not add reference head/plate/toe boundary points, force the measured curve through (0,0), or join upper and lower measured polylines across the cell. Depth belongs on Y; no 90-degree rotation is needed. |
| Figure 14 / p30 | **Shaft-friction versus depth step profiles.** X: Friction, TonF/m², 0–48, across the top. Y: depth, m, 0–17, increasing downward. | Color identifies loading stage. Constant-per-interval steps extend through the reference's modeled upper and lower intervals; cell shown as a horizontal band. Visible legend omits the 80 tf stage despite p35 containing it. | Supported from P2's existing inter-gauge load-transfer rows. Draw only 9.7–14.2, 14.2–18.0, 18.0–21.2, 24.1–26.2 and 26.2–28.7 m. Leave other intervals blank. Preserve signed values, including negative residual friction. kPa or tf/m² is a unit choice, with 1 tf/m² = 9.80665 kPa. A step is the **segment average displayed over its interval**, not proof that local friction is spatially uniform. |
| Figure 15 / p31 | **Toe bearing pressure versus nominal load**, titled “Realized Bearing Capacity of the Toe”. X: Load, TonF; reference display starts at **75**, not zero, and ends at 450. Y: toe bearing pressure, TonF/m², 0–800, increasing upward. | One loading curve, approximately 80–400 tf. This is not toe load versus displacement and not a strain-depth profile. Its pressure is based on the reference's inferred toe-force values divided by toe area. | **Unavailable as verified P2 toe resistance.** The lowest P2 gauge is not a verified toe load cell. No approved method or measurements establish force loss in the last uninstrumented segment or residual/weight treatment. One can display SG7's already calculated near-toe strain/stress versus load, labeled as that gauge result, but it must not be labeled toe bearing capacity. |
| Figure 16 / p32, supporting table p31 | **Equivalent top-down load versus settlement/displacement.** X: Load, tonF, 0–880. Y: displacement, mm, **zero at top with negative values downward**, 0 to −11. Equivalent load table reaches 800 tf. | One modeled loading curve derived from the two elements' loads/displacements. Table labels it “polynomial interpolation”. It is a constructed top-down model, not directly measured by one instrument. No unloading equivalent branch is shown. | **Unavailable as a verified P2 equivalent curve.** P2 load semantics and physical displacement calibration/corrections are unresolved; the documented interpolation/construction method and domain are not established. Do not import the reference's points, its doubling rule, or P2 Sheet2's unvalidated fit. |

## What should be merged, and what should remain distinct

- Merge loading and unloading **within each response-versus-load family**, joining them at the actual maximum-load reading in chronological order. Initial and final zero-load stages remain different observations.
- Upper and lower strain-versus-load views can use one selectable all-level chart because the quantities and units match.
- Upper and lower **depth profiles** can share one canvas, but measured lines must remain disconnected across the cell/unmeasured region.
- Do not merge displacement (mm), strain (με), axial force (tf), shaft friction (kPa or tf/m²), or toe pressure (tf/m²) into a single unlabeled quantity. A metric selector is acceptable when axes and units change explicitly.
- Reference force/friction axes are at the top. Putting their numeric X labels at the bottom is acceptable if depth still increases downward and all zero ticks remain visible. It does not require swapping X and Y.
- The reference's Fig15 X minimum of 75, cropped Fig11 axes, incomplete legends, and smoothed-looking curves are not presentation defects to reproduce. P2 should retain all source points and visible zero reference lines, extend domains for actual negatives, and use straight segments between measured points.

## Additional charts and supporting evidence in the annexes

| Pages | Family | P2 applicability |
| --- | --- | --- |
| p41 | **Cross-hole sonic integrity profiles**, three panels. Y is depth increasing downward. X includes arrival time in ms and relative energy in dB; waveform/diagnostic traces and classification colors are superimposed. These are a different measurement system from load testing. | No matching P2 sonic records are present in the analyzed dataset. Do not generate sonic diagnostics from strain data or attach the reference's integrity outcome to P2. |
| p46 | **Hydraulic-cell calibration: load versus pressure.** X pressure, bar, increasing right; Y load, ton-f, increasing upward. Separate series identify 25, 60 and 120 mm stroke calibration conditions. | No verified P2 hydraulic-cell serial/certificate and matching pressure/stroke readings are available here. The 2025 ACH-400 certificate belongs to the reference instrument and cannot convert P2 loads. |
| p47–50 | Four **VW crackmeter calibration tables/formulas**, not extra plotted experimental graphs. They include applied displacement, frequency, calculated displacement, error, polynomial A/B/C, thermal coefficient, serial and date. | These specific 2025/2026 coefficients cannot calibrate P2 2020 channels without evidence of instrument identity and applicability. |
| p51 | **VW strain-gauge calibration certificate/table**, model 1240, with application GF3.304. No additional plotted load-test chart. | Corroborates a generic family/application factor, but it is a 2025 certificate for a reference lot, not a P2 sensor-specific certificate. |
| p2, p7–8, p45, p52 | Geological section, soil/geotechnical tables, pile/instrumentation layout and borehole log. These are engineering context diagrams/tables, not extra measured load-response curves. | P2's known geometry can support its own instrumentation schematic. Do not import the reference's soil layers, levels, groundwater, pile length or construction findings. A matching P2 borehole/soil source is needed for geotechnical overlays. |
| p36–37 | Concrete-certificate annex. p36 is a caption/mostly blank; the visible p37 certificate reports concrete strength. It is not a plotted stress–strain/modulus curve. | Reference material documents do not prove P2 Ec. P2 E=34 GPa remains its own workbook input/model assumption. |

No further experimental curve family was found in the full extracted text. Photo pages, assembly drawings, calibration tables and report summary numbers are not additional measured graph series.

## Inputs needed before creating the unavailable physical/model curves

### Toe load, pressure or mobilization

1. Verified P2 toe position/area, lower gauge positions and effective stiffness/strain calibration.
2. An independently measured toe force, or an explicitly approved equilibrium/extrapolation model for the **uninstrumented segment between the last gauge and toe**, with uncertainty and residual/weight/buoyancy treatment disclosed.
3. To plot pressure-versus-load as Fig15 does: a defensible toe-force series paired with the actual recorded loading stages, and the P2 load convention.
4. To plot true toe mobilization **versus toe displacement**, which Fig15 does not show: calibrated, signed toe movement relative to a verified stable reference, including required beam/thermal/rod/elastic corrections and timestamp/stage pairing. Neither nominal load nor lower-plate movement may silently substitute for toe movement.

### Equivalent top-down curve

1. Verified mapping/calibration/direction for upper plate, lower plate, top and toe displacement channels; stable-reference corrections and synchronization.
2. Verified definition of P2's applied cell force and the separate upper/lower resistance curves.
3. A documented construction rule for matching component responses at compatible displacement, including elastic shortening/composite stiffness, initial/residual forces and weight/buoyancy as applicable. Simply adding two simultaneous displacements or doubling the recorded load is not an established construction.
4. The intended branch/cycle, interpolation form/degree, fitting points, admissible domain, extrapolation policy and independent checks. A polynomial fit is a model; it must not be presented as measured settlement or certified allowable capacity.
5. Engineering review/acceptance criteria before any capacity conclusion. The reference's project-specific conclusion is not a P2 criterion.

## Reference inconsistencies that must not become P2 assumptions

- **Toe level label:** p27 writes `Ft = ε5 × A × E` and describes the lowest gauge, while p28/p35 identify the lower-element gauge as SG6. No derivation explains how the p35 toe-force row is obtained below that gauge. The reference formula is insufficient evidence that a P2 lowest-gauge force equals toe force.
- **Unsigned-looking friction:** p35 gives SG2=4.4 tf and SG3=1.0 tf at nominal 40 tf, but its SG2–SG3 friction entry is positive 0.60 tf/m². A signed upper-element deeper-minus-shallower difference is negative. Therefore the reference's handling of negative gradients is not transparently reconciled. Keep P2's signed estimates.
- **Displacement summary labels:** p25 lists peak top plate 15.207 mm and top pile 14.348 mm. p32–33's summary associates approximately 14.38 with the top plate and 15.20 with the element head, reversing those identities. Do not adopt its summary labels to map P2 channels.
- **Protocol duration:** p20's planned schedule and repeated steps differ from p25's consolidated recorded-step table. P2 hold durations must come from P2 timestamps, not the reference's nominal timetable or minimum-hold prose.
- **Narrative conflict:** p5 says no obvious geotechnical failure, p20 mentions lower-element failure, while p32 says minimal lower displacement. These are reference-specific and unresolved; they are not P2 failure evidence.
- **Boundary/model endpoints:** the reference force-depth graph includes head, plate and toe values; P2's actual gauge rows do not supply these endpoints. Copying their visual continuity would invent P2 values.
- **Missing disclosures:** no polynomial coefficients/degree or full toe-force reconstruction method appears in the inspected main text. The pictures illustrate families, not a complete transferable computation protocol.

## Implementable P2 coverage

Supported now: combined all-level strain-versus-recorded-load with both branches; selectable reference-relative strain/stress/force-depth profiles; signed inter-gauge friction-depth steps; load and reported-channel histories from P2 timestamps; reported-channel change-versus-load with calibration limitations.

Must remain explicitly unavailable as verified physical results: calibrated/reference-corrected head/plate/toe displacement, toe-bearing pressure/capacity, equivalent top-down settlement, sonic integrity and hydraulic calibration. Missing families should have a short reason and input list, not a fabricated curve.
