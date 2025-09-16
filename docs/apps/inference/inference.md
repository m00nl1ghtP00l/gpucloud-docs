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


**Inference** is the process of using a trained AI/ML model to generate predictions from new data. It is central to machine learning workflows, enabling real time or batch decision making for use cases such as image classification, anomaly detection, or customer behavior prediction.

The platform provides an **Inference Endpoint Configuration** screen to deploy and manage models at scale. From a single interface, users can configure compute resources, API access, and cluster details without relying on separate tools or scripts. This streamlines model operationalization, ensuring consistency, scalability, and secure access for ML engineers and data scientists managing production or development environments.

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
