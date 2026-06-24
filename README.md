# Home Credit Predictor

A machine learning-based web application that predicts home credit approval decisions. This project uses XGBoost and scikit-learn to classify loan applications as good or bad, with both single and batch prediction capabilities.

## 📋 Table of Contents

- [Features](#features)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Project Pipeline](#project-pipeline)
- [Testing](#testing)
- [Model Information](#model-information)
- [Contributing](#contributing)

## ✨ Features

- **Single Prediction**: Make predictions through a user-friendly web form
- **Batch Predictions**: Upload CSV files for bulk predictions
- **Data Preprocessing**: Automated data cleaning, scaling, and encoding
- **Feature Selection**: Uses top features for optimal model performance
- **RESTful API**: Flask-based web service
- **Model Persistence**: Serialized models and preprocessors
- **Comprehensive Logging**: Track execution flow and errors

## 📁 Project Structure

```
home-credit-predictor/
├── app.py                          # Flask application entry point
├── requirements.txt                # Python dependencies
├── config/
│   └── model.yaml                  # Model configuration
├── data/
│   ├── application_train.csv       # Training dataset
│   └── application_test.csv        # Test dataset
├── artifacts/
│   ├── model.pkl                   # Trained XGBoost model
│   ├── preprocessor.pkl            # Data preprocessor
│   ├── top_features.json           # Top features list
│   ├── train_processed.csv         # Processed training data
│   └── train.npy                   # NumPy format training data
├── src/
│   ├── components/
│   │   ├── data_ingestion.py       # Data loading
│   │   ├── data_transformation.py  # Data preprocessing
│   │   └── model_trainer.py        # Model training
│   ├── pipeline/
│   │   ├── train_pipeline.py       # Training pipeline
│   │   └── predict_pipeline.py     # Prediction pipeline
│   ├── utils/
│   │   ├── main_utils.py           # Utility functions
│   │   └── extract_top_features.py # Feature extraction
│   ├── constant/
│   │   └── __init__.py             # Constants definition
│   ├── exception.py                # Custom exceptions
│   └── logger.py                   # Logging configuration
├── templates/
│   ├── form.html                   # Single prediction form
│   └── upload.html                 # Batch prediction interface
├── tests/
│   ├── test_data_ingestion.py
│   ├── test_data_transformation.py
│   ├── test_model_trainer.py
│   ├── test_predict_pipeline.py
│   ├── test_train_pipeline.py
│   └── test_extract_top_features.py
├── notebooks/
│   └── home_credit.ipynb           # Exploratory analysis notebook
└── logs/                           # Application logs
```

## 🚀 Installation

### Prerequisites
- Python 3.8+
- pip or conda

### Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd home-credit-predictor
   ```

2. **Create virtual environment**
   ```bash
   python -m venv myvenv
   source myvenv/Scripts/activate  # On Windows
   # or
   source myvenv/bin/activate      # On Linux/Mac
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## ⚙️ Configuration

### Model Configuration

Edit `config/model.yaml` to customize:
- Model hyperparameters
- Feature selections
- Training parameters

### Constants

Modify `src/constant/__init__.py` for:
- Data paths
- Target column name
- Model file names

## 📖 Usage

### Run Flask Application

```bash
python app.py
```

The application will be available at `http://127.0.0.1:5000`

### Single Prediction
1. Navigate to the home page
2. Fill in the required features
3. Click "Predict" to get the result

### Batch Predictions
1. Go to `/batch_predict` endpoint
2. Upload a CSV file with feature columns
3. Download the predictions

### Command Line Training

```bash
python -m src.pipeline.train_pipeline
```

### Command Line Prediction

```bash
python tests/test_predict_pipeline.py
```

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET, POST | `/` | Single prediction form |
| GET, POST | `/batch_predict` | Batch prediction upload |
| GET | `/download/<filename>` | Download prediction results |

## 🔄 Project Pipeline

### Training Pipeline
1. **Data Ingestion** → Load raw CSV files
2. **Data Transformation** → Clean, encode, and scale features
3. **Model Training** → Train XGBoost classifier
4. **Feature Extraction** → Extract and save top features
5. **Model Serialization** → Save model and preprocessor

### Prediction Pipeline
1. **Load Artifacts** → Load model, preprocessor, and features
2. **Input Preprocessing** → Apply same transformations as training
3. **Prediction** → Generate predictions
4. **Output Mapping** → Map to labels (good/bad)
5. **Result Saving** → Save predictions to CSV

## 🧪 Testing

Run all tests:
```bash
python -m pytest tests/
```

Run specific test:
```bash
python tests/test_predict_pipeline.py
```

### Test Coverage
- Data ingestion
- Data transformation
- Model training
- Prediction pipeline
- Feature extraction

## 📊 Model Information

- **Algorithm**: XGBoost Classifier
- **Target**: Binary classification (Good/Bad)
- **Features**: Top features automatically selected
- **Performance**: Metrics saved in training logs

### Key Metrics
- Train/Test accuracy
- Feature importance
- Cross-validation scores

## 📦 Dependencies

- **Flask** (3.1.1) - Web framework
- **pandas** (2.3.0) - Data manipulation
- **NumPy** (2.3.0) - Numerical computing
- **scikit-learn** (1.7.0) - ML algorithms
- **XGBoost** (3.0.2) - Gradient boosting
- **scipy** (1.15.3) - Scientific computing
- **PyYAML** (6.0.2) - Configuration management
- **gunicorn** (23.0.0) - Production server

## 🛠️ Troubleshooting

### Common Issues

**"Module not found" error**
- Ensure virtual environment is activated
- Reinstall dependencies: `pip install -r requirements.txt`

**Model/Preprocessor not found**
- Run training pipeline first to generate artifacts
- Check artifact directory permissions

**Port 5000 already in use**
- Change port in app.py or kill process using the port

## 📝 Logging

Logs are stored in the `logs/` directory with:
- Training logs
- Prediction logs
- Error logs

Check logs for debugging: `logs/app.log`

## 🤝 Contributing

1. Create a feature branch
2. Make your changes
3. Run tests to ensure functionality
4. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see LICENSE file for details.

## 👥 Author

Home Credit Predictor Team

## 📞 Support

For issues or questions, please create an issue in the repository.

---

**Last Updated**: 2026-06-24