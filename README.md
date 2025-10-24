# BGSIT Hackathon Project Template

Welcome to the BGSIT Hackathon! This repository provides a standardized project structure that all participants should follow to ensure consistency and facilitate evaluation.

## 📁 Project Structure

```
BGSIT_Hackathon/
├── Notebooks/
│   ├── 01-exploratory_data_analysis.ipynb
│   ├── 02-model_development.ipynb
│   └── 03-dummy_for_testing.ipynb
├── README.md
├── data/
│   ├── processed/
│   │   └── bgsit_processed.csv
│   └── raw/
│       └── bgsit_raw_data.csv
├── extras/
│   └── docs.docx
├── model_artifacts/
│   └── model.pkl
├── submissions/
│   └── teamid-teamname.csv
└── test/
```

## 📋 Directory Guidelines

### 📓 `Notebooks/`
This folder contains Jupyter notebooks for your data science workflow:
- **`01-exploratory_data_analysis.ipynb`**: Initial data exploration, visualization, and insights
- **`02-model_development.ipynb`**: Model building, training, and evaluation
- **`03-dummy_for_testing.ipynb`**: Testing and validation scripts

**Important**: Follow the numerical naming convention for proper workflow organization.

### 📊 `data/`
Contains all dataset files:
- **`raw/`**: Original, unmodified datasets
  - `bgsit_raw_data.csv`: The provided raw dataset
- **`processed/`**: Cleaned and preprocessed data files
  - `bgsit_processed.csv`: Your processed dataset ready for modeling

### 🏗️ `model_artifacts/`
Store your trained models and related files:
- `model.pkl`: Your final trained model (pickle format)
- Additional model files, scalers, encoders, etc.

### 📤 `submissions/`
Final submission files:
- **`teamid-teamname.csv`**: Your prediction file for evaluation
- Format: Replace `teamid` with your assigned team ID and `teamname` with your team name

### 📁 `extras/`
Additional documentation and supplementary files:
- `docs.docx`: Project documentation, methodology, insights
- Any additional supporting files

### 🧪 `test/`
Testing scripts and validation code (optional)

## 🚀 Getting Started

1. **Clone this repository** to your local environment
2. **Install required dependencies** (create a `requirements.txt` if needed)
3. **Follow the notebook sequence**: Start with `01-exploratory_data_analysis.ipynb`
4. **Maintain the folder structure** throughout your project
5. **Document your work** in the notebooks with clear markdown explanations

## 📝 Submission Requirements

- Ensure your final model is saved in `model_artifacts/model.pkl`
- Submit predictions in `submissions/teamid-teamname.csv`
- Complete all three notebooks with proper documentation
- Include a brief methodology summary in `extras/docs.docx`

## ⚠️ Important Notes

- **DO NOT** modify the basic folder structure
- Keep file naming conventions consistent
- Ensure your code is reproducible
- Comment your code thoroughly
- Include data preprocessing steps in the processed folder

## 🏆 Evaluation Criteria

Your submission will be evaluated based on:
- Code quality and documentation
- Model performance
- Methodology and approach
- Adherence to project structure
- Reproducibility of results

---

**Good luck with the hackathon! 🎯**

For any questions or clarifications, please contact the organizing team.