# 1.	How anomaly detection can help your business
Anomaly detection allows companies to identify or even predict abnormal patterns in unbounded data streams. Whether you are a large retailer identifying positive buying behaviors, a financial services provider detecting fraud, or a sustainability customer, identifying and mitigating potential greenhouse gases from equipment. In this post, we walk through an AI and human combined pattern for detecting anomalies in tabular data. 
# 2.	Enabling anomaly detection for tabular data
A model-based pattern has been the primary technique used by many customers. However, our method is a combination of ML models and human intelligence. 
First, our model would pick the appropriate model based on that human intelligence. Since multi-definition is supported, there could be conflicts between models or rules, we use a pruning model to filter false-positive results. Then the results would be returned to users, telling which record is anomalous and including a detailed explanation to help handle the anomaly. 
Second, users can provide feedback based on the results. Our model would use feedback to fine-tune the model. So, the entire workflow would be like this, customers provide contexts and data to our model, and according to the detected results, they can offer feedback labels for us to finetune the results. After several iterations, the model will converge and satisfy customers' requirements. 
Third, we also support an inference scenario; when the result is acceptable for customers, we will train a supervised model based on the result so that the model can make inference for future inference data.
# 3.Step by Step Guidence
## Upload Data
Select provided data files on the left panel of the portal or upload user’s own dataset (Only Emission data is available now) 
## Set Up Human Intelligence 
For users to deliver human intelligence, we designed a SQL-like config module. It is composed of 4 basic conceptions, including group, slice, measure, and anomaly type. 
## Measure: 
required, a numerical column, indicating intuitive measure of anomalies. 
## Group: 
optional, column names of subgroups, we separate data into different subgroups and conduct detection within each subgroup. For example, separate data into different countries. 
## Slice: 
optional, column names of slicers, we slice each group of data into different slices, then aggregate the data to slice level and conduct anomaly detection. For example, slice data into different regions and aggregate the measure values from the same region, then the algorithm will detect anomalous regions. 
## Aggregation method: 
'Average', 'Max', 'Min', 'Sum', 'Percentile XX'(XX percentiles, where XX is an integer value from 1 to 99)]
Default: 'Average'
## Anomaly type: 
1. Auto anomaly detection: If human intelligence is not available, the platform will turn on auto-detection model that is an unsupervised model applied on whole data. 
2. Human intelligence-based anomaly detection: We define 3 types of anomalies based on human intelligence that will potentially lead to better performance. As illustrated in the following future, the anomaly types include Distribution, Extreme Value and Correlation.
3. Label: Users can also label some samples based on the platform’s outputs to refine the data. To improve the detection performance further, our platform has a semi-supervised learning process to make use of the additional labeled data.
![image](https://user-images.githubusercontent.com/36343326/186331938-dc93049a-0279-4f74-9a12-5c2a591bf19c.png)

# 4. Result
Click the ‘Run’ button to get the anomaly detection result.
### Detected Anomaly Overview: 
the graph shows the detected anomaly number and model-filtered false positive anomaly number of each human intelligence.
### Result Filter: 
users can filter the result with specific column value.
### Top 5 Anomaly: 
anomalies with top 5 anomaly score are shown by default. Click on the ‘show graph’ button to see the visualized explanation.


