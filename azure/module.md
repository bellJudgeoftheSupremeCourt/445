lab
title	module
Enable Dynamic Configuration and Feature Flags
Module 04: Implement a secure continuous deployment using Azure Pipelines
Enable Dynamic Configuration and Feature Flags
Lab requirements
This lab requires Microsoft Edge or an Azure DevOps supported browser.

Set up an Azure DevOps organization: If you don't already have an Azure DevOps organization that you can use for this lab, create one by following the instructions available at Create an organization or project collection.

Identify an existing Azure subscription or create a new one.

Verify that you have a Microsoft account or a Microsoft Entra account with the Contributor or the Owner role in the Azure subscription. For details, refer to List Azure role assignments using the Azure portal and View and assign administrator roles in Azure Active Directory.

Lab overview
Azure App Configuration provides a service to manage application settings and feature flags centrally. Modern programs, especially those running in a cloud, generally have many distributed components. Spreading configuration settings across these components can lead to hard-to-troubleshoot errors during application deployment. Use App Configuration to store all the settings for your application and secure their accesses in one place.

Objectives
After you complete this lab, you will be able to:

Enable dynamic configuration.
Manage feature flags.
Estimated timing: 45 minutes
Instructions
Exercise 0: (skip if done) Configure the lab prerequisites
In this exercise, you will set up the prerequisites for the lab, which consist of a new Azure DevOps project with a repository based on the eShopOnWeb.

Task 1: (skip if done) Create and configure the team project
In this task, you will create an eShopOnWeb Azure DevOps project to be used by several labs.

On your lab computer, in a browser window open your Azure DevOps organization. Click on New Project. Give your project the name eShopOnWeb and choose Scrum on the Work Item process dropdown. Click on Create.
Task 2: (skip if done) Import eShopOnWeb Git Repository
In this task you will import the eShopOnWeb Git repository that will be used by several labs.

On your lab computer, in a browser window open your Azure DevOps organization and the previously created eShopOnWeb project. Click on Repos > Files , Import. On the Import a Git Repository window, paste the following URL https://github.com/MicrosoftLearning/eShopOnWeb.git and click on Import:

The repository is organized the following way:

.ado folder contains Azure DevOps YAML pipelines.
.devcontainer folder container setup to develop using containers (either locally in VS Code or GitHub Codespaces).
infra folder contains Bicep&ARM infrastructure as code templates used in some lab scenarios.
.github folder container YAML GitHub workflow definitions.
src folder contains the .NET 8 website used on the lab scenarios.
Task 3: (skip if done) Set main branch as default branch
Go to Repos > Branches.
Hover on the main branch then click the ellipsis on the right of the column.
Click on Set as default branch.
Exercise 1: (skip if done) Import and run CI/CD Pipelines
In this exercise, you will import CI/CD pipelines to build and deploy the eShopOnWeb application. The CI pipeline is already prepared to build the application and run tests. The CD pipeline will deploy the application to an Azure Web App.

Task 1: Import and run the CI pipeline
Let's start by importing the CI pipeline named eshoponweb-ci.yml.

Go to Pipelines > Pipelines.
Click on Create Pipeline button (if there are no pipelines) or New pipeline button (if there are already created pipelines).
Select Azure Repos Git (Yaml).
Select the eShopOnWeb repository.
Select Existing Azure Pipelines YAML File.
Select the main branch and the /.ado/eshoponweb-ci.yml file, then click on Continue.
Click the Run button to run the pipeline.
Your pipeline will take a name based on the project name. Let's rename it for identifying the pipeline better. Go to Pipelines > Pipelines and click on the recently created pipeline. Click on the ellipsis and Rename/Remove option. Name it eshoponweb-ci and click on Save.
Task 2: Import and run the CD pipeline
Let's import the CD pipeline named eshoponweb-cd-webapp-code.yml.

Go to Pipelines > Pipelines.

Click on New pipeline button.

Select Azure Repos Git (Yaml).

Select the eShopOnWeb repository.

Select Existing Azure Pipelines YAML File.

Select the main branch and the /.ado/eshoponweb-cd-webapp-code.yml file, then click on Continue.

In the YAML pipeline definition, customize:

YOUR-SUBSCRIPTION-ID with your Azure subscription id.
az400eshop-NAME replace NAME to make it globally unique.
AZ400-EWebShop-NAME with the resource group name defined before in the lab.
Click on Save and Run and wait for the pipeline to execute successfully.

Note: You must click Save and Run twice. If the Jobs window displays a permission needed message, select Deploy from the Jobs window, select View, and then Permit twice to complete the pipeline run.

Note: The deployment may take a few minutes to complete.

The CD definition consists of the following tasks:

Resources: it is prepared to automatically trigger based on CI pipeline completion. It also downloads the repository for the bicep file.
AzureResourceManagerTemplateDeployment: Deploys the Azure Web App using bicep template.
Your pipeline will take a name based on the project name. Let's rename it for identifying the pipeline better. Go to Pipelines > Pipelines and click on the recently created pipeline. Click on the ellipsis and Rename/Remove option. Name it eshoponweb-cd-webapp-code and click on Save.

Exercise 2: Manage Azure App Configuration
In this exercise, you will create the App Configuration resource in Azure, enable the managed identity and then test the full solution.

Note: This exercise doesn't require any coding skills. The website's code implements already Azure App Configuration functionalities.

If you want to know how to implement this in your application, please take a look at these tutorials: Use dynamic configuration in an ASP.NET Core app and Manage feature flags in Azure App Configuration.

Task 1: Create the App Configuration resource
In the Azure Portal, search for the App Configuration service
Click Create app configuration then select:
Your Azure Subscription.
The Resource Group created previously (it should be named AZ400-EWebShop-NAME).
The location.
A unique name like appcs-NAME-REGION for example.
Select the Free pricing tier.
Click on Review + create then Create.
After creating the App Configuration service, go to Overview and copy/save the value of the Endpoint.
Task 2: Enable Managed Identity
Go to the Web App deployed using the pipeline (it should be named az400-webapp-NAME).
In the Settings section, click on Identity then switch status to On in the System Assigned section, click save > yes and wait a few seconds for the operation to finish.
Go back to the App Configuration service and click on Access control then Add role assignment.
In the Role section, select App Configuration Data Reader.
In the Members section, check Manage Identity, then click + Select members. In the Managed Identity field, select App Service (1), select your app service, then click Select.
Click on Review and assign twice to complete the role assignment.
Task 3: Configure the Web App
In order to make sure that your website is accessing App Configuration, you need to update its configuration.

Go back to your Web App.

In the Settings section, click on Environment Variables.

Add two new application settings:

First app setting
Name: UseAppConfig
Value: true
Second app setting
Name: AppConfigEndpoint
Value: the value you saved/copied previously from App Configuration Endpoint. It should look like https://appcs-NAME-REGION.azconfig.io
Click Apply then Confirm and wait for the settings to be updated.

Go to Overview and click on Browse

At this step, you will see no changes in the website since the App Configuration doesn't contain any data. This is what you will do in the next tasks.

Task 4: Test the Configuration Management
In your website, select Visual Studio in the Brand drop-down list and click on the arrow button (>).
You will see a message saying "THERE ARE NO RESULTS THAT MATCH YOUR SEARCH". The goal of this Lab is to be able to update that value without updating the website's code or redeploying it.
In order to try this, go back to App Configuration.
In the Operations section, select Configuration Explorer.
Click on Create > Key-value then add:
Key: eShopWeb:Settings:NoResultsMessage
Value: type your custom message
Click Apply then go back to your website and refresh the page.
You should see your new message instead of the old default value.
Task 5: Test the Feature Flag
Let's continue to test the Feature manager.

In order to try this, go back to App Configuration.

In the Operations section, select Feature manager.

Click on Create then add:

Enable feature flag: Checked
Feature flag name: SalesWeekend
Click Apply then go back to your website and refresh the page.

You should see an image with text "ALL T-SHIRTS ON SALE THIS WEEKEND".

You can disable this feature in App Configuration and then you would see that the image disappears.

[!IMPORTANT] Remember to delete the resources created in the Azure portal to avoid unnecessary charges. Be sure to disable the eshoponweb-cd-webapp-code pipeline or it will re-create a deleted resource group and associated resources after the next run of eshoponweb-ci.

Review
In this lab, you learned how to dynamically enable configuration and manage feature flags.
