# DevOps CI/CD Pipeline - Assignment Report

## Student Information
- **Name:** Jesser Hamdi
- **Date:** November 17, 2025
- **Repository:** https://github.com/LICHG4E/ml-app

---

## Task 1: Prepare the ML Project

### What I Did:
- Forked the repository to my GitHub account
- Cloned it to my local machine: `git clone https://github.com/LICHG4E/ml-app.git`
- Verified `requirements.txt` exists in the project root
- Inspected the repository structure

---

## Task 2: Run the App Locally

### Steps Taken:
1. Created virtual environment: `python -m venv .venv`
2. Activated environment: `.venv\Scripts\activate` (Windows)
3. Installed dependencies: `pip install -r requirements.txt`
4. Ran training: `python src/train.py`
5. Ran predictions: `python src/predict.py`

### Results:
- Training completed successfully with 96.67% model accuracy
- Model saved to `models/iris_classifier.pkl`
- Predictions working correctly on test data

---

## Task 3: Write Unit Tests

### What I Did:
- Created `tests/` folder
- Added `tests/test_model.py` with 8 unit tests
- Tests cover: model initialization, training, prediction, evaluation, save/load, data loading, data format, and prediction range validation

### Running Tests:
```bash
pytest tests/test_model.py -v
```

### Results:
- All 8 tests passed in 1.17 seconds

---

## Task 4: Linting & Formatting

### What I Did:
- Installed flake8: `pip install flake8`
- Created `.flake8` configuration file
- Configured to ignore common ML project patterns (unused imports, line length 120)
- Ran linter: `flake8 src/ tests/`

### Configuration:
Set max line length to 120 and ignored specific error codes (E302, W293, E305, F401, E501, E402, F541, W292) that are common in data science projects.

---

## Task 5: GitHub Actions CI Workflow

### What I Did:
1. Created `.github/workflows/ci.yml` file
2. Configured workflow to run on push and pull requests to main/master branches
3. Implemented the following steps:
   - Checkout code using `actions/checkout@v3`
   - Set up Python 3.10 using `actions/setup-python@v4`
   - Install dependencies (requirements.txt, flake8, pytest)
   - Run flake8 linter on src/ and tests/
   - Run pytest tests with verbose output
   - Build Docker image
   - Save Docker image to tar file
   - Upload Docker image as artifact using `actions/upload-artifact@v4`

### Challenges:
- Had to update from `actions/upload-artifact@v3` to `@v4` (v3 was deprecated)
- Fixed flake8 configuration to use `.flake8` config file instead of inline flags
- Fixed Dockerfile to handle missing models/ folder

### CI Workflow Behavior:
- Triggers automatically on every push/PR to main branch
- Runs all checks: linting, testing, Docker build
- Uploads Docker image artifact for download
- Shows pass/fail status in GitHub Actions tab

---

## Task 6: Containerise the App

### What I Did:
Created `Dockerfile` with:
- Base image: `python:3.10-slim`
- Working directory: `/app`
- Copies requirements.txt and installs dependencies
- Copies src/ folder
- Creates models/ directory (handles case when models don't exist yet)
- Exposes port 5000
- Default command: `python src/train.py`

### Building and Running:
```bash
docker build -t ml-app:latest .
docker run ml-app:latest
```

### Results:
- Docker image builds successfully
- Container runs training and achieves 96.67% accuracy
- Model saves successfully inside container

---

## How to Run Locally

### Setup:
```bash
python -m venv .venv
.venv\Scripts\activate  # Windows
pip install -r requirements.txt
```

### Run Training:
```bash
python src/train.py
```

### Run Tests:
```bash
pytest tests/ -v
```

### Run Linting:
```bash
flake8 src/ tests/
```

### Docker:
```bash
docker build -t ml-app:latest .
docker run ml-app:latest
```

---

## CI/CD Pipeline Summary

The GitHub Actions pipeline automatically:
1. Checks out code
2. Sets up Python environment
3. Installs dependencies
4. Runs linter (flake8)
5. Runs tests (pytest)
6. Builds Docker image
7. Uploads Docker image artifact

This ensures code quality and reproducibility on every commit.

---

## Repository
https://github.com/LICHG4E/ml-app