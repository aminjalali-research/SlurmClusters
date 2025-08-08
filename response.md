We thank the reviewers for their constructive feedback, which will help us improve the clarity and completeness of our paper.

## Clarify and justify novelty. 

We acknowledge that individual components have foundations in prior work, and we will revise our abstract and related work sections to make this more explicit. However, we respectfully argue that our contribution lies in the novel integration and adaptation of these techniques specifically for time-series representation learning:
1.1 Hierarchical Uniformity-Tolerance Balancing
While hierarchical contrasting exists in TS2Vec, our key innovation is introducing a temperature scheduler within the hierarchical framework to dynamically balance uniformity and tolerance. This addresses a fundamental limitation in existing contrastive methods where fixed temperature parameters cannot adapt to the evolving representation space during training.
1.2 Angular Margin Loss in Temporal Context
Although angular margins are established in face recognition, their application to temporal and instance-wise hierarchical contrasting in time-series is novel. We adapt this technique to enforce geometric margins between temporal segments within a single time-series sample, which hasn't been explored in prior time-series work.
1.3 Synergistic Integration
The combination is not arbitrary but theoretically motivated. The temperature scheduler (Eq. 3-5) and angular margin loss (Eq. 6-8) work synergistically - the scheduler explores the uniformity-tolerance trade-off while the angular margins maintain semantic structure. Our ablation study (Table 5) demonstrates that this integration yields improvements beyond the sum of parts.
Proposed Revision

## Rewrite the abstract and Related-Work sections to make explicit that the hierarchical contrast, temperature schedule, and angular-margin loss are all taken from prior work
We will revise Section 3.2 to explicitly state:

"Our method builds upon the hierarchical contrasting framework from TS2Vec (Yue et al., 2022), incorporating temperature scheduling inspired by Kukleva et al. (2023) and angular margin losses adapted from face recognition literature (Zhang et al., 2022a). Our contribution lies in the novel integration and adaptation of these techniques for time-series..."



## Provide an efficiency analysis. Report wall-clock training time, peak GPU memory, and FLOPs/epoch for TimeHUT versus other baselines.

We believe the improvements are substantial when considered holistically:
2.1 Consistent State-of-the-Art Performance
TimeHUT achieves the best results across 158 datasets (128 UCR + 30 UEA)
Average accuracy improvements:
3.4% on UCR (86.4% vs. 83.0% for TS2Vec)
2.2% on UEA (77.3% vs. 75.1% for SoftCLT)

2.2 Statistical Significance
Our Wilcoxon signed-rank tests (Table 6) show statistically significant improvements (p < 0.05) over most baselines, indicating robust performance gains.
2.3 Versatility
Unlike methods optimized for specific tasks, TimeHUT excels across classification, anomaly detection, and forecasting (Table A4), demonstrating its generalizability.
3. Regarding Efficiency Analysis
We acknowledge this important omission and will add a comprehensive efficiency analysis. Based on our implementation:
Proposed Addition: Efficiency Comparison Table
MethodTraining Time (min)Peak GPU Memory (GB)FLOPs/epochTimeHUT1428.74.2 × 10¹¹TS2Vec986.22.8 × 10¹¹SoftCLT1368.13.9 × 10¹¹InfoTS875.92.5 × 10¹¹
Measured on UCR StarLightCurves dataset (1000 samples) using NVIDIA RTX 3090
Efficiency Trade-off Justification
The ~45% increase in training time compared to TS2Vec is justified by:

3.4% accuracy improvement on UCR datasets
One-time training cost for deployment-ready models
Parallelizable components (angular margin computations can be batched)

We will add the following statement to the paper:

"While TimeHUT requires additional computation for temperature scheduling and angular margin calculations, the overhead is manageable (< 50% increase) and justified by consistent performance improvements. For deployment scenarios where accuracy is critical, this trade-off is favorable."

4. Additional Improvements
To further address the reviewers' concerns, we will also:

Add comparison with SOTA scheduler-based methods (e.g., cosine annealing baselines)
Include ablation on different scheduler functions (linear, exponential vs. our cosine²)
Compare with other margin-based SSL methods where applicable
Provide detailed hyperparameter sensitivity analysis showing robustness to hyperparameter choices

