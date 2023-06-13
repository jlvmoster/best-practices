# Best Practices on Data Engineering Concepts

## The Five Vs of Big Data

- Volume: how much data? (initial/growing size)
- Velocity: how fast is data generated and how quickly should it move? (batch vs stream)
- Variety: how diverse is the data? (unstructured, semi-structured, structured)
- Veracity: how accurate is the data? (quality)
- Value: what story is the data telling? (insights)

## The Five Key Data SLIs

- Data freshness: how up-to-date is your data?
- Distribution: is your data within an accepted range?
- Volume: is your data complete?
- Schema: does your schema change often? (frequent change indicates broken data)
- Lineage: answers questions like which upstream sources and downstream ingestors were impacted, as well as which teams are generating data and who is accessing it?

## Data Orchestration

> Data orchestration is the process of harvesting data from a variety of data sources for the purpose of combining and organizing it.

## Data Governance (DG)

> Data governance is everything you do to ensure data is secure, private, accurate, available, and usable. It includes the actions people must take, the processes they must follow, and the technology that supports them throughout the data life cycle.

### Data Stewardship

> A subset of DG which focuses on the core values such as data management and oversight in order to help provide business users with high-quality data that is easily accessible in a consistent manner.

## Data Lineage

> Data lineage is the process of tracking the flow of data over time, providing a clear understanding of where the data originated, how it was changed, and its ultimate destination within the data pipeline.

## Data Quality vs Data Reliability

### Data Quality

> Data quality covers the **six dimensions** of accuracy, completeness, consistency, timeliness, validity, and uniqueness.

### Data Reliability

> Data reliability does more than assessing completeness and accuracy; it necessitates considering how data quality evolves across diverse real-world conditions over time. Defines SLAs, SLIs (Service Level Indicator), and SLOs (Service Level Objective).

## Data Reconciliation

> Data reconciliation is defined as the process of verifying data during data migration. In-process target data is compared against source data to ensure that migration happens as expected.

During the data migration process, it is possible for mistakes to happen when performing mapping and transformation logic. Issues like runtime failures such as network dropouts or broken transactions can lead to data corruption.

These errors can lead to invalid data and can create a range of issues like:
- Missing records
- Missing values
- Incorrect values
- Duplicated records
- Badly formatted values
- Broken relationships across tables/systems
