# Workflow CI - Breast Cancer ML Training Pipeline

Repository ini berisi Workflow CI untuk melakukan **retraining model Machine Learning** secara otomatis menggunakan **MLflow Project** pada **GitHub Actions**.

## Struktur Repository

```
Workflow-CI/
├── .github/
│   └── workflows/
│       └── ci.yml                    # GitHub Actions workflow
├── MLProject/
│   ├── modelling.py                  # Script training model
│   ├── conda.yaml                    # Conda environment
│   └── MLProject                     # MLflow Project config
├── breast_cancer_preprocessing/      # Dataset preprocessing
│   ├── X_train.csv
│   ├── X_test.csv
│   ├── y_train.csv
│   ├── y_test.csv
│   ├── metadata.json
│   └── scaler_info.json
├── DOCKERHUB_LINK.md                 # Tautan Docker Hub
├── README.md
└── .gitignore
```

## Workflow CI

Pipeline CI berjalan otomatis ketika ada perubahan pada folder `MLProject/` atau `breast_cancer_preprocessing/`, atau dapat di-trigger secara manual melalui `workflow_dispatch`.

### Steps:
1. **Set up job** - Setup runner Ubuntu
2. **Run actions/checkout@v3** - Checkout repository
3. **Set up Python 3.12.7** - Setup Python environment
4. **Check Env** - Verifikasi environment
5. **Install dependencies** - Install MLflow dan dependencies
6. **Run mlflow project** - Jalankan MLflow Project untuk retraining model secara otomatis
7. **Get latest MLflow run_id** - Ambil run ID dari hasil training

## Model

- **Dataset**: Breast Cancer Wisconsin (Binary Classification)
- **Algorithm**: Random Forest Classifier
- **Framework**: MLflow + Scikit-learn
- **Tracking**: DagsHub MLflow

## Tautan Docker Hub

🐳 [Docker Hub - muhammadghazi/breast-cancer-model](https://hub.docker.com/r/muhammadghazi/breast-cancer-model)

## Cara Menjalankan

### Manual Trigger
Buka tab **Actions** di GitHub → pilih workflow **ML Training CI Pipeline** → klik **Run workflow**.

### Otomatis
Push perubahan ke folder `MLProject/` atau `breast_cancer_preprocessing/` di branch `main`.

## Author
Muhammad Ghazi Saputra (gaji)
