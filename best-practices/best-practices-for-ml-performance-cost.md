# Best practices for performance and cost optimization for machine learning

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
