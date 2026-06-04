# Statistical Analysis Lab

This project analyzes marketing performance across platforms using a notebook-first workflow.
It covers data preparation, pairwise statistical testing, multiple-comparison correction, bootstrap confidence intervals, and power analysis.

## Project Contents

- `statistical_analysis.ipynb` - main notebook with the full analysis workflow
- `marketing_data.csv` - cleaned and prepared dataset used by the notebook
- `cpa_comparison_results.csv` - pairwise CPA t-test results
- `fisher_comparison_results.csv` - pairwise conversion-rate Fisher test results
- `cpa_confidence_intervals.csv` - bootstrap confidence intervals for daily CPA
- `power_analysis_results.csv` - Monte Carlo power simulation results
- `group_metrics_overview.png` - summary chart of key platform metrics
- `group_distributions.png` - distribution plots for daily metrics
- `group_distributions_boxplot.png` - boxplots for daily metric variability
- `metric_comparison_heatmap.png` - CPA pairwise p-value heatmap
- `rate_comparison.png` - conversion rate comparison chart
- `correction_comparison.png` - significance comparison after corrections
- `power_analysis_cpa.png` - CPA power curve chart

## Requirements

Install the project dependencies with:

```bash
pip install -r requirements.txt
```

## How to Run

1. Open `statistical_analysis.ipynb` in Jupyter or VS Code.
2. Select the project kernel or your `.venv` kernel.
3. Run the notebook from top to bottom.

The notebook will:

- load `marketing_data.csv`
- run the statistical analysis
- generate the tables and plots
- save the final outputs in the project folder

## Notes

- The notebook is the primary deliverable for this lab.
- The generated CSV and PNG files can be recreated by rerunning the notebook.
- If you update the data preparation step, rerun the notebook so all outputs stay in sync.

