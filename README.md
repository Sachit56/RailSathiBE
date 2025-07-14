# Project Setup and Running with Docker

This guide explains how to set up and run the project using Docker and Docker Compose. The project consists of a PostgreSQL database and a Python web application served with Uvicorn.

## Prerequisites

- Docker
- Postgresql

## Project Structure

- `docker-compose.yml`: Defines the services (PostgreSQL database and web application).
- `Dockerfile`: Builds the Python application container.
- `.env`: Environment variables file for configuration (e.g., database credentials).
- `requirements.txt`: Lists Python dependencies for the application.
- `wait-for-it.sh`: Utility script to ensure the web service waits for the database to be ready.
- `main.py`: The main application file (assumed to contain the FastAPI/Uvicorn app).
- `others`: Other files

## Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone git@github.com:Sachit56/RailSathiBE.git
   cd RAILSATHIBE
   ```

2. **Create an `.env` File**
   Create a `.env` file in the project root with the following content:
   ```env
   POSTGRES_HOST=<your_host>
   POSTGRES_USER=<user>
   POSTGRES_PASSWORD=<password>
   POSTGRES_DB=<your_database>

   MAIL_USERNAME=<mail_username>
   MAIL_PASSWORD=<mail_password>
   MAIL_FROM=<mail_from>
   ```

3. **Build and Run the Application**
   Run the following command to build and start the services:
   ```bash
   docker compose up --build
   ```
   - The `--build` flag ensures the web service image is built from the `Dockerfile`.
   - This starts the PostgreSQL database (`db`) and the web application (`web`).
   - The web service waits for the database to be ready using `wait-for-it.sh` before starting Uvicorn.

4. **Access the Application**
   Once the services are running, the web application will be available at:
   ```
   http://localhost:8000
   ```

5. **Stopping the Application**
   To stop the running containers, press `Ctrl+C` in the terminal where `docker compose up` is running, or run:
   ```bash
   docker compose down
   ```
   This stops and removes the containers but retains the database data unless volumes are explicitly cleared.
