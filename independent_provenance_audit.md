# Independent numerical provenance audit - P2 Bridge 5

Audit date: 2026-10-03.

All 24,202 independent comparisons matched, with zero mismatches. Largest floating-point difference: 3.85e-13. This verifies numerical reproduction from the available workbook under the report's stated calculation choices. It is not engineering validation of sensor calibration, material behavior, or capacity.

Source: `WORK_FILE with EQU_line.xlsx`

Source SHA-256: `1ac477cd47eee7a928161c7db7886bbb7c10c72005306367de5ce16d9b76842e`

## What was checked

| Report data | Exact source / calculation | Rows or values checked |
| --- | --- | ---: |
| Recorded load and timestamps | Raw Data!A2:A155 and C2:C155 | 154 records |
| 21 SG1-SG7 frequencies | Raw Data!F2:Z155 | 3,234 frequencies |
| 21 compression-strain values per reading | Factor 3.304 times baseline-frequency squared minus current-frequency squared, divided by 1,000 | 3,234 calculated strains |
| Stage boundaries, chronology, load and source markers | Contiguous source load groups; Raw Data!B first-row markers agree with stage IDs | 19 stages |
| Endpoint gauges, arithmetic mean, time mean, stress, force, spread flags | Recalculated independently from final source row in each stage | 133 stage-level rows |
| Transferred load and mean shaft stress | Recalculated from adjacent endpoint force estimates and source gauge-depth intervals | 95 interval rows |
| stage_results.csv | Every cell checked against independently recalculated stage data | 133 rows |
| load_transfer.csv | Every cell checked against independently recalculated interval data | 95 rows |
| logger_calculations.csv | Every cell checked against Raw Data and independent strain calculation | 154 rows |
| Sensor mapping and baseline/peak examples | Raw Data!F:Z at rows 19 and 146 | 21 gauges |

## Inputs present in the source

| Input | Workbook source | Value |
| --- | --- | --- |
| Pile diameter | Исходные данные!C4 | 1.2 m |
| Concrete modulus used in calculations | Исходные данные!C12 | 34 GPa |
| Gross circular area | Report uses pi times diameter squared / 4; workbook C5 uses the same expression in cm2 | 1.1309733552923256 m2 |
| Common strain calculation factor | Стрейны!D2, D3 and 397 other formulas for SG1-SG7 | 3.304 |
| O-cell top | Исходные данные!B22 | 22.9 m |
| O-cell thickness | Исходные данные!D22 | 0.4 m |
| O-cell bottom | Исходные данные!B23 | approximately 23.3 m |
| Pile base depth | Исходные данные!B27 and D28 | approximately 29.2 m |
| Gauge depths | Исходные данные!B18:B21 and B24:B26 | 9.7, 14.2, 18.0, 21.2, 24.1, 26.2, 28.7 m |

Factor provenance is explicit: `Стрейны!D2` contains `=SG!C2^2*3.304/1000` and `Стрейны!D3` contains `=SG!C3^2*3.304/1000-$D$2`. Its presence in the workbook proves the factor was carried from the source calculation, not invented. It does not prove this common factor is the certified calibration of each installed gauge.

## Missing values automatically filled

None. No missing numeric observation, gauge frequency, stage endpoint, source depth, modulus, or diameter was imputed. No numerical measurements came from the reference PDF or attached chart photographs. The complete 52-page reference PDF is now available and is being used for graph structure, axes, loading/unloading continuity, and presentation only. Its numerical measurements are not copied into this P2 dataset; it concerns a different load test.

## Choices made by the report

- **Zero reference:** Final initial zero-load Raw Data row19 chosen for all 21 channels; processed workbook uses a different baseline.
- **Compression-positive sign:** 3.304*(f_zero^2-f_current^2)/1000; reverse sign of the workbook processed delta formula.
- **One common gauge factor:** Workbook 3.304 convention applied to all 21 channels SG1-SG7; individual calibration remains unverified.
- **Sensor averaging:** Equal arithmetic mean of all3 gauges per level, no sensor exclusion or imputation; stage time mean is unweighted arithmetic mean of the recorded means.
- **Force/stress model:** Uniform E=34GPa times strain; gross circular area pi*1.2^2/4; ignore reinforcement contribution, steel area, composite stiffness, and modulus variation.
- **Unit conversion:** 1tf=9806.65N; exact conventional SI conversion rather than workbook rounded10.1972tf/cm2 per GPa.
- **Load/stage classification:** Contiguous equal recorded load groups, checked against source markers; baseline0, stages1-15 loading,16-18 unloading. Recorded load retained unchanged; no halving/doubling.
- **Transfer direction:** Upper deeper force minus shallower; lower shallower minus deeper; divide bypi*diameter*intervalLength for mean shaft stress. Negative results preserved.
- **Review thresholds:** Spread computed if abs(mean)>=20 microstrain; flag spread>25%. Interval flagged if either endpoint flagged ortransfer negative. These are report review heuristics, not acceptance criteria.
- **Display/model limits:** No gauge extrapolation to pile head/cell boundaries; no measured head point inserted; no force line across O-cell; no synthesized local displacement/capacity.

These choices are distinct from missing-value filling. Some are source-carried modeling conventions; others are report calculation/display choices. Their effect must be disclosed when using the results.

The final initial zero-load reading is Raw Data row 19, dated 2020-03-01 16:55:00. The peak endpoint is row 146 at recorded load 900 tf. The zero-load baseline point is real, but no strain gauge exists at pile-head depth 0 m; therefore no measured head point at (0,0) can be added to depth profiles. Source timestamps are exported to whole seconds; source microseconds are discarded only for display.

## Engineering inputs not supplied / not verified

- Per-sensor calibration certificates and factors.
- Verified sensor orientation/compression sign and temperature compensation.
- Measured concrete modulus test report and its applicable range.
- Reinforcement area/stiffness and composite axial rigidity.
- Installation/as-built gauge elevations independently certified.
- O-cell pressure/load calibration and whether recorded load is combined or per-element.
- Displacement calibration/polarity certificates.
- Verified local relative displacement for shaft-mobilization curves.
- Verified toe load/resistance and equivalent top-down model inputs.

These remain missing. The audit does not silently substitute certificates, material tests, reinforcement quantities, local displacement, toe resistance, or load-system interpretation.

## Source inconsistencies

- The processed SG sheet contains timestamp strings for 2019-07-15 while Raw Data is dated 2020-03-01/02. Reconstructed timestamps use Raw Data exclusively. This inconsistent processed metadata does not supply the report chronology.
- Setup A6 labels pile length in cm although C6 is 29.2. The geometry depth table B27/D28 defines a 29.2 m pile; the report follows that meter-based geometry.
- Raw Data A1 says only Load. In the processed sheet, Напряжения!B2 describes load in the cell, C2 describes load in the elements, and C4=B4/2. The available data do not establish whether the recorded load represents combined or per-element force. The report retains the recorded load unchanged and does not convert it to capacity.
- SG8 frequency columns AA:AC were not included: no SG8 depth is defined in the source geometry, and processed SG8 formulas use a different factor, 4.062. Its location/calibration were not invented.
- Processed displacement Sheet1 often assigns readings from the first row of the next load stage to the preceding load and includes unexplained adjustments. Its edited delta values were not used. See displacement_source_audit.md.

No unexplained numerical mismatch was found in the original strain report reconstruction. Remaining uncertainty concerns physical interpretation and missing engineering provenance, not arithmetic reproduction.

## Independent verification of the new displacement outputs

Independently reconstructed displacement_data.json from the actual source mm columns AN:AR, with no dependency on the displacement builder's calculations. This extension adds 4,126 comparisons to the original 20,076 strain/transfer comparisons, for 24,202 comparisons overall. All matched; there were zero mismatches.

- Five source baseline values at Raw Data row 19 and the exact source-column mapping checked.
- All 19 stage endpoints, their recorded load, phase, timestamps, final source rows, and all 95 signed channel changes checked.
- All 137 timeline records from source rows 19-155, including 685 signed channel changes, checked.
- Every displacement_stage_results.csv data cell checked: 19 rows by 17 columns, 323 cells, plus its header and shape.
- Every displacement_logger_results.csv data cell checked: 137 rows by 16 columns, 2,192 cells, plus its header and shape.
- Original workbook-reported mm and calculated signed differences in both CSVs checked separately against the source.
- Crack anomalies at source rows 112 and 122 and the pre-baseline top anomaly at row 13 verified directly from source values.

The source baseline values are base=9.674768 mm, down=59.070396 mm, crack=7.617234 mm, up=81.605808 mm, and top=132.213740 mm. Changes are current source reading minus the source row 19 reference, preserving their sign. No absolute-value conversion, inferred direction, hidden correction, smoothing, missing-value fill, or edited Sheet1 pairing is involved.

Displacement calibration, physical installation direction, and the crack channel's interpretation remain unverified. Passing these checks proves reproduction of reported instrument-channel numbers and their arithmetic differences; it does not certify physical settlement, uplift, or O-cell opening. The crack channel remains flagged for review throughout.

## Reference PDF scope and baseline-relative estimates

The complete 52-page reference PDF is available at `/Users/yanivberniker/Developer/ocell_reference_analysis/reference-report.pdf`.

Reference PDF SHA-256: `a89c52d4ec958908222eb66e40963bc28e1818a117d51f3f64cb7c58e76e8edf`.

Its role is graph structure, axis orientation, loading/unloading continuity, and presentation only. All reported P2 numeric measurements and calculated values remain reconstructed from the P2 WORK_FILE workbook. No numeric observations were copied from the reference report.

Compression strain is a change relative to Raw Data row 19. Consequently estimated concrete stress and axial force are **baseline-relative increments**, not absolute in-situ stress or force. Mean shaft stress computed from adjacent incremental forces is likewise a baseline-relative increment rather than a certified absolute soil-resistance profile.

No initial/residual concrete stress or initial axial-force profile, pile self-weight/submerged effective unit weight distribution, or groundwater/buoyancy corrections were supplied or applied. These are missing engineering inputs; they have not been invented or silently assigned zero. Zero strain change at the reference reading does not prove zero actual initial stress, force, or shaft resistance.

The independent numerical verification count remains **24,202 comparisons with zero mismatches**. This interpretation note adds no measurement data and changes no calculation results.


## Subsequent source-boundary display update

The original 24,202 checks above cover preserved gauge/channel data. Source-workbook head and cell-face boundaries were subsequently added as explicitly distinct squares/dashed guides; they are not new strain-gauge measurements. The force-profile table G/H/M assigns the recorded stage load to each cellface and zero at the head. A separate earlier /2 table remains contradictory and disclosed. Three additional boundary-derived interval estimates per stage are in boundary_interval_results.csv; their source audit cell_boundary_source_audit.md reports 2,547 additional comparisons with zero mismatches. Original numeric datasets remain unchanged.
