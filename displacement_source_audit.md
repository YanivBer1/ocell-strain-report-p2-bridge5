# Displacement source audit - P2 Bridge 5

Audited 2026-10-03.

## Source and method

Source workbook: `WORK_FILE with EQU_line.xlsx`

SHA-256: `1ac477cd47eee7a928161c7db7886bbb7c10c72005306367de5ce16d9b76842e`

Test identity in `Исходные данные!C2`: P2 Brige5. Diameter in C4: 1.2 m. Modulus in C12: 34 GPa. Recorded maximum load: 900 tf. These identify the P2 dataset; graphs from another test do not supply its numerical measurements.

All five displacement channels `Raw Data!AN2:AR155` are finite numeric literals, already labeled mm in the workbook. They contain no cell formulas. No channel calibration coefficients, installation polarity certificate, or calibration sheet was found in the workbook. These outputs preserve the workbook-reported values; they do not verify their physical calibration, infer displacement from frequency, apply elastic corrections, or certify settlement/capacity.

Signed change is `reported_mm(row) - reported_mm(19)`, preserving negative values. It is an instrument-channel change, not a verified physical upward/downward direction. Origin `(0,0)` is the actual final zero-load reference, not an added measurement.

Baseline: `Raw Data!19`, timestamp 2020-03-01 16:55:00 (original timestamp includes 0.005 s). The timeline uses rows 19-155 inclusive, 137 records. Stage endpoints use each contiguous load group's actual last row, cross-checked against the existing strain report's 19 stages. Loading and unloading remain in chronological order. CSVs include both original workbook-reported mm and signed changes; JSON values are signed changes.

| ID | Source | Workbook header | Baseline mm | Status |
| --- | --- | --- | ---: | --- |
| base | Raw Data!AN | base (mm) | 9.674768 | Reported channel; calibration/direction unverified |
| down | Raw Data!AO | down plate (mm) | 59.070396 | Reported channel; calibration/direction unverified |
| crack | Raw Data!AP | crack (mm) [source header encoding damaged] | 7.617234 | Always flagged; unreliable opening interpretation |
| up | Raw Data!AQ | up plate (mm) | 81.605808 | Reported channel; calibration/direction unverified |
| top | Raw Data!AR | top (mm) | 132.213740 | Reported channel; calibration/direction unverified |

## Stage endpoint validation

| Stage | Recorded load tf | Phase | Source row | base change mm | down change mm | crack change mm | up change mm | top change mm |
| ---: | ---: | --- | ---: | ---: | ---: | ---: | ---: | ---: |
| 0 | 0 | Baseline | 19 | 0.000000 | 0.000000 | 0.000000 | 0.000000 | 0.000000 |
| 1 | 45 | Loading | 24 | 0.025084 | 0.026916 | 0.448951 | 0.000848 | -0.008660 |
| 2 | 90 | Loading | 29 | 0.032890 | 0.042464 | 0.452667 | 0.009232 | 0.032320 |
| 3 | 135 | Loading | 33 | 0.040274 | 0.055956 | 0.627693 | 0.020592 | 0.040760 |
| 4 | 180 | Loading | 41 | 0.070044 | 0.073716 | 0.825486 | 0.038048 | 0.052660 |
| 5 | 225 | Loading | 45 | 0.087050 | 0.090456 | 1.123542 | 0.010496 | 0.060560 |
| 6 | 270 | Loading | 49 | 0.164854 | 0.126480 | 1.443832 | 0.007152 | 0.101460 |
| 7 | 315 | Loading | 53 | 0.451652 | 0.154448 | 2.014702 | 0.000272 | 0.118920 |
| 8 | 360 | Loading | 59 | 1.578994 | 0.344696 | 3.800568 | -0.077352 | 0.110840 |
| 9 | 405 | Loading | 66 | 4.335914 | 3.413848 | 6.861260 | -0.085744 | 0.095540 |
| 10 | 450 | Loading | 72 | 7.854598 | 7.529160 | 10.641304 | -0.128928 | 0.071320 |
| 11 | 540 | Loading | 84 | 18.414412 | 19.728212 | 21.754340 | -0.265128 | -0.082820 |
| 12 | 630 | Loading | 100 | 36.159896 | 39.773044 | 40.606950 | -0.569984 | -0.577140 |
| 13 | 720 | Loading | 120 | 50.691024 | 56.851024 | 102.351046 | -1.584632 | -1.658260 |
| 14 | 810 | Loading | 137 | 66.481768 | 75.021524 | 74.391086 | -3.291552 | -3.266460 |
| 15 | 900 | Loading | 146 | 74.208376 | 83.825024 | 83.192446 | -4.198336 | -4.204800 |
| 16 | 450 | Unloading | 149 | 74.228192 | 83.784624 | 81.549862 | -4.206640 | -4.117000 |
| 17 | 225 | Unloading | 152 | 74.144496 | 83.322984 | 79.549590 | -4.194328 | -3.853500 |
| 18 | 0 | Unloading | 155 | 73.883144 | 79.947224 | 74.801174 | -3.981176 | -3.040960 |

## Anomalies and rejected processed pairings

- The top channel has large initialization changes before the final baseline. `Raw Data!AR13 = -2342.3476 mm`; early AR2-AR12 change from 33.43769 to 132.16184 mm under zero recorded load. Pre-baseline readings are retained in the source workbook but excluded from this displacement timeline.
- Crack rises by 37.435012 mm between source rows 111 and 112 and drops by 43.378172 mm between rows 121 and 122. Stage 13 at 720 tf ends with change 102.351046 mm; stage 14 at 810 tf ends with change 74.391086 mm. This channel is flagged for every stage/record. It must not be represented as verified O-cell opening, silently corrected, or used in capacity calculations.
- Processed Sheet1 pairings are unreliable: Sheet1 row 3 marked 0 tf uses Raw Data row 20 at 45 tf; Sheet1 row 4 marked 45 tf uses Raw Data row 25 at 90 tf; Sheet1 row 13 marked 450 tf uses Raw Data row 73 at 540 tf; Sheet1 row 18 marked 900 tf uses Raw Data row 147 at 450 tf; Sheet1 row 19 marked 450 tf uses Raw Data row 150 at 225 tf; Sheet1 row 20 marked 225 tf uses Raw Data row 153 at 0 tf. Most processed values use the first row of the next load group. This export uses Raw Data stage endings exclusively.
- Sheet1 deltas contain undocumented changes. Down-plate raw value plus signed delta implies baseline 59.05448 mm through 720 tf, 61.05448 mm at 810 tf, 63.05448 mm at 900 tf/450 tf unloading, 60.05448 mm at 225 tf unloading. Crack has an apparent 43 mm correction at 720 tf and 1 mm changes later. None are reproduced here.
- Sheet2 normal-load-equivalent polynomial is a fit, not a measured curve. It predicts about 548.77 tf at 0.01 mm while an explicit row is forced to 0 tf at 0 mm. Fit calibration/validity was not established. It must not be promoted as verified equivalent top-down capacity.
- Workbook charts include broken #REF! references and external sources in a different workbook. These charts were not used for measured trace reconstruction.

## Other valid graph families from existing P2 data

1. Mean compression strain versus recorded load for SG1-SG4 (upper) and SG5-SG7 (lower), using the same axes for loading and unloading. X: recorded load tf. Y: mean strain microstrain. Preserve chronological ordering and repeated loads on return. They may be combined in one all-level chart with upper/lower filters.
2. Strain profiles by stage: X mean strain; Y depth m increasing downward. This differs from strain versus load and should not be rotated to match it.
3. Estimated axial-force profiles by stage: X estimated force tf; Y depth m increasing downward. Upper/lower segments can share one canvas but must not connect across the O-cell gap. Only actual gauge depths are measured. Do not fabricate a measured pile-head or cell-boundary point.
4. Estimated mean shaft friction by depth as step profiles: X q_s kPa; Y depth m increasing downward. Draw constant values only across valid gauge intervals SG1-SG2 (9.7-14.2 m), SG2-SG3 (14.2-18.0 m), SG3-SG4 (18.0-21.2 m), SG5-SG6 (24.1-26.2 m), SG6-SG7 (26.2-28.7 m). Leave uninstrumented/cell intervals blank; preserve negative values and review flags. A bar chart by interval alone does not match the reference depth-profile family.
5. Estimated load transfer or shaft friction versus recorded load for each valid interval, with loading and unloading. Conversion to local displacement/friction mobilization is unjustified because local relative displacement at those intervals is not measured.
6. Recorded load versus elapsed time, reported instrument-channel change versus elapsed time, and reported instrument-channel change versus recorded load; displacement timeline starts at source row 19.

Strain-derived force and friction retain existing assumptions E=34 GPa, diameter 1.2 m, three-sensor mean, gauge factor 3.304, baseline row 19. They are estimates, not independent force measurements.
