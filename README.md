# Spark ETL Practice

## Description
ETL job built with Apache Spark to process restaurant and weather data.

## What the job does:
1. Reads restaurant data from CSV
2. Finds and fixes null coordinates using OpenCage Geocoding API
3. Generates 4-character geohash from latitude and longitude
4. Loads weather data (October 2016)
5. LEFT JOINs restaurant and weather data by geohash
6. Saves enriched data to Parquet partitioned by country

## Technologies
- Apache Spark 3.5.0
- PySpark
- pygeohash
- OpenCage Geocoding API
- Docker + Jupyter Notebook

## Results
- 1997 restaurants processed
- 1 null coordinate fixed via OpenCage API (Savoria, Dillon, US)
- 66697 rows in final dataset
- Data saved in Parquet format partitioned by country

## How to run
1. Install Docker
2. Run Jupyter with PySpark:
```
docker run -it --rm -p 8888:8888 jupyter/pyspark-notebook
```
3. Open `spark_etl_job.ipynb` and run all cells

## Tests
5 tests implemented and passed:
- ✅ No null coordinates
- ✅ All geohashes are 4 characters long
- ✅ Result is not empty
- ✅ All 1997 restaurants present in result
- ✅ Output parquet file exists
