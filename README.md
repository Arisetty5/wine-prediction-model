# 🍷 Wine Prediction with DVC (Data Version Control)

A demonstration project showcasing how to use DVC (Data Version Control) for managing large datasets in Machine Learning workflows.

## 📋 Table of Contents
- [Overview](#overview)
- [Why DVC?](#why-dvc)
- [Prerequisites](#prerequisites)
- [Setup Instructions](#setup-instructions)
- [Project Structure](#project-structure)
- [DVC Workflow](#dvc-workflow)
- [Usage](#usage)
- [Key Learnings](#key-learnings)
- [Technologies Used](#technologies-used)

## 🎯 Overview

This project demonstrates how DVC solves the challenge of versioning large datasets that are too heavy for Git. Using a wine dataset, we showcase how to:
- Store large datasets in remote storage (AWS S3)
- Track dataset versions using lightweight metadata files
- Enable seamless team collaboration on ML projects

## 🤔 Why DVC?

Traditional Git struggles with large datasets because:
- Large files bloat repository size
- Git is not optimized for binary data
- Cloning and pulling becomes slow and inefficient

**DVC solves this by:**
- Storing actual data in remote storage (S3, GCS, Azure, etc.)
- Keeping only lightweight `.dvc` metadata files in Git
- Generating unique checksums for data versioning
- Enabling reproducible ML pipelines

## ✅ Prerequisites

- Python 3.7+
- Git installed
- AWS Account (for S3 storage)
- Basic understanding of Git and command line

## 🚀 Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/wine-prediction-dvc.git
cd wine-prediction-dvc
```

### 2. Create Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Initialize DVC
```bash
dvc init
```

### 5. Configure Remote Storage
```bash
dvc remote add -d myremote s3://your-bucket-name/path
```

### 6. Pull Data from Remote
```bash
dvc pull
```

## 📁 Project Structure
```
wine-prediction-dvc/
│
├── data/
│   ├── wine-sample.csv          # Actual dataset (not tracked by Git)
│   └── wine-sample.csv.dvc      # DVC metadata file (tracked by Git)
│
├── .dvc/
│   ├── config                   # DVC configuration
│   └── .gitignore              
│
├── venv/                        # Virtual environment
├── .gitignore
├── requirements.txt
└── README.md
```

## 🔄 DVC Workflow

### Adding/Updating Dataset

1. **Add new or modified data to DVC:**
```bash
dvc add data/wine-sample.csv
```
This creates/updates `wine-sample.csv.dvc` with a new checksum.

2. **Push data to remote storage:**
```bash
dvc push
```

3. **Commit DVC metadata to Git:**
```bash
git add data/wine-sample.csv.dvc data/.gitignore
git commit -m "Update wine dataset"
git push
```

### Pulling Latest Dataset
```bash
git pull
dvc pull
```

## 💻 Usage

### For New Team Members

1. Clone the repository
2. Set up virtual environment and install dependencies
3. Run `dvc pull` to fetch the actual dataset from remote storage
4. Start working on the project!

### Checking Remote Configuration
```bash
dvc remote list
```

### Checking DVC Status
```bash
dvc status
```

## 🎓 Key Learnings

- ✅ DVC separates data storage from version control
- ✅ Large datasets stay in cloud storage while metadata stays in Git
- ✅ Every data change generates a unique checksum for proper tracking
- ✅ Team collaboration becomes seamless with synchronized data versions
- ✅ Git repositories remain lightweight and fast
- ✅ Data pipelines become reproducible

## 🛠️ Technologies Used

- **Python** - Programming language
- **DVC** - Data Version Control
- **Git** - Source code version control
- **AWS S3** - Remote storage for datasets
- **Virtual Environment** - Dependency isolation

## 📝 Requirements
```txt
dvc==3.x.x
dvc[s3]==3.x.x
pandas
numpy
scikit-learn
```
