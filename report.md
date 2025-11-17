# DevOps Assignment Report

## Student Information
- Name: [Your Name]
- Project: ML-APP (Iris Classifier)
- Repository: [Your GitHub Repo Link]

---

## Task 1: Prepare the ML Project

### What I Did:
1. Downloaded the project ZIP file containing the ML application
2. Created a new GitHub repository called "ML-APP"
3. Pushed the project files to GitHub
4. Verified the repository structure

### Repository Structure:
```
ML-APP/
├── .idea/
├── models/
│   └── iris_classifier.pkl
├── src/
│   ├── __pycache__/
│   ├── data_loader.py
│   ├── model.py
│   ├── predict.py
│   ├── train.py
│   └── utils.py
├── tests/
│   └── test_model.py
├── .gitignore
├── confusion_matrix.png
├── feature_importance.png
├── README.md
└── requirements.txt
```

### Screenshot:
![Project Structure](screenshots/task1_structure.png)

---

## Task 2: Run the App Locally

### What I Did:
1. Opened VS Code terminal in the project directory
2. Created a Python virtual environment: `python -m venv .venv`
3. Activated the virtual environment: `.venv\Scripts\activate` (Windows)
4. Installed dependencies: `pip install -r requirements.txt`
5. Ran the training script: `python src/train.py`
6. Ran the prediction script: `python src/predict.py`

### Results:
- **Model Accuracy**: 96.67%
- **Training Set**: 120 samples
- **Test Set**: 30 samples
- **Features**: 4 (sepal length, sepal width, petal length, petal width)
- **Classes**: 3 (setosa, versicolor, virginica)

### How to Run Locally:
```bash
# 1. Create and activate virtual environment
python -m venv .venv
.venv\Scripts\activate  # Windows
# source .venv/bin/activate  # Linux/Mac

# 2. Install dependencies
pip install -r requirements.txt

# 3. Train the model
python src/train.py

# 4. Run predictions
python src/predict.py
```

### Screenshots:
![Virtual Environment Setup](screenshots/task2_venv.png)
![Training Output](screenshots/task2_training.png)
![Prediction Output](screenshots/task2_prediction.png)

---

## Task 3: Write Unit Tests
[To be completed]

## Task 4: Linting & Formatting
[To be completed]

## Task 5: GitHub Actions CI Workflow
[To be completed]

## Task 6: Containerise the App
[To be completed]

---

## Challenges and Solutions
- **Challenge**: [Describe any issues you faced]
- **Solution**: [How you resolved them]

## Conclusion
[Summary of what you learned]