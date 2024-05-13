# ETL (Extract, Transform, Load)

ETLs are workloads that plays important roles in a big data pipeline.
These workloads are responsible to collect data from different datasources, and apply some operations over the data such as cleaning, aggregating, reporting. And finally loading the data into another storage, usually datalakes and data warehouses.

## Cronjobs

Cronjobs are tasks schedulers which are configured to trigger a process after a specific intervals.
Commonly Cronjobs are responsible to start ETLs processes and other sort of tasks.
You can define cronjobs directly in the operational system in cases you are using a bare metal machine, or some platforms such as kubernetes also allow you to define them as an object.
