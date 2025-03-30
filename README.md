# Latency_Measurement_and_evaluation_in_Real-time_Data_Streams
This repository contains configuration files and resources for benchmarking the Odysseus Data Stream Management System using the Nexmark data generator. It provides a structured benchmarking framework to evaluate query latency under varied streaming workloads.

## Table of Contents

- [Overview](#overview)
- [Docker Setup](#docker-setup)
- [Configuration Files](#configuration-files)
- [Data Rate Configurations](#data-rate-configurations)
- [Query Set](#query-set)
- [Benchmark Results](#benchmark-results)
- [License](#license)

---

## Overview

This benchmark leverages the Nexmark generator to simulate an online auction system with realistic data streams (`person`, `auction`, and `bid`). The benchmark is executed using the Odysseus stream processing system and measures end-to-end latency across different stream rates, windowing strategies, and operator combinations.

---

## Docker Setup

To run the Nexmark generator as a container, use the following command:

```bash
docker run -d -v "YOURLOCALFOLDER:/var/lib/nexmark" -p 65440-65443:65440-65443 odysseusol/nexmark
```

Replace `YOURLOCALFOLDER` with the absolute path to your local folder that contains the `NEXMarkGeneratorConfiguration.properties` file. This bind mount passes your custom configuration into the container at runtime.

---

## Configuration Files

This repository includes four configuration folders:

- `nexmark-config-1/`
- `nexmark-config-2/`
- `nexmark-config-3/`
- `nexmark-config-4/`

Each folder contains a tailored `NEXMarkGeneratorConfiguration.properties` file, aligned with one of the four workload scenarios described below. These configurations define tuple counts, stream emission rates, and auction durations to simulate different streaming conditions.

---

## Data Rate Configurations

The following table summarizes the configuration parameters for each query scenario:

| Scenario               | Tuples | Bid (t/s) | Auction (t/s) | Person (t/s) | Auction Duration (s) |
|------------------------|--------|-----------|---------------|--------------|-----------------------|
| Controlled Low Rate    | 5000   | 500       | 100           | 20           | 8                     |
| Mid-Rate Streaming     | 25000  | 500       | 100           | 20           | 6                     |
| High-Rate Streaming    | 100000 | 3000      | 600           | 300          | 5                     |
| Peak Load Simulation   | 100000 | 6000      | 1200          | 600          | 3                     |

---

## Query Set

The full list of benchmark queries used in the experiments is available in the following document:

📄 [Queries_List.pdf](./Queries_List.pdf)

This includes baseline queries, selection/projection queries, aggregation queries, and join-based workloads, all written in the Procedural Query Language (PQL) used by Odysseus.

---

## Benchmark Results

The latency and performance results from running the benchmark across all scenarios are compiled in:

📊 [Thesis_Implementation_results.xlsx](./Thesis_Implementation_results.xlsx)

This spreadsheet presents detailed measurements including query latency across scenarios, operator comparisons, and windowing strategy evaluations.

---

## License
This project is licensed under the MIT License. See the LICENSE file for details.
