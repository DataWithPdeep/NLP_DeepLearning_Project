🧠 NLP Deep Learning Text Classification API

An end-to-end NLP text classification project built with
TensorFlow/Keras and deployed as a FastAPI inference service.
The project preprocesses text, converts it into token sequences, and
predicts one of six emotions using a trained BiGRU model.

🚀 Features

🧠 Deep learning-based NLP text classification

🔤 Tokenizer-based text preprocessing

🧹 Text cleaning and normalization

🔥 BiGRU model for emotion classification

🧩 TensorFlow/Keras model loading

⚡ FastAPI REST API for real-time inference

📊 Emotion confidence scores and probability distribution

❤️ Emotion-specific emoji mapping

🩺 Health-check endpoint

🌐 Static web interface served through FastAPI

🔒 Input validation using Pydantic

🚀 Uvicorn production-style ASGI server

🎯 Emotion Classes

The model predicts six emotion categories:

😢 Sadness

😄 Joy

❤️ Love

😠 Anger

😨 Fear

😲 Surprise

🏗️ Architecture

                 ┌──────────────────┐
                 │      User        │
                 │   Text Input     │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │    FastAPI       │
                 │   /predict      │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │ Text Preprocessing│
                 │ Lowercase / Clean │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │    Tokenizer     │
                 │ Text → Sequences │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │  Padding         │
                 │ Max Length = 50  │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │   BiGRU Model    │
                 │ TensorFlow/Keras │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │ Emotion +        │
                 │ Confidence Score │
                 └──────────────────┘

🔄 Prediction Pipeline

The /predict endpoint follows this workflow:

Raw Text
   ↓
Lowercase
   ↓
Remove Apostrophes
   ↓
Remove Special Characters
   ↓
Normalize Spaces
   ↓
Tokenizer
   ↓
Padding / Truncation
   ↓
BiGRU Model
   ↓
Emotion Probabilities
   ↓
Predicted Emotion + Confidence

The application uses a maximum sequence length of 50 tokens for
inference.

🧠 Model

The repository contains a trained BiGRU TensorFlow/Keras model
stored in the Artifacts directory.

The API loads:

Artifacts/BiGRU_Model.keras
Artifacts/tokenizer.pkl

The model output is converted into probabilities for the six emotion
labels and the highest-probability class is returned as the predicted
emotion.

🌐 API Endpoints

GET /

Serves the static web interface.

GET /health

Returns server health and model-loading status.

Example response:

{
  "status": "Server is running",
  "model_loaded": true
}

POST /predict

Predicts the emotion of the submitted text.

Example request:

{
  "text": "I feel so happy and excited"
}

Example response:

{
  "text": "I feel so happy and excited",
  "predicted_emotion": "joy",
  "confidence": 0.95,
  "all_probabilites": {
    "sadness": 0.01,
    "joy": 0.95,
    "love": 0.01,
    "anger": 0.01,
    "fear": 0.01,
    "surprise": 0.01
  }
}

🛠️ Tech Stack

Machine Learning / Deep Learning

Python

TensorFlow

Keras

NumPy

BiGRU

NLP

Text Classification

NLP

Tokenization

Text preprocessing

Sequence padding

Sequence truncation

Emotion classification

Backend / API

FastAPI

Uvicorn

Pydantic

REST API

CORS

📁 Project Structure

NLP_DeepLearning_Project/
│
├── Artifacts/
│   ├── BiGRU_Model.keras       # Trained BiGRU model
│   └── tokenizer.pkl           # Fitted tokenizer
│
├── static/
│   └── index.html              # Web interface
│
├── final_clean.ipynb           # NLP model development/training notebook
├── main.py                     # FastAPI inference application
├── requirements.txt            # Python dependencies
└── README.md

⚙️ Installation

1. Clone the repository

git clone https://github.com/DataWithPdeep/NLP_DeepLearning_Project.git
cd NLP_DeepLearning_Project

2. Create a virtual environment

python -m venv venv

Activate on Windows:

.\venv\Scripts\Activate.ps1

3. Install dependencies

pip install -r requirements.txt

The repository currently pins the main runtime dependencies including
FastAPI, Uvicorn, Pydantic, TensorFlow CPU, NumPy, and h5py.

▶️ Run the API

Start the FastAPI application with Uvicorn:

uvicorn main:app --reload

The API will be available at:

http://127.0.0.1:8000

📚 API Documentation

FastAPI automatically provides interactive API documentation.

Swagger UI:

http://127.0.0.1:8000/docs

ReDoc:

http://127.0.0.1:8000/redoc

🧪 Example cURL Request

curl -X POST "http://127.0.0.1:8000/predict" \
-H "Content-Type: application/json" \
-d "{\"text\":\"I am very happy today\"}"

🔐 Input Validation

The API validates incoming text using Pydantic.

Minimum length: 1 character

Maximum length: 2000 characters

This helps prevent invalid requests from reaching the inference
pipeline.

❤️ Response

The prediction response contains:

Original input text

Predicted emotion

Confidence score

Probability distribution for all emotion classes

This makes the API useful not only for classification but also for
understanding model confidence.

📌 Project Highlights

End-to-end NLP project from model development to API deployment

Deep learning-based emotion classification using BiGRU

Reusable tokenizer and trained model artifacts

Production-style FastAPI inference layer

Health monitoring endpoint

Structured request/response schemas

Real-time prediction API

🔗 Repository

GitHub: https://github.com/DataWithPdeep/NLP_DeepLearning_Project

👨‍💻 Author

Pradeep Singh

GitHub: https://github.com/DataWithPdeep

Kaggle: https://www.kaggle.com/psrana344

📄 License

This project is intended for educational and portfolio purposes.
