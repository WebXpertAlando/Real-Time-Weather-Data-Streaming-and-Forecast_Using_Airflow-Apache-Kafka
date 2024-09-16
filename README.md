Overview
========
Welcome to Astronomer! This project was generated after you ran 'astro dev init' using the Astronomer CLI. This readme describes the contents of the project, as well as how to run Apache Airflow on your local machine.

Project Contents
================
 # Hackathon Project 1: Real-Time Weather Data Streaming and Forecast System with Change Data Capture and Apache Kafka
 Create a real-time weather data streaming system that captures weather updates and
 forecasts from various sources, processes this data in real-time, and makes it available
 for analytics and visualization. Implement Change Data Capture (CDC) to handle
 updates efficiently and use Apache Kafka for real-time data streaming
 
# System Overview:
 ## 1. Data Ingestion from APIs:
 - WeatherAPIIntegration: Set up integrations with weather APIs to pull real-time
 weather data and forecasts. 
 ##Examples include:
 1. OpenWeatherMap
 2. Weatherstack
 3. ClimaCell.
 - Current Weather Data: Get current weather conditions such as
 temperature, humidity, wind speed, and weather descriptions.
- Forecast Data: Retrieve weather forecasts for various locations, including hourly and daily forecasts.
## 2. Change Data Capture (CDC) Setup:
 ● DatabaseSetup: Store historical weather data and forecasts in a relational
 database (e.g., PostgreSQL, MySQL).
 ● CDCTool(e.g., Debezium): Use Debezium to capture changes in the database,
 such as updates to weather records or forecasts.
 ● KafkaIntegration: Debezium will stream these changes to Kafka topics (e.g.,
 weather-updates, forecast-updates).
 ## 3. Real-Time Data Streaming with Apache Kafka:
 1. KafkaTopics: Create Kafka topics for different types of data: weather-updates: For real-time updates of current weather data. forecast-updates: For real-time updates of forecast data.
 2. KafkaProducers: Implement Kafka producers to push data from the weather
 APIs into Kafka topics.
 3. KafkaConsumers: Set up Kafka consumers to process and analyze data in
 real-time.
 ## 4. Stream Processing:
 1. Apache Kafka, Streamsor or Apache Flink: 
 Use Kafka Streams or Flink to process and transform the real-time data streams.
 2. DataEnrichment: Combine real-time weather updates with historical data
 for more context.
 3. Aggregation: Aggregate data to compute metrics such as average
 temperature, rainfall, or wind speed for specific regions or time periods.
 4. AnomalyDetection: Implement rules or machine learning models to detect
 unusual weather patterns or forecast anomalies.
 ## 5. Data Storage and Warehousing:
 a) DataLake: Store raw and processed data in a data lake (e.g., Amazon S3 with
 Apache Hudi or Delta Lake) for long-term storage and analysis.
 b) DataWarehouse: Load aggregated and transformed data into a data warehouse
 (e.g., Amazon Redshift, Snowflake) for analytical querying and reporting.
## 6. Visualization and Dashboarding:
 1. Real-Time Dashboards: Create dashboards to visualize key weather metrics and
 forecasts in real-time.
 2. WeatherDashboard: Display current weather conditions, alerts, and
 historical weather data.
 3. Forecast Dashboard: Show forecast trends, upcoming weather conditions,
 and alert thresholds.
 4. Alerting: Set up alerts based on specific conditions (e.g., severe weather
 warnings, temperature extremes) using tools like Grafana or Kibana.

Deploy Your Project Locally
===========================

1. Start Airflow on your local machine by running 'astro dev start'.

This command will spin up 4 Docker containers on your machine, each for a different Airflow component:

- Postgres: Airflow's Metadata Database
- Webserver: The Airflow component responsible for rendering the Airflow UI
- Scheduler: The Airflow component responsible for monitoring and triggering tasks
- Triggerer: The Airflow component responsible for triggering deferred tasks

2. Verify that all 4 Docker containers were created by running 'docker ps'.

Note: Running 'astro dev start' will start your project with the Airflow Webserver exposed at port 8080 and Postgres exposed at port 5432. If you already have either of those ports allocated, you can either [stop your existing Docker containers or change the port](https://docs.astronomer.io/astro/test-and-troubleshoot-locally#ports-are-not-available).

3. Access the Airflow UI for your local Airflow project. To do so, go to http://localhost:8080/ and log in with 'admin' for both your Username and Password.

You should also be able to access your Postgres Database at 'localhost:5432/postgres'.
