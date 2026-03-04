# The project

ChillChain is an IoT platform for refrigerated transport sharing, combining a logistics marketplace for shipment booking with real-time cold chain monitoring and ML-based anomaly detection.

The system is organised as in the image

![Architecture](images/architettura_IoT.png)

A refrigerated vehicle equipped with sensors streams telemetry data via MQTT to a broker. Two Python microservices handle the data pipeline: the Fridge Streamer simulates sensor readings from CSV datasets and publishes them on MQTT, while the Anomaly Detector subscribes to the same topic, runs an LSTM autoencoder for anomaly detection, and publishes alerts on a separate topic. The Spring Boot backend subscribes to both MQTT topics, persisting telemetry to MongoDB and converting anomaly messages into notifications. The React frontend consumes the REST API for fleet management, shipment booking, telemetry dashboards, and anomaly alerts.

Check out the code:

- [Frontend Service](https://github.com/UniSalento-IDALab-IoTCourse-2024-2025/wot-project-2024-2025-frontend-service-Bello) — React + TypeScript + Tailwind CSS

- [Backend Service](https://github.com/UniSalento-IDALab-IoTCourse-2024-2025/wot-project-2024-2025-spring-backend-service-Bello) — Spring Boot + MongoDB + MQTT

- [FastAPI Services](https://github.com/UniSalento-IDALab-IoTCourse-2024-2025/wot-project-2024-2025-fast-api-service-Bello) — Telemetry Streamer + LSTM Anomaly Detector