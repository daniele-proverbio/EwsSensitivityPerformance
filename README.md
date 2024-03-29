# EWS Sensitivity and Performance

Code to estimate the performance of EWS in approaching bifurcations and their sensitivity to the interplay of b-tipping and n-tipping.

### Considered model
Autoactivating positive feedback loop for enzymatic activity (Strogatz, 2018)


### Motivation: 
We often do not have access to complete models of biological switches. However, using the theory of topological dynamical systems, we might be able to perform "macroscopic" measures to assess the resilience of the system and its vicinity to critical points. The relevance of 2D models is justified by the active area of research of dimension reduction, which aims at mapping high-dimensional networks to low-dimensional effective models.  

### Aim 
Evaluate different summary statistics indicators and their performance in detecting the vicinity of a tipping point, singularly. 
Assess their performance by the parameter value at which  their increase is significant and provides an EWS.  
Inquire the role of n-tipping.

## Folders and reproducibility

A brief description is here provided. For other details, refer to Chapter 5 of the thesis referenced below.

### MATLAB simulation results
- simulate: folder containing the code to simulate the system (including statistical repreated experiments). Parameters used: c = 1.9:-0.002:1.68 (with c_0 = 1.78). To generate data for the analysis of sensitivity to noise level and n-tipping, change manually "noise" (ln 36), rename the output .mat file and run the code. Original noise values: [0.010,0.012,0.014,0.016,0.018,0.020,0.025,0.030,0.035,0.040,0.045,0.050]. 
  * simulate_after_transition: Euler-Maruyama, additive white noise
  * simulate_after_transition_mn: Milstein, multiplicative noise
  * simulate_after_transition_both: both noise types, weighted by \alpha. Change \alpha manually to test the various combinations
- data: where in silico data are saved. .mat file contain the "sol" variable (solution of simulations), indexed as as [time step, parameter value, experiment number]. Files can be quite heavy (>700Mb each) and are not saved, but can be reproduced as described above.
- data_mn: same, for simulations with multiplicative noise.
- analyse: code to analyse in silico data.
  * full_analysis: to generate all final figures and outputs for the analysis of simulations. It calls recursively the function "analysis.m"
  * analysis: function to analyse a single .mat file. It computes statistical indicators, looks for parameter values where indicator trends become significant (calling "testsignificance.m") and counts how many n-tippings occurred, at each parameter value, before the bifurcation point. It also allows plotting example figures of  statistical indicators.
  * full_optimise: to generate all final figures and outputs for the optimisation process. It calls recursively the function "optimise.m"
  * optimise: computes the combination of statisticall indicators, for the optimisation analysis.
  * optimal_plot: after extacting the weight sets associated to each \alpha (see simulate_after_transition_both), it produces the final plot
  * testsignificance: checks the first parameter value at whichthe increasing trend of statistical indicastors become significant
  * scaleStd: simple adjustments for plotting
  * wavelet_entropy_analysis: preliminary tests on wavelet entropy

### Mathematica analytical plots
In "graphs.nb", subdivided according to considered normal form.


### Data analysis (in Matlab)
Folder: analysisDai2012  
Public data from: Dai, L.; Vorselen, D.; Korolev, K. S.; Gore, J. (2012), Generic Indicators for Loss of Resilience Before a Tipping Point Leading to Population Collapse, Science, Article-journal, https://doi.org/10.1126/science.1219805
- bootstrap: function to perform bootstrapping on empirical data, to estimate distributions of indicators.
- full-analysis: estimate the indicators, calculate their significance for EWS


## Credits
Author: Daniele Proverbio, LCSB, 2022 (daniele.proverbio@outlook.com).
Please cite the corresponding thesis if you use any figure or code.

### Suggested citation (bibtex)
@thesis{Proverbio2022,   
author = {{Proverbio}, Daniele},   
publisher = {University of Luxembourg},   
title = {{Classification and detection of critical transitions}},   
year = {2022}
}
