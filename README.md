# Evading Detection: Deceiving Machine-Text Detectors through Realistic Red Teaming Attacks

This repository contains the report and resources for our project: **Evading Detection: Deceiving Machine-Text Detectors through Realistic Red Teaming Attacks**. This project explores vulnerabilities in machine-generated text detectors through realistic red teaming methods which preserve text quality.

Initial exploration included a study on how the DetectGPT method works

[YouTube (Report/Demo) - Part 1](https://www.youtube.com/watch?v=h8XT2ENvBl8)

[YouTube (Report/Demo) - Part 2](https://www.youtube.com/watch?v=h8XT2ENvBl8)

## Overview

With the growing adoption of Large Language Models (LLMs), there is a critical need to detect machine-generated text. Zero-shot detection methods like DetectGPT show promise but remain vulnerable to red teaming attacks. Our project:
- Analyzes these vulnerabilities using word substitution and paraphrasing methods.
- Introduces quality and context-preserving attack strategies.
- Extends evaluations to other zero-shot methods like FastDetectGPT, DetectLLM and DNA-GPT.
- Test detection performance and robustness of zero-shot methods.

## Approach

1. **Text Generation**:
   - Collected 100 human-written samples from the *xsum* dataset.
   - Generated machine-generated text using GPT-2-xl.

2. **Attack Strategies**:
   - **Random Substitution**: Replace up to 20% of words with synonyms.
   - **Thresholding**: Limits log probability degradation to 0.2 or 0.4 using a third-party LLM.
   - **Genetic Algorithms**: Optimize word replacements to evade detection while maintaining context.

3. **Evaluation**:
   - Tested original and attacked samples on DetectGPT, FastDetectGPT, and DNA-GPT.
   - Measured detection performance using AUROC scores.

## Key Results

- **Quality-Preserving Attacks**: Even with thresholds, attacks significantly degraded detection performance while maintaining readability.
- **Genetic Optimization**: Achieved the largest performance drops against FastDetectGPT.
- **AUROC Trends**:
  
| Method        | DetectGPT | FastDetectGPT | DNA GPT  |
|---------------|-----------|---------------|----------|
| Original      | 0.73      | 0.9466        | 0.7582   |
| Random        | 0.2036    | 0.3033        | 0.1435   |
| Random - 0.2  | 0.4919    | 0.6795        | 0.3052   |
| Random - 0.4  | 0.4315    | 0.5437        | 0.2142   |
| Genetic       | 0.1292    | 0.3233        | 0.1754   |
| Genetic - 0.2 | 0.53      | 0.3500        | 0.2000   |
| Genetic - 0.4 | 0.57      | 0.2200        | 0.1000   |


For more detailed inferences, refer to the [report](./Documents/CSCI_544_Final_Report.pdf).

## Future Work
- Develop universal attack methods to optimize against all detectors.
- Explore improved metrics for text quality evaluation.
- Test attacks across diverse domain-specific datasets.

## References
- Zhouxing Shi et al. 2023. Red Teaming Language Model Detectors with Language Models.
- Eric Mitchell et al. 2023. DetectGPT: Zero-Shot Machine-Generated Text Detection using Probability Curvature.
- Guangsheng Bao et al. 2024. FastDetectGPT: Efficient Zero-Shot Detection of Machine-Generated Text.
- Xianjun Yang et al. 2023. DNA-GPT: Divergent N-Gram Analysis for Training-Free Detection of GPT-Generated Text.
