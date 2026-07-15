Downloads Colorado construction data from two federal sources with no API yet, cleans it, and loads it into the SDO Postgres database (`econ` schema). Used by `state_forecast_2025` (CO construction behavioral equations) and available for other SDO projects.

Sources:
- Census C30 "Value of Private Nonresidential Construction Put in Place, by State" (state only -- no county breakdown exists)
- Census/HUD Building Permits Survey (BPS) -- residential permits (buildings/units/valuation), state and county

Writes three tables (full overwrite each run, matching `process_lehd`'s `econ.commute` pattern):
- `econ.construction_value_state` -- C30 nonresidential value put in place
- `econ.construction_permits_state` -- BPS residential permits, state
- `econ.construction_permits_county` -- BPS residential permits, CO counties

Also writes the same three tables as CSVs at the repo root (committed to git, as an audit trail -- same pattern as `process_lehd`'s `lehd_mjh.csv`).

To refresh with a newly-published annual vintage, just re-render `construction_data.qmd`.
