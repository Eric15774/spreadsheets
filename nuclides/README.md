# Chart of Nuclides Data (2024)

Half-lives, decay modes and binding energies for 3,147 radioactive nuclides, from the IAEA LiveChart of Nuclides.

## Files

| File | What it is |
|---|---|
| `Nuclides2024.xlsx` | Workbook for class use. Sheets: About, Student View, Full Data, Decay Modes |
| `data/nuclides_student_view.csv` | One row per nuclide (ground state), 14 columns |
| `data/nuclides_clean.csv` | Every source row, cleaned, 66 columns |
| `data/Nuclides2024_raw.csv` | Original IAEA export, unchanged |

## Source

IAEA Nuclear Data Section, LiveChart of Nuclides: https://www-nds.iaea.org/relnsd/vcharthtml/VChartHTML.html

Exported 2024. Please credit the IAEA if you reuse this data, and check the IAEA terms of use.

## How the source is laid out

- Each row is one decay mode of one nuclear state. A nuclide with three decay paths (U-238: alpha, fission, double beta) takes three rows. Isomers (levelEnergy above 0) get their own rows too. That is why the raw file has 6,343 rows for 3,147 nuclides.
- Only radioactive nuclides are included. Stable nuclides such as H-1, C-12 and Fe-56 are not in the file.
- Energies are in keV unless the column name says MeV. `bindingEnergy` is per nucleon.

## Changes made in the cleaned files

- Removed 24 columns that were completely empty (separation energies, excited state energies, U-241 fission yields and others).
- Split `name` (for example `238U`) into `A` (mass number) and `symbol`.
- Added `halflife_seconds`, with every time unit converted to seconds (1 y = 365.25 d), so the column sorts correctly.
- Moved the `<`, `>` and `≈` signs out of `halflife` into `halflifeQualifier`. The source stored them as HTML codes (`&lt;`, `&asymp;`).
- The source marks 479 rows as `STABLE`, but they are exotic nuclides (for example Li-12, Fe-76) whose half-life has not been measured. In the cleaned files their half-life is blank and `halflifeMeasured` is `no`.
- About 32 very short-lived nuclides give a width in eV, keV or MeV instead of a time. Their `halflife_seconds` is blank.
- Changed a few Greek-letter decay codes to match the rest of the file (β⁻ to B-, ɑ to A, ε to EC).

## Student View columns

Z, N, A, Symbol, Nuclide, Half-life qualifier, Half-life, Unit, Half-life (s), Half-life measured?, Main decay mode, Main mode %, Other decay modes, Binding energy per nucleon (MeV)

"Main decay mode" is the path with the highest branching ratio. Other paths are listed with their percentages.

## Decay mode codes

| Code | Meaning |
|---|---|
| B- | Beta minus |
| EC+B+ | Electron capture and/or beta plus |
| EC | Electron capture |
| A | Alpha emission |
| IT | Isomeric transition |
| SF | Spontaneous fission |
| P, 2P, 3P | Proton emission (one, two, three) |
| N, 2N | Neutron emission |
| B-N, B-2N, B-3N, B-4N | Beta minus, then neutrons emitted |
| ECP, EC2P, EC3P | Electron capture, then protons emitted |
| ECA, B-A | Electron capture or beta minus, then alpha emitted |
| ECSF, B-SF | Electron capture or beta minus, then fission |
| 2B- | Double beta minus |
| 14C, 20O, 24NE, 28MG, 34SI, etc. | Cluster decay: emits that nucleus |

The full list with counts is on the Decay Modes sheet of the workbook.
