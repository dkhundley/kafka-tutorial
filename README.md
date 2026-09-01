# Lightweight Kafka Pizza-Order Demo

This project runs a small local event-streaming environment for learning Kafka:

- one Kafka broker using KRaft (no ZooKeeper)
- Confluent Schema Registry
- Kafka Connect
- one Jupyter notebook with an Avro producer and two consumer groups

The setup is intentionally plaintext, single-node, and suitable only for local development.

## Prerequisites

- Docker Desktop
- [`uv`](https://docs.astral.sh/uv/)

The Confluent `8.3.1` images support both Intel and Apple Silicon Macs.

## Start the demo

Install the Python environment and start the containers:

```bash
uv sync
docker compose up -d
docker compose ps
```

Wait until Kafka, Schema Registry, and Kafka Connect all show as `healthy`. Then launch JupyterLab:

```bash
uv run jupyter lab
```

Open `notebooks/pizza_orders.ipynb` and run the cells from top to bottom. The notebook recreates only the `pizza-orders` topic on every run, produces five Avro orders, confirms their schema registration, and lets two independent consumer groups process all five records.

## Local endpoints

| Service | Endpoint |
| --- | --- |
| Kafka | `localhost:9092` |
| Schema Registry | `http://localhost:8081` |
| Kafka Connect | `http://localhost:8083` |

Kafka Connect is configured and checked by the notebook, but this first demo does not create a connector.

## Stop or reset

Stop the containers while preserving Kafka's Docker volume:

```bash
docker compose down
```

Remove the containers and all persisted Kafka data for a completely clean cluster:

```bash
docker compose down --volumes
```
