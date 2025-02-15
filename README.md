# AirQualityFlow

**AirQualityFlow** is an open-source data pipeline for collecting, storing, processing, and visualizing real-time air quality data. The project collects data from the OpenAQ API and provides real-time data access through a RESTful API, along with an interactive dashboard for data visualization.

## Demo

You can explore a live version of the project here: **WORK**.

## Objective

AirQualityFlow provides a comprehensive solution for exploring air quality data. Users can:
- View the levels of different pollutants (PM2.5, PM10, Ozone, etc.).
- Track the evolution of air quality in cities or regions.
- Retrieve detailed statistics about air quality, such as average pollutant levels over a time period.

The project is open-source and freely available on GitHub.

## Features

- **Data Collection**: Collects real-time air quality data from the OpenAQ API.
- **Data Storage**: Raw data is stored in **MinIO** (S3-compatible storage), while cleaned data is stored in **PostgreSQL**.
- **REST API**: Provides access to real-time and historical data via **FastAPI**.
- **Data Visualization**: An interactive **Streamlit** dashboard for exploring and visualizing data.
- **Containerized Deployment**: The project is containerized using **Docker** for easy local or cloud deployment.

## Project Architecture

### 1. **Data Collection**
   - The OpenAQ API is queried to collect air quality data (PM2.5, PM10, Ozone, etc.).
   - Data collection happens automatically every hour using **Apache Airflow**.

### 2. **Raw Data Archival**
   - Retrieved data is stored in **MinIO** (S3-compatible) as JSON or CSV files for archival.

### 3. **Data Processing**
   - The raw data is cleaned and transformed using **Pandas**.
   - Cleaned data is stored in a **PostgreSQL** database for further analysis.

### 4. **API Access**
   - A **FastAPI** app exposes several API endpoints to access the data:
     - **/air-quality/{city}**: Retrieves air quality data for a specific city.
     - **/air-quality/real-time**: Fetches real-time air quality data.
     - **/air-quality/statistics**: Retrieves statistics (e.g., average PM2.5 levels over a given period).

### 5. **Data Visualization**
   - An interactive **Streamlit** dashboard allows users to:
     - View air quality evolution over time.
     - Compare different pollutants in a given region.
     - Filter data by period or region.

### 6. **Deployment**
   - The project is **containerized** with **Docker** for easy deployment locally or on cloud services (e.g., **AWS**, **Heroku**, or **Google Cloud**).
   - All services (Airflow, PostgreSQL, MinIO, FastAPI, Streamlit) are managed using **Docker Compose**.

## Technologies Used

- **Apache Airflow**: For orchestrating data collection and processing.
- **PostgreSQL**: For storing cleaned data.
- **MinIO**: For archiving raw data in S3-compatible storage.
- **FastAPI**: For building the RESTful API to access data.
- **Streamlit**: For creating interactive data visualizations.
- **Docker**: For containerizing the application for easy deployment.

## Deployment

### Prerequisites

1. **Docker** and **Docker Compose** must be installed on your machine.
2. **Python 3.8+** is required for dependencies.

### Install and Run Locally

1. Clone the repository:

    ```bash
    git clone https://github.com/S-MTZG/AirQualityFlow.git
    cd AirQualityFlow
    ```

2. Build and start the Docker containers:

    ```bash
    docker-compose up --build
    ```

    This will build all services (Airflow, PostgreSQL, MinIO, FastAPI, Streamlit) and start them locally.

3. Once the services are up, you can access:
   - **Streamlit dashboard**: `http://localhost:8501`
   - **FastAPI API**: `http://localhost:8000`

### Usage

- The **Streamlit** dashboard will allow you to visualize and explore air quality data interactively.
- You can also use the **FastAPI** API to retrieve real-time or historical data programmatically.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Feel free to contribute by submitting **issues** or **pull requests**. Contributions are welcome to improve the functionality and extend the project.

---

