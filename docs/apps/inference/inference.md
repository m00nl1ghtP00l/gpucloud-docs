---
title: Inference Endpoints
description: Lifecycle Management of Inference Endpoints
tags:
  - inference endpoints
  - machine learning inference
  - deploy ML models
  - inference API
  - inference deployment
  - model endpoints
  - inference configuration
  - ML model serving
  - real-time predictions
  - inference lifecycle management
---


**Inference** refers to the process of using a trained AI/ML model to make predictions based on new input data. It plays a crucial role in machine learning workflows, as it enables models to provide valuable insights and automate decision-making in real-time or batch scenarios. Inference can be applied across various use cases, such as predicting customer behavior, classifying images, or detecting anomalies, depending on the specific business problem being addressed.

For users, the ability to deploy and manage inference endpoints is essential when they need to operationalize their models and scale AI/ML services. Users typically rely on this feature to deploy trained models into production environments for real-time inference, test models in development settings, or adjust the scale of inference services to meet growing demand. By centralizing the deployment and configuration process, the platform simplifies the operationalization of machine learning workflows, ensuring consistency, scalability, and security.

The **Inference Endpoint Configuration** screen provides a seamless way to set up and manage inference endpoints. It offers a centralized interface to configure essential parameters, such as compute instances, API credentials, and cluster details. This eliminates the need for multiple tools and manual scripts, allowing users to define all necessary configurations in one place. The interface also integrates with existing clusters and cloud environments, optimizing resource utilization and enabling automation for tasks like blueprint application, scaling, and securing access via API keys. This functionality is ideal for ML engineers and data scientists who need a simple, efficient way to deploy, test, and scale their models across various environments.

---

## Create Inference Endpoints

To create an inference endpoint, access the **Developer Hub** and navigate to the home page. The page provides options to create and manage inference endpoints, which are predefined configurations designed to simplify and accelerate the deployment of machine learning models as APIs. These profiles enable rapid prototyping and real-time predictions. On the Developer Hub home page, users can either click on **View All** to access the Inference Endpoints page or click on **New Inference Endpoint** to create a new inference endpoint. Users can also click on the **Inference Endpoints** menu on the left to directly access the Inference Endpoints page.

![Hierarchy](img/inferences_homepage.png)

---

## New Inference Endpoint

To create a new Inference Endpoint,

- Select **Inference Endpoints** from the menu on the left of the console
- Click on **Inference Endpoints**
- Select a suitable inference service profile that suits your requirements

![Hierarchy](img/service-prof-list.png)

Once the profile is selected, provide the required details. If pricing for the selected profile is configured in [Global Settings](../csp/global_settings.md) by the Org Admin, a monthly estimate will be displayed.

- Provide a name for the Inference with an optional description
- Select the desired **Workspace** from the dropdown list
- Based on the configuration fields defined in the selected service profile and its associated template, users must provide the required details
- Click on **Deploy** to launch the service

![Hierarchy](img/inferences_inputs.png)

It can take a few minutes for the inference and associated software components to be deployed and ready for use.  

!!! info
    Users can deploy multiple inferences on an instance. The only constraint is whether the underlying instance has the resources required for all the inference.

- The instance initially displays a status of ***In Progress***. Upon successful deployment, the status updates to ***Success***

![Hierarchy](img/inferences_success.png)


---

## View Inferences

Clicking on the Inference Endpoints menu will list of all the inferences the user has access to. Note that inferences may span different workspaces and different instances. To view details about a specific inference, users just need to click on the name of the inference.

![Inference in Browser](img/inf_views.png)


---

## Delete Inference

To delete a Inference, users should click on the ellipses on the far right of the selected Inference and select delete.

![inference in Browser](img/delete_inferences.png)

!!! info
    Once deletion has been initiated, it cannot be stopped or reversed. Users can create a new Inference if required.

---
