# ACEest Fitness & Gym - DevOps Assignment

## 📖 Project Overview
This is a sample Flask application for **ACEest Fitness & Gym**, built as part of a DevOps assignment.  
It demonstrates:
- Flask web app & REST APIs
- Unit testing with pytest
- Docker containerization
- Docker Compose for local development
- GitHub Actions CI pipelines (Python + Docker)
- Bonus: HTML templates + additional APIs

---

## 🚀 Features
- **Homepage** (`/`) → renders HTML template
- **View workouts** (`/workouts` GET) → JSON list of workouts
- **Add workout** (`/workouts` POST) → add new workout, returns `201 Created`
- **Health check** (`/health` GET) → returns `{ "status": "ok" }`

---

## 📂 Project Structure
aceest_fitness_app/
├── app.py # Flask application
├── requirements.txt # Dependencies
├── Dockerfile # App Dockerfile
├── Dockerfile.test # Test Dockerfile
├── docker-compose.yml # Docker Compose for app
├── docker-compose.test.yml # Docker Compose for tests
├── pytest.ini # Pytest config
├── templates/ # HTML templates
│ └── index.html
├── tests/ # Unit tests
│ └── test_app.py
└── .github/
└── workflows/
├── ci.yml # Python CI (pytest)
└── docker-ci.yml # Docker CI (pytest in container)

---

## 🛠️ Setup & Run

### 1. Clone the repository
git clone https://github.com/<your-username>/aceest_fitness_app.git
cd aceest_fitness_app

### 2. Run locally (with venv)
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
pytest # run tests
python app.py # run app

App will be available at:  
👉 http://127.0.0.1:5000/ (or http://127.0.0.1:5005/ if using Docker)

---

## 🐳 Run with Docker

### Build & Run app
docker-compose up --build

Visit 👉 http://127.0.0.1:5005/

### Run tests in Docker
docker build -f Dockerfile.test -t aceest_fitness_app_test .
docker run aceest_fitness_app_test

or using docker-compose:
docker-compose -f docker-compose.test.yml up --build

---

📡 API Usage Examples
Get workouts
curl http://127.0.0.1:5005/workouts
Add a new workout
curl -X POST http://127.0.0.1:5005/workouts \
  -H "Content-Type: application/json" \
  -d '{"id": 5, "name": "Lunges", "reps": "3 sets of 12"}'
Health check
curl http://127.0.0.1:5005/health

## ✅ CI/CD Workflows
- **ci.yml** → installs Python, runs pytest directly.  
- **docker-ci.yml** → builds Docker image and runs pytest inside it.  

Both run automatically on every **push** and **pull request** to `main`.

---



## 👩‍💻 Author
Sindhusri Janapati
2024TM93312
DevOps Assignment
