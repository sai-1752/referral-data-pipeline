# Referral Data Pipeline

## Overview

This project implements a data pipeline to process referral program data and detect invalid referral rewards using business logic rules.

The pipeline performs:

* Data ingestion from CSV sources
* Data profiling
* Data cleaning and transformation
* Referral source categorization
* Fraud detection using business logic
* Report generation

## Technologies Used

* Python
* Pandas
* Docker

## Project Structure

```
referral-data-pipeline
│
├── data
├── output
├── Dockerfile
├── referral_pipeline.py
└── requirements.txt
```

## How to Run

Build the Docker image:

```
docker build -t referral-pipeline.
```

Run the pipeline:

```
docker run -v %cd%\output:/app/output referral-pipeline
```

## Output

The pipeline generates:

```
output/referral_report.csv
```

This report indicates whether each referral reward satisfies the defined business rules.

## Business Logic Validation

A referral reward is considered valid if:

* Reward value > 0
* Referral status is "Berhasil."
* Transaction status is "PAID."
* Transaction type is "NEW."
* Transaction occurs after referral creation
* Referrer membership is active
* Reward has been granted

Otherwise, the referral reward is flagged as invalid.
