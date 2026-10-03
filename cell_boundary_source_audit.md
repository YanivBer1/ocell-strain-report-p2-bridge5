# P2 cell and pile-head boundary source audit

Audited 2026-10-03. The user explicitly requested pile-head and O-cell force-profile boundary points. These additions reproduce the explicit source-workbook force-profile convention. They are labeled boundary conditions/points, not new strain gauges or invented strain measurements.

Source: `/Users/yanivberniker/Developer/foundation-lab-handoff-2026-09-30/trial-kit/Foundation Lab - ערכת ניסיון P2 גשר 5/03 - מקורות ודוגמאות - לעיון בלבד/WORK_FILE with EQU_line.xlsx`

Source SHA-256: `1ac477cd47eee7a928161c7db7886bbb7c10c72005306367de5ce16d9b76842e`

## Exact source convention

| Boundary | Depth source | Source profile coordinate | Source force rule |
| --- | --- | --- | --- |
| Pile head | Исходные данные!B17 = 0 m | Напряжения!M56 = 0 m | Напряжения!M57:M74 are literal zero values |
| Cell top face | Исходные данные!B22 = 22.9 m | Напряжения!H56 = 22.9 m | Напряжения!H57:H74 equal the full corresponding recorded load |
| Cell bottom face | Исходные данные!B23 approximately 23.3 m | Напряжения!G56 approximately 23.3 m | Напряжения!G57:G74 equal the full corresponding recorded load |

Profile row mapping is `sourceProfileRow = stage ID + 56` for stages 1-18. Source A57:A74 matches all 18 noninitial Raw Data load groups exactly: 45, 90, 135, 180, 225, 270, 315, 360, 405, 450, 540, 630, 720, 810, 900, 450, 225, 0 tf. In every source row, G=H=A and M=0.

Peak stage 15 maps to source row 71: `A71=900`, `G71=900`, `H71=900`, `M71=0`. Thus the explicit force-profile plotting convention is **900 tf at each cell face**, with a zero head boundary. It is not a 450 tf cell-face convention.

Initial stage 0 has no dedicated source profile row. Its boundary force increments are zero using the actual recorded zero load `Raw Data!A19` and the same source head-zero/face-equals-recorded-load convention. This initial boundary construction is explicitly recorded rather than attributed to a nonexistent source profile row.

## Conflicting source convention and calibration limit

The earlier table labels Напряжения!B2 as load in the cell and C2 as load in the elements. B4:B21 reproduces the same recorded load schedule as numeric literals, while C4:C21 is exactly B/2 throughout. In particular B18=900 and C18=B18/2=450. That table conflicts with the explicit force-profile G/H boundary values.

The earlier B values are not formula links to Raw Data, but their 18-stage numerical schedule matches Raw Data exactly. No pressure readings, active jack count, matching hydraulic calibration certificate, or verified rule resolves the physical meaning of this conflict. Setup C8 gives only the area of one jack, 201 cm2; it does not establish the number of active jacks or a pressure-to-load conversion. The boundary files therefore reproduce the source **profile** convention explicitly and retain the unresolved physical load interpretation.

The chosen full-load boundary is not independently certified hydraulic force, an extra SG measurement, or a pressure-derived reconstruction. Existing SG strain means and estimated forces are unchanged. The source zero-head values represent a boundary condition, not a measured zero strain reading. No boundary strain is inferred. No force line or load-transfer interval passes through the 22.9-23.3 m cell gap.

## Additional boundary-derived intervals

Using diameter 1.2 m from setup C4 and the existing unchanged mean-gauge force estimates:

| Interval | Part | Depth span | Length | Signed transfer convention |
| --- | --- | --- | --- | --- |
| Head-SG1 | Upper | 0-9.7 m | 9.7 m | SG1 force minus zero head boundary |
| SG4-CellTop | Upper | 21.2-22.9 m | 1.7 m | top-face boundary force minus SG4 force |
| CellBottom-SG5 | Lower | 23.3-24.1 m | 0.8 m | bottom-face boundary force minus SG5 force |

Mean boundary-derived shaft-stress increment is `transfer_tf * 9.80665 / (pi * 1.2 * length_m)` in kPa. All 57 rows are explicitly tagged `source=boundary`, `boundaryDerived=true`; they are not inter-gauge-only measured intervals and are exported to a separate boundary_interval_results.csv. Original stage_results.csv and load_transfer.csv are not edited.

Negative values and strain-level review flags are preserved. At peak stage 15:

- Head-SG1 transfer = 245.684059468 tf; mean shaft-stress increment = 65.886251842 kPa.
- SG4-CellTop transfer = 119.060718923 tf; mean shaft-stress increment = 182.183539790 kPa.
- CellBottom-SG5 transfer = -10.908428703 tf; mean shaft-stress increment = -35.470047274 kPa. The negative estimate remains negative and flagged; it is not adjusted to force agreement with the nominal source cell boundary.

All forces/stresses are baseline-relative estimates or source boundary increments. Initial/residual stress, self-weight, buoyancy, hydraulic load calibration, and physical load-convention corrections remain unverified and unapplied.

## Independent numerical mini-validation

2,547 comparisons matched with zero mismatches; maximum floating difference 7.96e-13. Checked all 57 boundary points, all 57 derived intervals, direct source row/depth mappings and earlier /2 contradictions, independently recomputed the relevant gauge forces/flags from Raw Data frequencies and baseline row 19, and checked every CSV data cell (57 rows by 19 columns = 1,083 cells).

No numeric source observation was imputed. The added head/cell points are explicitly source boundary conditions, not measurement samples. The validation demonstrates faithful reproduction and arithmetic, not independent engineering certification of the hydraulic force convention.
