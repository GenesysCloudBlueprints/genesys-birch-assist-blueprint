---
title: Integrating Birch Assist
author: 
indextype: blueprint
icon: blueprint
image: images/banner.png
category: 11
summary: |
  In this Genesys Cloud Developer Blueprint, Birch AI is used to automate complex after-call tasks. Our Live Call Analytics includes Task Tracking, Sentiment Tracking, Field Extraction, Pacing guidance, among others, as well as After-Call Work that includes summaries, reasons for the call, and classifications. 
---

:::{"alert":"primary","title":"About Genesys Cloud Blueprints","autoCollapse":false} 
Genesys Cloud blueprints were built to help you jump-start building an application or integrating with a third-party partner. 
Blueprints are meant to outline how to build and deploy your solutions, not a production-ready turn-key solution.
 
For more details on Genesys Cloud blueprint support and practices, 
see our Genesys Cloud blueprint [FAQ](https://developer.genesys.cloud/blueprints/faq "Goes to the Genesys Cloud Blueprint FAQ page") sheet.
:::

In this Genesys Cloud Developer Blueprint, Birch AI is used to automate complex after-call tasks. Our **Live Call Analytics** includes Task Tracking, Sentiment Tracking, Field Extraction, Pacing guidance, among others, as well as **After-Call Work** that includes summaries, reasons for the call, and classifications. 

For more information about Birch Assist setup, contact us [here](https://birch.ai/#footerscroll).

![Birch Assist Integration](images/genesys_birchai_workflow.png "Birch Assist Integration Overview")

## Scenario

A company wants to reduce handling time by automating the generation of draft after-call summaries and call classifications in the following ways:

- The agent interacts with the caller to understand and resolve customer issues.

- The call has ended. Using the organization's CRM system, the agent documents the customer's call and its purpose, the steps taken by the agent to resolve the problem, and any next steps.

- A CRM interaction is closed and the agent returns to the call queue.

## Solution components

* **Genesys Cloud CX** - A suite of Genesys Cloud services for enterprise-grade communications, collaboration, and contact center management. In this solution, you use the Genesys Cloud CX audio stream function.
* **BirchAssist** – A pre-trained generative AI model, BirchAssist automatically generates call summaries and classifications based on the style and quality of an organization’s existing documentation. It can be fine-tuned to meet virtually any organization’s needs. Medical device customer service, payers and providers clinical authorization calls, frontline health or life insurance customer service, and banking, utility, and telecommunications customer service are examples of use cases. 
* **Customer CRM** – BirchAssist automatically generates call summaries and classifications that are fed to the organization's CRM system via a two-way API. The BirchAssist agents review the auto-generated data, make necessary edits, and then BirchAssist captures the diff file for future model retraining. 
* **BirchAI services** – Most use cases require a small amount of configuration to emulate the organization’s desired summary language and style. Configuring this configuration is necessary to ensure that the downstream CRM system functions.

## Prerequisites

### Specialized knowledge

* Administrator-level knowledge of Genesys Cloud  
* Experience using the Genesys Cloud OAuth Process for third party apps

### Genesys Cloud account

A suite of Genesys cloud services for enterprise-grade communications, collaboration, and contact center management.

### BirchAI account

You need a BirchAI account to use the service.

### AudioHook integration

Live call streams require audio hook integration. 

## Deployment steps

The following steps are involved in Birch AI integration:

1. Create a custom Birch Assist role.
2. Create a Genesys Cloud Credentials OAuth Client for Birch. 
3. Set up your organization's integration with AudioHook. 
4. Contact Birch to link AudioHook to Birch Assist.

### Create a custom role for Birch Assist

1. Log into your Genesys Cloud organization and [Add roles](https://help.mypurecloud.com/articles/add-roles/ "Goes to the Add roles article") with the following permissions:

    * Analytics Agent Conversation Detail View
    * Analytics Conversation Detail View
    * Authorization Role View
    * OAuth Client View
    * Integrations Integration Edit

2. Assign the role to yourself

### Create a Client Credentials OAuth Client

1. Log in to your Genesys Cloud organization and [Create a Client Credentials OAuth Client](https://help.mypurecloud.com/articles/create-an-oauth-client/ "Goes to Create an OAuth client page").
2. In the Grant Types section, click on Client Credentials, and then the Roles tab.
3. Create the custom role and save it in the OAuth client.
4. Make a note of the Client ID and Client Secret.

:::primary
**Note:
If you have already set up AudioHook for your Genesys Cloud organization, skip this step.
:::

### Contact Birch team
1. You need to share the Client ID and Client Secret for the OAuth Client with the Birch Team.
2. You will be provided with a Connection URI once AudioHook is set up and ready to stream live audio.


Contact demo@birch.ai with questions regarding setup.
