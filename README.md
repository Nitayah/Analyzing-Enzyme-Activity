# Comparing Enzyme Activity Across Variable Experimental Conditions

## Introduction
Experimental results for plastic-degrading enzymes are often obtained under highly variable conditions (e.g., experiment duration, substrate type), making direct comparisons of enzyme performance unreliable.  
This project explores whether **transitive qualitative rankings** can overcome this limitation, enabling the identification of highly active enzymes in a dataset with highly variable experimental conditions.

Example:  
If enzyme A outperforms B in one experiment and B outperforms C in another, can we infer that A outperforms C even if experimental conditions differ?

## Hypothesis
Enzyme performance rankings remain transitively consistent across different setups, allowing meaningful comparisons even when conditions vary.

## Dataset
The analysis uses published experimental data from **Erickson et al. (2022)**, in which 19 enzymes were tested on:
- **Three PET substrates:** amorphous film, amorphous powder, semi-crystalline powder
- **Eight time points** in a time-course experiment

Each unique combination of substrate and time point is treated as a distinct experiment, yielding **24 experiments** in total.

## Methodology
1. **Ranking within experiments:**  
   For each experiment, enzymes were ranked by performance.
2. **Rank correlation:**  
   Kendall Tau (τ) was calculated for every pair of experiments to quantify ranking agreement.  
   - τ = 1 → perfect agreement  
   - τ = 0 → no correlation  
3. **Probability interpretation:**  
   Ranking agreement probability was computed as `p = (τ + 1) / 2`.

## Key Findings
- **Rankings are robust:** Even the lowest τ value (0.47) corresponds to a **73.5% probability** of consistent rankings across experiments.
- **Substrate form effect:** Rankings correlate better when both experiments use **powder** (regardless of crystallinity) than when using amorphous substrates of different forms (film vs. powder) — an unexpected result.
- **Practical implication:** Transitive rankings can be applied to larger datasets, such as the **PANDA dataset** (~250 experiments, ~100 enzymes), to identify highly active enzymes despite varying experimental conditions.

## Visualization
A heatmap of Kendall Tau correlations shows:
- Square `E` (both experiments use powder, amorphous vs. crystalline) shows better correlation than square `B` (both experiments use amorphous substrate, powder vs. film)
- Square `D` (lower part): lowest correlation (different substrate type and time)

## Disclaimers
- Different time points of a single time-course experiment were treated as independent experiments. This mainly affects same-substrate comparisons (squares `A`, `C`, `F` in the heatmap), while conclusions are based on comparisons where both substrate type and duration differed.
- The PANDA dataset may differ in more than two experimental conditions (e.g., measurement tools, enzyme concentration), potentially lowering the real-world likelihood of ranking agreement.

## Publication
Following this analysis, the method was applied to the PANDA dataset, identifying 20 highly active enzymes.  
These results passed peer-review in the journal **Protein Science** (Q1) under the title:  
*"The diversity of PET degrading enzymes: a systematic review of sequence, structure, and function"*, and are pending publication (Aug 25).

## Repository Contents
- **Comparing Enzyme Activity.ipynb** — Full analysis with code, results, and visualizations  

- **data.xlsx** — Processed dataset from Erickson et al. (2022) 
