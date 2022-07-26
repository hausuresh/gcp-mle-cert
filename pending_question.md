# Pending Problem
- Recommendation
- Tensorflow vs Keras

# Pending question

---
N7
You recently designed and built a custom neural network that uses critical dependencies specific to your organization's framework. You need to train the model using a managed training service on Google Cloud. However, the ML framework and related dependencies are not supported by Al Platform Training. Also, both your model and your data are too large to fit in memory on a single machine. Your ML framework of choice uses the scheduler, workers, and servers distribution structure. What should you do?

A. Build your custom container to run jobs on Al Platform Training

B. Use a built-in model available on Al Platform Training

C. Build your custom containers to run distributed training jobs on Al Platform Training

D. Reconfigure your code to a ML framework with dependencies that are supported by Al Platform Training

---
N6
You work for a global footwear retailer and need to predict when an item will be out of stock based on historical inventory dat a. Customer behavior is highly dynamic since footwear demand is influenced by many different factors. You want to serve models that are trained on all available data, but track your performance on specific subsets of data before pushing to production. What is the most streamlined and reliable way to perform this validation?

A. Use the TFX Mode!Validator tools to specify performance metrics for production readiness

B. Use k-fold cross-validation as a validation strategy to ensure that your model is ready for production.

C. Use the last relevant week of data as a validation set to ensure that your model is performing accurately on current data.

D. Use the entire dataset and treat the area under the receiver operating characteristics curve (AUC ROC) as the main metric.


---
N5
You are building a linear model with over 100 input features, all with values between -1 and 1. You suspect that many features are non-informative. You want to remove the non-informative features from your model while keeping the informative ones in their original form. Which technique should you use?

A. Use Principal Component Analysis to eliminate the least informative features.
B. Use L 1 regularization to reduce the coefficients of uninformative features to 0.
C. After building your model, use Shapley values to determine which features are the most informative.
D. Use an iterative dropout technique to identify which features do not degrade the model when removed

---
You are an ML engineer in the contact center of a large enterprise. You need to build a sentiment analysis tool that predicts customer sentiment from recorded phone conversations. You need to identify the best approach to building a model while ensuring that the gender, age, and cultural differences of the customers who called the contact center do not impact any stage of the model development pipeline and results. What should you do?

**A. Convert the speech to text and extract sentiments based on the sentences**
B. Convert the speech to text and extract sentiment using syntactical analysis
C. Extract sentiment directly from the voice recordings
D. Convert the speech to text and build a model based on the words

---
You are building a linear regression model on BigQuery ML to predict a customer's likelihood of purchasing your company's products. Your model uses a city name variable as a key predictive component. In order to train and serve the model, your data must be organized in columns. You want to prepare your data using the least amount of coding while maintaining the predictable variables. What should you do?

A. Create a new view with BigQuery that does not include a column with city information.

B. Use Dataprep to transform the state column using a one-hot encoding method, and make each city a column with binary values.

C. Use Cloud Data Fusion to assign each city to a region labeled as 1, 2. 3, 4, or Sr and then use that number to represent the city in the model.

D. Use TensorFlow to create a categorical variable with a vocabulary list Create the vocabulary file, and upload it as part of your model to BigQuery ML

---
During batch training of a neural network, you notice that there is an **_oscillation_** in the loss. How should you adjust your model to ensure that it converges?

A. Increase the size of the training batch

B. Decrease the size of the training batch

C. Increase the learning rate hyperparameter

D. Decrease the learning rate hyperparameter



---
You are going to train a DNN regression model with Keras APJs using this code:

```python
  model = tf.keras.Sequential() 
  model.add(tf.keras.layers.Dense(256,use_bias-True,
    activation-•relu',
    kernel_initializer-None,
    kernel_regularizer-None,
    input_shape-(500,)))
  model.add(tf.keras.layers.Oropout(rate-0.25))
  model.add(tf.keras.layers.Oense(
    128, use_bias-True,
    activation-•relu',
    kernel_initializer-'uniform',
    kernel_regularizer-'12')
   )
  model.add(tf.keras.layers.Dropout(rate-0.25))
  model.add(tf.keras.layers.Dense( 2, use_bias-False, activation-'softriax'))
  model.compile(loss-mse')

```
How many trainable weights does your model have? (The arithmetic below is correct.)

A. 501 * 256+257 * 128+2 = 161154

B. 500 * 256+256 * 128+128 * 2 = 161024

C. 501 * 256+257 * 128 + 128 * 2 = 161408

D. 500*256*0(?)25+256*128*0(?)25+128*2 = 4044

---
You are an ML engineer at a large grocery retailer with stores in multiple regions. You have been asked to create an inventory prediction model. Your modelג€™s features include region, location, historical demand, and seasonal popularity. You want the algorithm to learn from new inventory data on a daily basis. Which algorithms should you use to build the model?

A. Classification

B. Reinforcement Learning

C. Recurrent Neural Networks (RNN)

D. Convolutional Neural Networks (CNN)

---
You are building a real-time prediction engine that streams files which may contain Personally Identifiable Information (PII) to Google Cloud. You want to use the
Cloud Data Loss Prevention (DLP) API to scan the files. How should you ensure that the PII is not accessible by unauthorized individuals?

A. Stream all files to Google Cloud, and then write the data to BigQuery. Periodically conduct a bulk scan of the table using the DLP API.

B. Stream all files to Google Cloud, and write batches of the data to BigQuery. While the data is being written to BigQuery, conduct a bulk scan of the data using the DLP API.

C. Create two buckets of data: Sensitive and Non-sensitive. Write all data to the Non-sensitive bucket. Periodically conduct a bulk scan of that bucket using the DLP API, and move the sensitive data to the Sensitive bucket.

_D. Create three buckets of data: Quarantine, Sensitive, and Non-sensitive. Write all data to the Quarantine bucket. Periodically conduct a bulk scan of that bucket using the DLP API, and move the data to either the Sensitive or Non-Sensitive bucket._

---
You have written unit tests for a Kubeflow Pipeline that require custom libraries. You want to automate the execution of unit tests with each new push to your development branch in Cloud Source Repositories. What should you do?

A. Write a script that sequentially performs the push to your development branch and executes the unit tests on Cloud Run.

B. Using Cloud Build, set an automated trigger to execute the unit tests when changes are pushed to your development branch.

C. Set up a Cloud Logging sink to a Pub/Sub topic that captures interactions with Cloud Source Repositories. Configure a Pub/Sub trigger for Cloud Run, and execute the unit tests on Cloud Run.

D. Set up a Cloud Logging sink to a Pub/Sub topic that captures interactions with Cloud Source Repositories. Execute the unit tests using a Cloud Function that is triggered when messages are sent to the Pub/Sub topic.

---
You have deployed multiple versions of an image classification model on AI Platform. You want to monitor the performance of the model versions over time. How should you perform this comparison?
https://cloud.google.com/ai-platform/prediction/docs/continuous-evaluation
A. Compare the loss performance for each model on a held-out dataset.

B. Compare the loss performance for each model on the validation data.

C. Compare the receiver operating characteristic (ROC) curve for each model using the What-If Tool.

D. Compare the mean average precision across the models using the Continuous Evaluation feature

--- 
You work for a social media company. You need to detect whether posted images contain cars. Each training example is a member of exactly one class. You have trained an object detection neural network and deployed the model version to AI Platform Prediction for evaluation. Before deployment, you created an evaluation job and attached it to the AI Platform Prediction model version. You notice that the precision is lower than your business requirements allow. How should you adjust the modelג€™s final layer softmax threshold to increase precision?

A. Increase the recall.

B. Decrease the recall.

C. Increase the number of false positives.

D. Decrease the number of false negatives.

---
Question 54 Topic 1

Your team has been tasked with creating an ML solution in Google Cloud to classify support requests for one of your platforms. You analyzed the requirements and decided to use TensorFlow to build the classifier so that you have full control of the model's code, serving, and deployment. You will use Kubeflow pipelines for the ML platform. To save time, you want to build on existing resources and use managed services instead of building a completely new model. How should you build the classifier?

A. Use the Natural Language API to classify support requests.

B. Use AutoML Natural Language to build the support requests classifier.

C. Use an established text classification model on AI Platform to **perform transfer learning**.

D. Use an established text classification model on AI Platform **as-is** to classify support requests.

---

Question 55Topic 1

You recently joined a machine learning team that will soon release a new project. As a lead on the project, you are asked to determine the production readiness of the ML components. The team has already tested features and data, model development, and infrastructure. Which additional readiness check should you recommend to the team?

A. Ensure that training is reproducible.

B. Ensure that all hyperparameters are tuned.

C. Ensure that model performance is monitored.

D. Ensure that feature expectations are captured in the schema.

  https://developers.google.com/machine-learning/testing-debugging/pipeline/deploying

---
Question #56Topic 1

You work for a credit card company and have been asked to create a custom fraud detection model based on historical data using AutoML Tables. You need to prioritize detection of fraudulent transactions while minimizing false positives. Which optimization objective should you use when training the model?

A. An optimization objective that minimizes Log loss

B. An optimization objective that maximizes the Precision at a Recall value of 0.50

C. An optimization objective that maximizes the area under the precision-recall curve (AUC PR) value

D. An optimization objective that maximizes the area under the receiver operating characteristic curve (AUC ROC) value

https://neptune.ai/blog/f1-score-accuracy-roc-auc-pr-auc#:~:text=ROC%20AUC%20vs%20PR%20AUC&text=What%20is%20different%20however%20is,and%20true%20positive%20rate%20TPR.

PR is recommended for high imbalanced than ROC

---
Question #57Topic 1

Your company manages a video sharing website where users can watch and upload videos. You need to create an ML model to predict which newly uploaded videos will be the most popular so that those videos can be prioritized on your company's website. Which result should you use to determine whether the model is successful?

A. The model predicts videos as popular if the user who uploads them has over 10,000 likes.

B. The model predicts 97.5% of the most popular clickbait videos measured by number of clicks.

C. The model predicts 95% of the most popular videos measured by watch time within 30 days of being uploaded.

D. The Pearson correlation coefficient between the log-transformed number of views after 7 days and 30 days after publication is equal to 0.

> note
  Ans: C (See https://developers.google.com/machine-learning/problem-framing/framing#quantify-it; though it's just an example.)
  (A) The absolute number of likes shouldn't be used because no information about subscribers or visits to the website is provided. The number may vary.
  (B) Clickbait videos are a subset of uploaded videos. Using them is an improper criterion.
  (D) The coefficient should reach 1. (Ref:https://arxiv.org/pdf/1510.06223.pdf)

![image](https://user-images.githubusercontent.com/39760546/184103423-192c3340-779f-4ccc-bba9-1ae45f9cfa23.png)

---
Question #59Topic 1

Your data science team needs to rapidly experiment with various features, model architectures, and hyperparameters. They need to track the accuracy metrics for various experiments and use an ** API to query the metrics over time**. What should they use to track and report their experiments while minimizing manual effort?

A. Use Kubeflow Pipelines to execute the experiments. Export the metrics file, and query the results using the Kubeflow Pipelines API.

B. Use AI Platform Training to execute the experiments. Write the accuracy metrics to BigQuery, and query the results using the BigQuery API.

C. Use AI Platform Training to execute the experiments. Write the accuracy metrics to Cloud Monitoring, and query the results using the Monitoring API.

D. Use AI Platform Notebooks to execute the experiments. Collect the results in a shared Google Sheets file, and query the results using the Google Sheets API.

https://www.kubeflow.org/docs/components/pipelines/sdk/pipelines-metrics/

---
