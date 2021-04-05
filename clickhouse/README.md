- размер таблиц
```bash
SELECT table, round(sum(bytes) / 1024/1024/1024, 2) as size_gb FROM system.parts WHERE active GROUP BY table ORDER BY size_gb DESC
```
```bash
SHOW CREATE TABLE db.table
```
DROP DATABASE db

SHOW TABLES IN db

sudo docker exec -it clickhouse sh
clickhouse-client

SELECT * FROM consumers.application_log
SELECT * FROM consumers.application_log_consumer limit 10
SELECT * FROM analytics.application_log limit 10



CREATE DATABASE consumers ENGINE = Atomic
CREATE DATABASE analytics ENGINE = Atomic

#######################################
CREATE DATABASE analytics;
CREATE DATABASE consumers;
​
CREATE TABLE analytics.application_log (
    node String,
    application String,
    application_version Nullable(String),
    request_id Nullable(String),
    request_path String,
    request_input String,
    request_user_agent Nullable(String),
    request_user_id Nullable(UInt64),
    request_execution_time Float64,
    request_timestamp Float64,
    request_log Nullable(String),
    response_code Nullable(UInt16)
)
ENGINE = MergeTree()
ORDER BY (request_timestamp);
​
CREATE TABLE consumers.application_log (
    node String,
    application String,
    application_version Nullable(String),
    request_id Nullable(String),
    request_path String,
    request_input String,
    request_user_agent Nullable(String),
    request_user_id Nullable(UInt64),
    request_execution_time Float64,
    request_timestamp Float64,
    request_log Nullable(String),
    response_code Nullable(UInt16)
)
ENGINE = Kafka('kafka:9092', 'application_log', 'clickhouse', 'JSONEachRow');
​
CREATE MATERIALIZED VIEW consumers.application_log_consumer TO analytics.application_log AS
SELECT * FROM consumers.application_log;
##############################################
#1 нода
CREATE DATABASE analytics;
CREATE DATABASE consumers;
​
CREATE TABLE analytics.application_log (
    node String,
    application String,
    application_version Nullable(String),
    request_id Nullable(String),
    request_path String,
    request_input String,
    request_user_agent Nullable(String),
    request_user_id Nullable(UInt64),
    request_execution_time Float64,
    request_timestamp Float64,
    request_log Nullable(String),
    response_code Nullable(UInt16)
)
ENGINE = MergeTree()
ORDER BY (request_timestamp);
​
CREATE TABLE consumers.application_log (
    node String,
    application String,
    application_version Nullable(String),
    request_id Nullable(String),
    request_path String,
    request_input String,
    request_user_agent Nullable(String),
    request_user_id Nullable(UInt64),
    request_execution_time Float64,
    request_timestamp Float64,
    request_log Nullable(String),
    response_code Nullable(UInt16)
)
ENGINE = Kafka('kafka:9092', 'application_log', 'clickhouse', 'JSONEachRow');
​
CREATE MATERIALIZED VIEW consumers.application_log_consumer TO analytics.application_log AS
SELECT * FROM consumers.application_log;
###############
