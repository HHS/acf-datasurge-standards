# Pipeline Best Practices

The range of pipeline projects that the ACF Data Surge team may take on will vary in scope and complexity. This guide foregoes specific recommendations in favor of providing a set of high-level considerations central to a well-executed pipeline project.

## Define clear goals/outcomes 
Understand and clearly define the business goals by knowing the answers  to the following questions:
- What is the problem?
    - Thoroughly understand the purpose of the pipeline. Spend significant time discussing the broad goal of the pipeline with stakeholders so that this goal is always in focus during pipeline development.
- What data sources/destinations are needed?
    - Clearly define where data are coming from and where they will ultimately be stored.
- What transformations should be applied?
    - Clarify how the data must be manipulated, if at all, en-route to its destination.
- What outputs are expected?
    - Define the format of data exiting the pipeline.
- How will success be measured?
    - Establish clear metrics for a successful pipeline.

## Choose the right tools and technologies
Depending on the data type, volume, and velocity, choose appropriate tools and technologies. For example: 
- Data ingestion tools: Apache Kafka, Logstash, Apache NiFi
- Data storage: 
    - SQL Databases (PostgreSQL, MySQL)
    - NoSQL Databases (MongoDB, Cassandra, DynamoDB):
    - Data Warehouses (Google BigQuery, Amazon Redshift, Snowflake)
- Monitoring and logging: Grafana, Elasticsearch, Logstash, and Kibana
- Data processing frameworks: Apache Spark, Apache Hadoop, Apache Flink, Pandas
- Data orchestration: Apache Airflow 

For a list of tools that can be used on GFE see the [Approved Software List](https://hhsgov.sharepoint.com/:x:/r/sites/asa/ocio/ops/ITServiceCentral/_layouts/15/Doc.aspx?sourcedoc=%7B2CFF3266-BDE4-4DAA-A007-2ACCC6015143%7D&file=Current%20Software%20Approval%20List.xlsx&action=default&mobileredirect=true) (only accessible within HHS).

## Scalability and flexibility 
Pipelines should balance the ability to be easily scaled up or down and to adapt to changes in data types and data formats. Some best practices to consider include:

- Program defenisively - Anticipate potential user and other errors and write code that fails gracefully. Avoid practices such as hardcoding, that can lead to subtle and insidious bugs. Instead, if matching a string use regular expressions. Otherwise, convert statements that are hardcoded into function parameters with default values.
- Use tool-agnostic frameworks - Where possible, use frameworks that work with many different tools. For example, when integrating SQL and Python, use [SQLAlchemy](https://www.sqlalchemy.org/) or a similar framework rather than writing SQL queries with text ([Example](https://github.com/HHS/ACF-pir-data/blob/dev/src/pir_pipeline/utils/SQLAlchemyUtils.py)).

Scalability and flexibility do not come without cost (both in time and money). When considering features for a pipeline, project teams can consider the following questions:

- How will implementing this feature affect the project timeline, and code complexity/maintainability?
- Does the cost of this feature fit within the project's budget?

## Implement data quality checks
Ensure that the pipeline includes steps for validating data at various stages to catch errors, inconsistencies, or missing data quickly.

- Validate pipeline input
  - [For example, confirm that file names have the correct structure](https://github.com/HHS/acf-ohs-budget-data-pipeline/blob/c6e1bd6f65b759200ada45427dd08c1d3603f13d/src/obdp/budget/BudgetData.py#L64)
- Validate that transformations are working as expected
  - [For example, include assertions that confirm data integrity is upheld after transformations](https://github.com/HHS/acf-ohs-budget-data-pipeline/blob/c6e1bd6f65b759200ada45427dd08c1d3603f13d/src/obdp/budget/BudgetData.py#L164)
- Validate pipeline output
  - [For example, use frameworks such as pydantic to ensure or enforce correct typing](https://github.com/HHS/acf-ohs-budget-data-pipeline/blob/c6e1bd6f65b759200ada45427dd08c1d3603f13d/src/obdp/budget/BudgetData.py#L215)
    - [Pydantic](https://docs.pydantic.dev/latest/)

## Monitoring and optimizing
Continuously monitor the performance of the pipeline and seek opportunities to optimize data processing times, reduce costs, and improve data quality. Implement monitoring and logging to track the performance and health of the pipeline. Alerts should be set up for failures or significant performance degradations. Logs can include assessments of data quality and any major errors or inconsistencies caught during data quality checks.

- [Simple logging functions](https://github.com/HHS/ACF-pir-data/blob/032d0a348d1330a435d0d118f067929cb5a047aa/src/pir_pipeline/utils/utils.py#L65-L96)
- Examples of logging
  - [PIR Pipeline](https://github.com/HHS/ACF-pir-data/blob/032d0a348d1330a435d0d118f067929cb5a047aa/src/pir_pipeline/ingestion/PIRIngestor.py#L41-L42) (and throughout)
  - [OHS Budget Data Pipeline](https://github.com/HHS/acf-ohs-budget-data-pipeline/blob/c6e1bd6f65b759200ada45427dd08c1d3603f13d/ohs-budget-data-pipeline/pipeline/app.py#L26) (and throughout)

## Ensure security and compliance
Regularly audit the pipeline for security vulnerabilities. Protect sensitive data through encryption, and access controls. Ensure any software used in a pipeline are approved by ACF and comply with security regulations ([Approved Software List](https://hhsgov.sharepoint.com/:x:/r/sites/asa/ocio/ops/ITServiceCentral/_layouts/15/Doc.aspx?sourcedoc=%7B2CFF3266-BDE4-4DAA-A007-2ACCC6015143%7D&file=Current%20Software%20Approval%20List.xlsx&action=default&mobileredirect=true) (only accessible within HHS)).

## Documentation and Testing
Ultimately, pipelines we develop are meant to be managed by the end-user without our support. Maintaining up-to-date documentation for the data pipeline architecture, data models, and operational procedures is crucial for helping clients take ownership of a pipeline. Pipelines should be tested with a robust, end-to-end strategy to ensure the reliability and accuracy of the data. A well-documented and tested pipeline will save time in understanding and troubleshooting during development and beyond.

- Example test suites
  - [PIR Pipeline](https://github.com/HHS/ACF-pir-data/tree/dev/tests)
  - [OHS Budget Data Pipeline](https://github.com/HHS/acf-ohs-budget-data-pipeline/tree/main/tests)
- Example documentation
  - [PIR Pipeline](https://hhs.github.io/ACF-pir-data/)
  - [OHS Budget Data Pipeline](https://super-disco-mrwvqkw.pages.github.io/)
