# Automated Climate Finance Policy Gap Analyser

This notebook compares internal climate-policy PDFs with a requirements library,
then produces a gap register and PDF report.

## Set up

Use Python 3.12 to create and activate a virtual environment:

```bash
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m ipykernel install --user --name climate-gap-analyser --display-name "Python (Climate Gap Analyser)"
jupyter lab climate_gap_analyser.ipynb
```

Select the **Python (Climate Gap Analyser)** kernel in JupyterLab.

## Provide input files

The notebook accepts a ZIP archive containing:

- One or more text-based policy PDFs (numbered section headings such as `3.1 Scenario analysis` are recommended).
- A `requirements_library.csv` file.

Run the notebook's setup cell. If the files are not already beside the notebook,
use the upload control that appears to select the ZIP, then run the setup cell
again before running the remaining cells. The archive is extracted to a
temporary directory. Alternatively, set `CLIMATE_GAP_INPUT_ZIP` to a ZIP path
before starting Jupyter for non-interactive use.

Results are written to `gap_outputs/` as `gap_register.csv`,
`gap_register.xlsx`, and `gap_analysis_report.pdf`. By default, retrieval uses
the notebook's TF-IDF fallback. To use sentence-transformer embeddings, install
the optional model dependency with `python -m pip install -r requirements-semantic.txt`;
model weights are downloaded on first use. Set
`OPENROUTER_API_KEY` to enable optional LLM refinement; without it, analysis
remains rule-based.

The requirement texts are paraphrased screening aids, not legal advice. Verify
results against primary sources before making compliance decisions.
