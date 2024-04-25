# Introduction - DevOps Azure Machine Learning Workspace for MLops
The pipeline delpoys an Azure Machine Learning Workspace for MLops within a resource group in your subscription along with supporting and neccessary resources 
..to data science, train, build, deploy, integrate or just learn.
This will assist in AI-900: Microsoft Certified Azure AI Fundamentals
And was inspired by the course 'Introduction to MLOps on Azure' on aCloudGuru

# Getting Started
1.	Require Microsoft Azure Subscription and Azure Devops Org and Project, Upload the folder to your Devops Organization's Repo folder provided from this repository.

2.	Jobs require one Parallelism which will require a self hosted agent which can be run in Private Project
(more paralellism will require a Public project or purchase of paralellism), which is beyond the scope of this code. *See step 4.

3. Update the parameter file with your enviornment elements and update the pipeline.yaml to match.

Note: Update the parameter values in the 'mlworkspacedeploy.param.json' (noted by 'rename')to fit your naming standards, uniqueness and environment.

UPDATE:

azureResourceManagerConnection: 'Azure subscription 1(ADD YOUR SUBSCRIPTION ID)'

AND

subscriptionId: 'ADD YOUR SUBSCRIPTION ID'

AND makesure the resource group name defined in the azure-pipelines.yml matches the element in mlworkspacedeploy.param.json
resourceGroupName: 'machine-learning-workspace-rename'.

Verify the folder path matches your devops project. If you upload this folder it should match the folder paths specified to the template and parameter json files.          
                csmFile: '$(System.DefaultWorkingDirectory)/ARM/mlworkspacedeploy.json'
                csmParametersFile: '$(System.DefaultWorkingDirectory)/ARM/mlworkspacedeploy.param.json'

# Quick High-level guidance on installing and configuring your own self-hosted agent to run parallelism for your DevOps org project.                

4.	However! here are high level accurate and tested instructions for deploying your own self-hosted agent; 
deploy a VM instance in the Azure subscription in any resource group, 
can be a server OS or client OS,(even your own workstation or laptop).
I would recommend at least 2 vcpus for whatever SKU is used.  

5. Create a Public Access Token (PAT) in user settings (the gear *) next to your devops login account.

6.	On the device you plan to use as a self-hosted agent open your devops project in a browser. 
Go to your Devops>Org>Project settings. Under Pipelines, select Agent Pools, and select the 'Default' Azure Pipelines and create a 'New agent' This will provide the download and instructions for Windows, macOS and Linux. After installing the agent on your device and following the configure account instructions, make sure you run .\run.cmd,  or ./run.sh with elevated permissions in Powershell or Bash.

7.   Again go to Devops>Org>Project settings. Under Pipelines, select Agent Pools, and select the 'Default' then the Agents tab
It should show the name of your server, workstation, pc as online.

8. Congrats now you can run the pipeline.


# Build and Test
Pipleline deploys resources defined ARM folder containing an ARM template 'mlworkspacedeploy.json' and 'mlworkspacedeploy.param.json' file 
it will create one resource group for the Azure ML workspace containing the Azure Machine Learning workspace, 
Application Insights, Key vault, Log Analytics workspace and a Storage account.


# Contribute
TODO: It is a working example that can be built on. Possibly build out the MLops pipeline.


