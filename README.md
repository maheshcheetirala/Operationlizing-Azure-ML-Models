*NOTE:* This file is a template that you can use to create the README for your project. The *TODO* comments below will highlight the information you should be sure to include.


# Operationalizing The Machine Learning Model In Azure <br>

*TODO:* 
The Main aim of this Project is to productionize the Machine learning model using  Azure Conatiner instance.<br>
We need to consume the model built to see how the model is performing . To consume the model we need to deploy the model using ACI or AKS.<br>
In short we are going to deploy a ML model and cosnume it usig Endpoints and see how its performing by enabling app insights.<br>

## Architectural Diagram


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




*TODO* Remeber to provide screenshots of the `RunDetails` widget as well as a screenshot of the best model trained with it's parameters.

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
