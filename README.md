# SchedulingTransformer

SchedulingTransformer is a full-stack university scheduling negotiation platform built around a Transformer-inspired multi-agent workflow. Instead of generating a full institutional timetable, the current project focuses on negotiating the best time slot between three actors: the room manager, the teacher, and the students.

The repository is organized into three connected parts:

- `FrontEnd`: React + Vite user interface
- `Backend`: Spring Boot API with PostgreSQL persistence
- `Transformer`: FastAPI + PyTorch negotiation engine

## Main Features

- User registration and login
- Profile update and password change
- Start a negotiation from the web interface
- Run a Transformer-based multi-round negotiation through the Python service
- Save negotiations for a specific user
- View negotiation history and negotiation details
- Sync saved negotiations into the `Mes emplois du temps` section
- Delete negotiations and related timetable entries

## Architecture

### Frontend

- React 18
- Vite
- React Router
- Tailwind CSS

The frontend talks to the backend at `http://localhost:8080/api`.

### Backend

- Spring Boot
- Spring Web + WebFlux
- Spring Data JPA
- PostgreSQL

The backend handles:

- authentication and user profile actions
- negotiation persistence
- negotiation history and detail retrieval
- timetable synchronization
- communication with the Transformer API at `http://localhost:8000`

### Transformer Service

- FastAPI
- PyTorch
- synthetic scenario generation
- satisfaction-based negotiation scoring

The Python service exposes endpoints such as:

- `GET /health`
- `POST /generate-scenario`
- `POST /negotiate`
- `POST /batch-negotiate`
- `GET /slots`
- `GET /config`
- `POST /explain-decision`

## Project Structure

```text
Schedular/
|-- FrontEnd/
|-- Backend/
|-- Transformer/
|-- RAPPORT_FINAL.md
`-- README.md
```

## Prerequisites

Install these before running the project:

- Node.js and npm
- Java 25
- Maven wrapper support or Maven
- Python 3.10+
- PostgreSQL

## Configuration

### Database

The backend is configured for PostgreSQL on:

- database: `scheduletransformer`
- port: `5432`

Current backend config is stored in `Backend/src/main/resources/application.properties`.

Important values already set in the project:

- backend port: `8080`
- transformer API URL: `http://localhost:8000`

You may want to update the database username and password locally before running the backend.

## How To Run

### 1. Start the Transformer API

```powershell
cd Transformer
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
python api\main.py
```

The API starts on `http://localhost:8000`.

### 2. Start the Spring Boot backend

```powershell
cd Backend
.\mvnw.cmd spring-boot:run
```

The backend starts on `http://localhost:8080`.

### 3. Start the frontend

```powershell
cd FrontEnd
npm install
npm run dev
```

The frontend runs on `http://localhost:5173`.

## Frontend Routes

The current application includes routes for:

- `/login`
- `/signup`
- `/`
- `/negociations`
- `/mes-negociations`
- `/mes-negociations/:negotiationId`
- `/emplois`
- `/profil`
- `/mot-de-passe`

## Training The Model

The repository already includes a trained weight file: `Transformer/best_model.pth`.

To retrain the model:

```powershell
cd Transformer
python training\train.py --regenerate-dataset
```

Optional arguments are available for dataset path, train size, validation size, and epochs.

## Current Scope

This project currently delivers a functional negotiation-based scheduling prototype. It does not yet generate a full university timetable with multi-course, multi-room, and institution-wide planning constraints.

## Related Document

For the final project analysis and scope review, see:

- `RAPPORT_FINAL.md`
