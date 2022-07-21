# Best practices for performance and cost optimization for machine learning
> References:
  - https://cloud.google.com/architecture/best-practices-for-ml-performance-cost
  - Best pratice of architecture : https://cloud.google.com/architecture
  - Supported models : https://cloud.google.com/tpu/docs/tutorials/supported-models

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

## Training with Vertex AI custom Training
- **trade-off** between model **accuracy** and **size** for your task (more complex -> more time predict & more model size)
- right machine configuration for your training characteristics
- **small datasets** (can fit all of your data in memory), use a **single large machine** (rather than using distributed training)
- Scale up before scaling out
- For **large datasets**, use distributed training
- Distributed training: 
  - Asynchronous: Increase the size of the parameter server to increase the bandwidth (because bandwitdth proportional to the size (number of vCPUs) )
  - Synchronous: Use MultiWorkerMirroredStrategy for distributed training of TensorFlow models
- Use the tf.data API to best utilize your accelerators
- Stream data from Cloud Storage for training **scikit-learn models**

  _When you train a scikit-learn model on large datasets, downloading the entire dataset into the training worker and loading it into memory doesn't scale. In these cases, consider using TensorFlow's stream-read/file_io API, which is preinstalled on the worker VM._
- Using **distributed XGBoost** with large datasets
- Prepare your environment in a container image
- Use automatic hyperparameter tuning
  - enableTrialEarlyStopping to True
  - maxParallelTrials to be between 2 and maxTrials/2 

## Serving with Vertex AI Prediction
- Online Serving
  - Reduce latency of serving ( usually online serving)
    - reduced-precision floating-point types (**bfloat16** ...)
    - post-training **quantization**
    - TensorFlow Model Optimization Toolkit
      -  post-training quantization, 
      -  quantization aware training, 
      -  model pruning
  - Manual scaling for highly variable request volume with N1 machines (When auto-scaling couldnt catch-up request volume)
  - Choose the right machine type for serving
    - **large models with high traffic** : N1 machines (but do not support scaling down to zero nodes)
    - **Scaling down to zero node**: mls1-c1-m2 and mls1-c4-m2
  - Use TF-TRT with NVIDIA GPU accelerators
  - Use **base64** encoding when **sending images**
  - Send multiple data points in one request
    - < 100 data points
    - < 1.5 Mb size
  - Request-response logging -> to BigQuery
---
- Offline Serving
  - Using Batch Serving service to saving cost
  - Increase the batch size for batch prediction jobs
- Use Cloud Monitoring to configure alerts based on the ML metrics

## Orchestration Pipelines
