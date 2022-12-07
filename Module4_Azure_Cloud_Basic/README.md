## EPAM Cloud&DevOps Fundamentals Autumn 2022
### Module 4 Azure Cloud Basic. Home task 4.

### HOME TASK

#### Prerequisites
1.	Create azure subscription
[0_0.png]
2.	Create azure devops organization
[0_1.png]
3.	Read information about github flow branching strategy
[0_2.png]
4.	terraform should be installed
[0_3.png]
5.	Terraform knowledge is also required to do the stuff
6.	Az cli should be installed
[0_4.png]


### Homework
### Part 1 – Configure application
1.	Create a service connection in a Azure DevOps project to your subscription
[1_1.png]
2.	Find a .net pet project for the experiments
[1_2.png]
3.	Build your app locally .net project via dotnet tool. dotnet restore/build/run
[1_3.png]
4.	Create an Azure DevOps repo
[1_4.png]
5.	Create a branching policy for you application. Added yourself as a reviewer - As branching strategy use a github flow (It will be applied by default when you strict commit to your main branch)
[1_5.png]

### Part 2 – Configure a pipeline to deploy infrastructure 
Below is describing on how to do it via terraform. If you want to use terraform you need to create service connection in manual way. Otherwise you won’t be able to deploy your iac – Navigate to the last section

### Terraform storage account 
1.	Create a separate resource group and deploy azure storage account
[1_6.png]
2.	Create a container with the name “tfstate” and remember the name. use portal settings    
In this storage account you will be store your tf state file
[1_7.png]

### Terraform preparation
1.	Create another repo to store devops code
[1_8.png]
2.	Create a folder terraform
[1_9.png]
3.	Add app service implementation 
[1_10.png]
[1_11.png]
[1_12.png]
[1_13.png]
4.	Integrate application insights with app service
[1_14.png]
[1_15.png]
5.	Updated backend “azurerm” according to the guide
[1_16.png]
[1_17.png]
[1_18.png]
6.	Run az login or Connect-AzAccount to connect the azure subscription from your local
7.	Run terraform apply to deploy infrastructure
[1_19.png]
[1_20.png]


### Create a terraform pipeline
1.	Create a yaml pipeline with the following steps: terraform install, terraform init, terraform plan/apply. Plan is an optional one
[1_21.png]
[1_22.png]
[1_23.png]
[1_24.png]
[1_25.png]
2.	Inside yaml pipeline add trigger to main branch. The scenario – when main is updated, pipeline should run automatically
[1_26.png]
3.	Added 3 steps – terraform install, terraform init, terraform plan/apply. Plan is an optional one. You may add it as 4th step
[1_27.png]
[1_28.png]
[1_29.png]



### Part 3 – Create a deploy pipeline to app service
1.	Add yml pipeline to the application folder
[1_30.png]
[1_31.png]
2.	Your pipeline structure should contain 2 stages. 1st – build, create zip archieve, and publish an artifact. 2nd – download an artifact and deploy it to azure app service
[1_31.png]
[1_32.png]
[1_33.png]
3.	To deploy .zip to app service use azure app service deployment task
[1_34.png]
[1_35.png]
[1_36.png]
