# Best practices for performance and cost optimization for machine learning
https://cloud.google.com/architecture/best-practices-for-ml-performance-cost
Best pratice of architecture
  https://cloud.google.com/architecture

> Using Big Query ML rather than using Vertex AI if batch-prediction only

## Experimentation with Vertex AI Workbench user-managed notebooks
- Start with a sample of your data
- Select the machine type with the right balance between cost and performance

  - M-series for memory optimize, C-serivers for Cpu optimize, N-series for balanced

- Leverage accelerators effectively
  - up to 8 NVIDIA® Tesla® GPUs with notebooks
- Don't treat your instances as long-living ones & Auto-shutdown if dont use
- Monitor and improve your GPU utilization
  -   set up the GPU metrics reporting script and view logs in Cloud Monitoring

## Data preparation with BigQuery
- BigQuery pricing
  - BigQuery is **serverless**, **highly scalable**, and **cost-effective** cloud data warehouse
  - **flat rate** pricing is the cheapest option if you're spending at least US$10k each month; the next cheapest option is **flexible slots**
  - preprocessing workloads, suggest **NOT USING** on-demand pricing

- BigQuery to **explore** and **preprocess** large amounts of data -> Visualize with Notebooks/ Vertex AI
- BigQuery Storage API to load the data into pandas DataFrames in memory
- Using tfio.bigquery.BigQueryClient to load into TensorFlow (**if no preprocessing**)

## Data preparation with Dataflow and Apache Beam
- Experiment with interactive Apache Beam on user-managed notebooks (**before truly running at scale**)
- To reduce cost/ runtime
  - Using **Dataflow FlexRS** 
  - Using **Dataflow Shuffle** (GroupByKey,CoGroupByKey ) to reduce runtime & cost
  - Use the right machine type for your workload
  - **Disable public IP** addresses of workers to reduce cost (using private IP addresses only) _usePublicIps_
- Avoid **setting num_shards** on output transforms ( = 0, Dataflow will decide how many)
- Create a **batch of data points and process it as a whole**
- Preprocess the data once and **save** it as a **TFRecord file** (using for train TF models later)
- **Logs** are written to **Cloud Logging**
- Monitor your Dataflow jobs


