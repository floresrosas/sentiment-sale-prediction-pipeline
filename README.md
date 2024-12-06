# sentiment-sale-prediction-pipeline

## Project Overview
Can reddit comments give a realtime gauge of market sentiment for particular stocks? How well can this be gauged? Note: This is a personal project to learn more about: Streaming, Containerization. Clusters, Data Modeling, Natural Language, Linear Regression and Visualization


# Table of Contents
- [Project Overview](#project-overview)
- [Table of Contents](#table-of-contents)
- [Architecture](#architecture)
- [Installation and Setup](#installation-and-setup)
- [Improvements](#improvements)
- [Acknowledgements](#acknowledgements)

# Architecture

![reddit_sentiment_analysis_pipeline_architecture](https://raw.githubusercontent.com/nama1arpit/reddit-streaming-pipeline/main/images/Reddit%20Sentiment%20Analysis%20Data%20Pipeline.drawio.png)

All applications in the above architecture are containerized into **Docker containers**, which are orchestrated by **Kubernetes** - and its infrastructure is managed by **Terraform**. The docker images for each application are available publically in the [Docker Hub registry](https://hub.docker.com/repositories/nama1arpit). Further details about each layer is provided below:

1. **Data Ingestion :** A containerized Python application called *reddit_producer* connects to Reddit API using credentials provided in the `.config/reddit_producer.cfg` file. It takes the received messages (reddit comments) and converts select messages into a JSON format. These transformed messages are then sent and stored in a Kafka broker. [PRAW](https://praw.readthedocs.io/en/stable/) python library is used for interacting with Reddit API.

2. **Message Broker :** The Kafka broker (*kafkaservice* pod), recieves messages from the *reddit_producer*. The Kafka broker is accompanied by the Kafdrop applicatino, which acts as Kafka mointoring tool through UI. When Kafka starts, another container named `kafkainit` creates the topic `redditcomments`. The *zookeeper* pod is launched before Kafka for managing Kafka metadata.

3. **Stream Processer : TODO 

4. **Processed Data Storage : TODO 

5. **Data Visualisation : TODO 


# Acknowledgements
1. [Finnhub Streaming Data Pipeline Project](https://github.com/RSKriegs/finnhub-streaming-data-pipeline)
2. Docker Images - 
3. Libraries - [Kafka-Python](https://kafka-python.readthedocs.io/en/master/), [PRAW](https://praw.readthedocs.io/en/stable/)

Thank you @nama1arpit for the inspo:
https://github.com/nama1arpit/reddit-streaming-pipeline/blob/main/README.md?plain=1



