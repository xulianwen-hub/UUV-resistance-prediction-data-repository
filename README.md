# Data for "Unmanned Underwater Vehicle Resistance Prediction Model Integrating Boundary Layer Prior Embedding and Hierarchical Fuzzy Cascading"

This repository contains the CFD-computed resistance dataset used in the above manuscript


## Overview

The dataset covers **70 Myring-type UUV hull forms** at **five advance speeds**
(1.029, 2.058, 3.087, 4.116 and 5.144 m/s), giving **350 records** in total.
For each hull form and speed, the pressure resistance, the frictional resistance and
the total resistance are given.

## Files

| File | Description |
|---|---|
| `resistance_data.csv` | Main dataset, comma-separated, UTF-8, header row included (350 data rows) |
| `LICENSE` | Creative Commons Attribution 4.0 International (CC BY 4.0) |

## Data dictionary

| Column | Unit | Description |
|---|---|---|
| `Length` | m | Overall hull length |
| `Width` | m | Maximum hull diameter |
| `Entry Length` | m | Length of the fore (entry) body |
| `Run Length` | m | Length of the aft (run) body |
| `fullness inflow` | – | Fullness coefficient of the fore (entry) segment, dimensionless |
| `fullness midship` | – | Fullness coefficient of the parallel middle body, dimensionless |
| `fullness out` | – | Fullness coefficient of the aft (run) segment, dimensionless |
| `speed` | m/s | Advance speed of the vehicle |
| `P` | N | Pressure (form) resistance |
| `S` | N | Frictional (skin-friction) resistance |
| `P+S` | N | Total resistance |

The seven geometry columns (`Length` … `fullness out`) are repeated for every speed, so
each hull form appears five times, once per speed.

## How to use

1. Group the rows by the seven geometry columns to recover the 70 individual hull forms.
2. Sort by `speed` within each group to obtain the resistance–speed curve of that hull form.
3. `P+S` equals `P + S` for every row, so the total can be recomputed from the two components.

Minimal example (Python):

```python
import pandas as pd

df = pd.read_csv("resistance_data.csv")
geom = ["Length", "Width", "Entry Length", "Run Length",
        "fullness inflow", "fullness midship", "fullness out"]

print(df.shape)                     # (350, 11)
print(df.speed.unique())            # [1.029 2.058 3.087 4.116 5.144]
print(df.groupby(geom).ngroups)     # 70 hull forms
```


## License

The dataset is released under the
[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)
licence. You are free to share and adapt the data for any purpose, provided appropriate
credit is given.

## Contact

Liangwen Xu — GitHub: [@xulianwen-hub](https://github.com/xulianwen-hub)
