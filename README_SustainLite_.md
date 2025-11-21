# SustainLite: Lightweight AI Recommendation System for Sustainable Construction

## Overview

SustainLite is a lightweight AI-based recommendation system designed to optimize construction project resources in Southeast Asia. It predicts sustainability performance based on project-level data (budget, duration, and resource ratios) and national indicators (CO₂ per capita, renewable energy share, GDP per capita). The system then recommends feasible adjustments in material, labor, and energy ratios to enhance sustainability with minimal cost trade-offs.

Developed as part of academic research and course project at the University of Florida College of Design, Construction & Planning, this project demonstrates how Small Language Models (SLM) and open-source AI workflows can support sustainable decision-making, even within resource-constrained environments such as developing countries. The implementation runs fully on Google Colab within <20 minutes and <500 MB RAM, using open-source Python libraries (`scikit-learn`, `pandas`, `scipy`, `matplotlib`).

## Authors

**Syarifah Ismailiyah Al Athas (Lya Alatas)**  
PhD Student, School of Architecture / Rinker School of Construction Management, University of Florida  
[LinkedIn](https://www.linkedin.com/in/syarifah-ismailiyah-al-athas-4031964b/) | [https://scholar.google.com/citations?hl=en&user=uPGy8DAAAAAJ) | [GitHub](https://github.com/SyarifahIA)

Supervising Faculty: Dr. Vivian Wong, for URP 6931 AI in Built Environment Course Fall 2025

## Motivation

Southeast Asia’s rapid construction growth is challenged by inefficient resource use and rising environmental costs. Many small-to-medium construction firms lack access to advanced analytics. SustainLite bridges this gap by using open data (from Kaggle) and lightweight models to provide practical sustainability recommendations that balance cost and performance. It exemplifies the vision of AI for equitable sustainability.

## Example Input and Output

### Input Dataset Preview (`df.head()`)

![Input CSV Preview](Screenshot%20of%20Input.png)

### Model Output Preview (`SustainLite_Output_Example.csv`)

![Output CSV Preview](Output%20sample.png)


## Repository Structure

```
SustainLite_Colab_Notebook.ipynb    # Main notebook (Google Colab ready)
SustainLite_Progress_Report.docx     # Original progress report (academic format)
README_SustainLite.md                # This README file
data/
	Construction_Dataset.csv         # From Programmer3 (Kaggle)
	sea_energy.csv                   # From Nguyen (Kaggle)
outputs/
	sustainlite_recommendations_sample.csv
	sustainlite_metrics.txt
```

## How to Run in Google Colab

1. Open **SustainLite_Colab_Notebook.ipynb** in [Google Colab](https://colab.research.google.com/).  
2. In the setup cell, choose one option:
   - Option A: Upload `kaggle.json` API key → the notebook downloads both datasets automatically.  
   - Option B: Manually upload `Construction_Dataset.csv` and `sea_energy.csv` to the `/data` folder.  
3. Run all cells sequentially.  
4. Check `/outputs/` for metrics and sample recommendations.

## Model Workflow

1. Data Preparation: Merge project-level and country-level datasets via country key.  
2. Feature Engineering: Normalize ratios (Material, Labor, Energy) to sum to 1.  
3. Baseline Models: Train Linear Regression and Random Forest for sustainability prediction.  
4. Evaluation Metrics:  
   - Mean Absolute Error (MAE)  
   - Mean Squared Error (MSE) 
   - Sustainability–Cost Trade-off Index (SCTI = ΔSustainability / ΔCost)  
5. Optimization: `scipy.optimize.minimize` (SLSQP) finds feasible ratio adjustments maximizing sustainability with budget constraint.  
6. Visualization: Plot actual vs predicted sustainability and export recommendations CSV.

## Dependencies

- Python 3.10+  
- scikit-learn  
- pandas, numpy  
- scipy  
- matplotlib  
- shap (optional for explainability)  

Install in Colab automatically via:
```bash
!pip install scikit-learn pandas numpy scipy matplotlib shap
```

## Key Results (Expected)

| Model | MAE | MSE | Notes |
|--------|-----|----|-------|
| Linear Regression | < 10 | ~0.60 | interpretable baseline |
| Random Forest | < 6 | >0.75 | robust nonlinear performance |
| Oracle (Optimization) | MAE < 5 | upper bound | serves as reference for improvement |

## Datasets

- Programmer3 (2023). Construction Project Resource Dataset. Kaggle. [Link](https://www.kaggle.com/datasets/programmer3/construction-project-resource-dataset)  
- Nguyen, D. L. (2023). Sustainability and Energy in Southeast Asia. Kaggle. [Link](https://www.kaggle.com/code/dieplinhnguyen/sustainability-energy-in-southest-asia)

## Citations

Darko, A., Chan, A. P. C., Huo, X., & Owusu-Manu, D. G. (2020). Artificial intelligence in the AEC industry: A review of research trends and future directions. *Automation in Construction*, 118, 103311.  
Hwang, B. G., Zhao, X., & Ng, S. Y. (2017). Identifying the critical factors affecting schedule performance of public housing projects. *International Journal of Project Management*, 35(4), 797–807.  
Zhang, L., Li, Y., & Chen, X. (2022). Multi-objective optimization of construction project energy consumption using machine learning and linear programming. *Journal of Cleaner Production*, 357, 131837.

## License

Open-source for educational and research use.  
© November 06, 2025, 1st Milestone Progress 
Updated November 10, 2025, feedback on input-output