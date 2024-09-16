# Real-time IoT Data Streaming and Processing Project

This project demonstrates real-time ingestion and processing of high-volume streaming data from IoT devices using Apache Kafka, Azure services, and containerized microservices.

## Table of Contents
- [Overview](#overview)
- [Architecture](#architecture)
  - [Architecture Diagram](#architecture-diagram)
- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Usage](#usage)
- [Data Processing](#data-processing)
- [Monitoring and Visualization](#monitoring-and-visualization)
- [Scaling](#scaling)
- [Contributing](#contributing)
- [License](#license)

## Overview

This project provides a scalable solution for ingesting, processing, and analyzing high-volume streaming data from IoT devices. It utilizes Apache Kafka for data ingestion, Azure services for data processing and storage, and containerized microservices for flexibility and scalability.

Key features:
- Real-time data ingestion from diverse IoT devices
- Scalable data processing using Apache Kafka and Azure services
- Time series analysis and anomaly detection
- Long-term data storage and analytics
- Real-time monitoring and visualization

## Architecture

The system architecture includes the following components:

1. **IoT Devices**: Various sensors and devices generating real-time data
2. **Edge Devices**: Local devices for initial data processing and aggregation
3. **Azure IoT Hub**: Managed service for bi-directional communication with IoT devices
4. **Apache Kafka**: Distributed streaming platform for high-throughput data ingestion
5. **Stream Processing**: Real-time data processing and analysis (e.g., Apache Flink, Kafka Streams)
6. **Azure Functions**: Serverless compute for event-driven data processing
7. **Azure Time Series Insights**: Time series database and analytics service
8. **Azure Cosmos DB**: Globally distributed NoSQL database for real-time data storage
9. **Azure Data Lake Storage**: Scalable data lake for long-term data retention
10. **Azure Synapse Analytics**: Analytics service for big data and data warehousing
11. **Power BI**: Business analytics and visualization tool
12. **Azure Kubernetes Service (AKS)**: Container orchestration for managing microservices

### Architecture Diagram

Below is a high-level architecture diagram of the Real-time IoT Data Streaming and Processing Project:

![Real-time IoT Data Streaming and Processing Architecture](iot-architecture-diagram.svg)

This diagram illustrates the flow of data from IoT devices through various components for ingestion, processing, storage, and analysis.

## Prerequisites

- Azure subscription
- Docker
- Azure CLI
- kubectl
- Helm
- Python 3.8+
- Apache Kafka
- Apache Flink or Kafka Streams

## Setup

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/realtime-iot-data-processing.git
   cd realtime-iot-data-processing
   ```

2. Build Docker images:
   ```
   docker build -t kafka-producer:latest -f Dockerfile.kafka-producer .
   docker build -t stream-processor:latest -f Dockerfile.stream-processor .
   docker build -t azure-function:latest -f Dockerfile.azure-function .
   docker build -t tsi-processor:latest -f Dockerfile.tsi-processor .
   ```

3. Set up Azure resources:
   - Create an Azure IoT Hub
   - Create an Azure Kubernetes Service (AKS) cluster
   - Create an Azure Cosmos DB account
   - Set up Azure Data Lake Storage
   - Create an Azure Synapse Analytics workspace
   - Set up Azure Time Series Insights

4. Deploy Kafka to AKS:
   ```
   helm repo add bitnami https://charts.bitnami.com/bitnami
   helm install my-kafka bitnami/kafka
   ```

5. Apply Kubernetes configurations:
   ```
   kubectl apply -f k8s/kafka-producer-deployment.yaml
   kubectl apply -f k8s/stream-processor-deployment.yaml
   kubectl apply -f k8s/azure-function-deployment.yaml
   kubectl apply -f k8s/tsi-processor-deployment.yaml
   ```

6. Configure IoT devices and edge devices to connect to Azure IoT Hub.

7. Update configuration files with your Azure credentials and connection details.

## Usage

1. Start the Kafka producer to ingest IoT data:
   ```
   kubectl apply -f k8s/kafka-producer-job.yaml
   ```

2. Monitor stream processing logs:
   ```
   kubectl logs -f deployment/stream-processor
   ```

3. Check Azure Function logs for event-driven processing:
   ```
   kubectl logs -f deployment/azure-function
   ```

4. Monitor Time Series Insights processing:
   ```
   kubectl logs -f deployment/tsi-processor
   ```

5. Use Azure portal to monitor IoT Hub, Cosmos DB, and other Azure services.

## Data Processing

The project includes several data processing components:

1. **Edge Processing**: Initial data filtering and aggregation on edge devices.
2. **Stream Processing**: Real-time analysis using Apache Flink or Kafka Streams.
3. **Azure Functions**: Event-driven processing for specific data patterns or thresholds.
4. **Time Series Analysis**: Using Azure Time Series Insights for temporal data analysis.

For details on data processing logic and customization, refer to the `docs/data-processing.md` file.

## Monitoring and Visualization

- Use Azure Monitor for comprehensive monitoring of all Azure resources.
- Azure Time Series Insights provides built-in visualization for time series data.
- Power BI can be connected to Azure Synapse Analytics for custom dashboards and reports.

## Scaling

To handle increased data volume:

1. Scale out Kafka brokers:
   ```
   kubectl scale statefulset my-kafka --replicas=5
   ```

2. Scale stream processing pods:
   ```
   kubectl scale deployment stream-processor --replicas=3
   ```

3. Adjust Azure IoT Hub and Cosmos DB throughput units as needed.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
