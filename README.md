# Attack Patterns in Cross-Chain Bridges

Dataset, codebook and analysis scripts for the paper *Attack Patterns in Cross-Chain Bridges* (Samiha, Rahman and Mukta).

We collected 48 cross-chain bridge attacks that happened between January 2022 and August 2026. Together they account for about USD 2.676 billion in losses. Every incident is assigned one of six attack patterns (PF, LE, EI, ESM, CS, IH) and one of five functional domains (FD-1 to FD-5).

## What is in here

- `data/incidents.csv`: the 48 incidents
- `data/excluded_incidents.csv`: 12 candidates we looked at and left out, with the reason for each
- `data/sources.csv`: the sources behind each incident
- `data/data_dictionary.csv`: what each column means
- `codebook/`: inclusion rules, pattern and domain definitions, and how boundary cases were handled
- `analysis/`: Python scripts that produce the tables and figures
- `results/`: the generated tables and figures
- `supplementary/supplementary_tables/`: all 64 boundary-case combinations, and losses by loss basis

## Running the analysis

You need Python 3.9 or newer.

```bash
pip install -r requirements.txt
python analysis/generate_tables.py
```

## Things to keep in mind

- The incidents are the ones we could find and verify, not a random sample, so the results describe this set only.
- 2026 only covers January to August.
- Losses are gross. Funds that were later recovered are not subtracted. The `loss_basis` column says what each figure actually measures.

## License

Code is under the MIT license. Data and documentation are under CC BY 4.0. Details are in `LICENSE`.

## Citing

Samiha, I., Rahman, Y., and Mukta, R. (2026). *Attack Patterns in Cross-Chain Bridges: Dataset, Codebook, and Analysis* (v1.0.0). Zenodo.

See also `CITATION.cff`.
