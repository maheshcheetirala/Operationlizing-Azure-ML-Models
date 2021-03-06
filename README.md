


# Operationalizing The Machine Learning Model In Azure <br>

*TODO:* 
The Main aim of this Project is to productionize the Machine learning model using  Azure Conatiner instance.<br>
We need to consume the model built to see how the model is performing . To consume the model we need to deploy the model using ACI or AKS.<br>
In short we are going to deploy a ML model and cosnume it usig Endpoints and see how its performing by enabling app insights.<br>


## Architectural Diagram<br>
![complete architecture of the Project](architecture.PNG)


## Key Steps
### Authentication:
The first step in life cycle process is authentication, we have three types of authentications.<br>
- Key Based <br>
- Token Based <br>
- Interactive based Authentication <br>
### Deployment Settings <br>
For any deployment to be successful proper configuration is the crucial step. Here we need to configure the Cluster settings under the compute section of workspace.We choose minimum node count as 1 and maximum node count as 5. The upscaling and down scaling happens based on the demand from the experiments.<br>
### Register the Dataset <br>
Navigate to the Datasets section in the Workspace and create a new dataset from webfile and submit the URL required for the dataset. After this we should be able to register the dataset and use the registered Dataset for running experimnents in the workspace.<br>
![Datset Registartion in Azure Portal](Register.PNG)<br>
### AutoML Run<br>
Once the Dataset is registered we need to run a new Automl run from the workspace experiments sections. We need to choose the label column and select the compute target.Once the automl run is completed we get the best model out of several models. Here we got voting ensemble model which chooses voting model to choose the best of several runs. The base model is XGBOOST with Maxabs scaling and an accuracy of 91%.<br>
![AutoMl run in portal](automl.PNG)<br> <br>
![Best Model from AutoML](bestmodel.PNG)<br>
### Deployment using endpoint<br>
Once we Have the best model its time to deploy the model. We can use azure Kubernetes service or azure container instane for the deployment. We need to choose authenticate method during the deployment method. Once deployment is succeded an endpoint will be created with status showing as healthy in workspace<br>.
![Endpoint of the deployed model](endpoint.PNG)<br>
### Enabling the Logs using app Insights<br>
Once the model is deployed we need to enable the logs setting the appinsights = True in the Experiment logging section by adding the experiment name. Once we have enabled the logging we should see the status in application insights saying the failed requests, timed out requests etc.<br>
![Logs Enabled in Python Script](logsenabled.PNG)<br>

![Logs Enabled](appinsightsenabled.PNG)<br>

![Application Insights from the Portal](appinsights.PNG)<br>

### Consumption of Endpoint<br>
We can consume this endpoint using REST API or by running Azure ML python SDK's. Here we are testing both using endpoint.py and Swagger<br>
![Endpoint consumption](consumption.PNG) <br>.
Here we are testing two data points and we get two outputs yes, No as the output.<br>

### Cosnumption of Endpoint through Swagger UI<br>
Swagger is one of the API tetsing platforms available . Once the model is deployed we get a Swagger JSon file from the endpoint which needs to be downloaded and placed in the folder containing swagger files serve.py and swagger.sh.<br>
After that we need to launch a local web server using serve script and lauch swagger using docker container by running swagger.sh<br>
![local server](localrender.PNG)<br>
![Sample Swagger](sampleswagger.PNG)<br>.
Replace the default swagger URL with your local hsot URL and swagger will display the sample input and sample outputs for our application.<br>
### Bench Marking<br>
Its always better to evaluate the model perfomance continuously and take necessary action. Here we use apache benchmark to see the model performance for ten runs.<br>
![Apache Bench Marl](benchmark.PNG)<br>
### Creating and Publishing pipeline <br>
The whole process can be automated using the CI/CD pipelines similar to devops. Azure ML python SDK has a great feature  for this where we can define the piplelines and pipeline parameters . We can schedule the pipelines using schdeule recurrence parameter reducing the manual efforts.<br>
![Pipeline in Azure](restoutputs.PNG)<br>
![Pipeline Graph](pipeline.PNG)<br>
![Rest Endpoint pipeline](restendpoint.PNG)<br>
The active endpoint can be veiwed in endpoints section as below.<br>
![Active rest api](activeendpoint.PNG)<br>
![PipelineRunSubmitted](rundetails.PNG)<br>
![Pipelinerun](pipelinesummary.PNG)

## Screen Recording
[Video Shwoing Complete Life Cycle](https://youtu.be/F1gmkDBKVfE)<br>

## Future Improvements
- The Dataset is imbalnaced may be doing feature engineering can improve the accuracy.<br>
- We can configure alerts using azure functions when the benchmark is above or beyond threshold.<br>
- collecting more data can definietly help in improving accuracy.
- We can try tesing the batch data in a shcedule and see the performance.
