# Fast-API Server - Hands-on ML Model Serving

This repository demonstrates a **FastAPI server** for serving ML models with Docker and Docker Compose support. Ideal for hands-on learning and experimentation.

---

## **Repository Overview**

- Build a **REST API** using FastAPI.
- Serve **ML model predictions** via API endpoints.
- Containerize with **Docker**.
- Orchestrate with **Docker Compose**.
- Easy deployment and testing using Docker Hub images.

---

## **Project Structure**

Fast-APi-server/
├─ app.py # FastAPI main app
├─ requirements.txt # Python dependencies
├─ model/ # ML model and predict scripts
│ └─ predict.py
├─ config/ # Configuration files
├─ schema/ # Pydantic request/response schemas
├─ Dockerfile # Dockerfile to build the image
├─ docker-compose.yml # Compose file for local deployment
└─ venv/ # Optional local virtual environment


---

## **Local Setup**

### 1. Clone the repository

```bash
git clone https://github.com/omumarvaishya005/Fast-APi-server.git
cd Fast-APi-server
```

### 2. Create a virtual environment (optional)
```bash
python3 -m venv venv
source venv/bin/activate  # Linux/Mac
# .\venv\Scripts\activate # Windows
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Run FastAPI server locally
```bash
uvicorn app:app --reload --port 8010

    API docs: http://127.0.0.1:8010/docs

    Health check: http://127.0.0.1:8010/health
```

## **Docker Setup**

### 1. Build the Docker image
```bash
docker build -t fast-api:latest .
```


### 2. Run the container
```bash
docker run -d -p 8010:8010 --name fast-api-server fast-api:latest
```

### 3. Push to Docker Hub
```bash
docker tag fast-api:latest omvaishya/fast-api:v1.0.0
docker login
docker push omvaishya/fast-api:v1.0.0
```

### 4. Pull from Docker Hub
```bash
docker pull omvaishya/fast-api:v1.0.0
docker run -d -p 8010:8010 omvaishya/fast-api:v1.0.0
```


## **Docker Compose Setup**

You can use Docker Compose to run your FastAPI server with just one command.
docker-compose.yml Example

version: "3.8"
```bash
services:
  fastapi:
    image: omvaishya/fast-api:v1.0.0
    container_name: fast-api-server
    ports:
      - "8010:8010"
    restart: unless-stopped
```

## **Run with Docker Compose**
```bash
docker-compose up -d

    Access the API at: http://localhost:8010

    Stop the server: docker-compose down
```

## **API Endpoints & Example Requests**
## 1. Health Check
```bash
curl http://localhost:8010/health

Response:

{"status": "healthy"}
```

### 2. Predict Endpoint
```bash
POST /predict
```

## **GitHub Repository Setup**

Add your repository:

    git remote add origin https://github.com/omumarvaishya005/Fast-APi-server.git

Push your changes:

    git add .
    git commit -m "Initial commit - FastAPI ML server"
    git push -u origin main

Contributing

    Fork the repository

    Create a new branch: git checkout -b feature-name

    Commit your changes: git commit -m "Add new feature"

    Push your branch: git push origin feature-name

    Create a pull request

License

MIT License