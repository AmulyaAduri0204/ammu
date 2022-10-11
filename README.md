Language Studio create

Language Studio is a set of UI-based tools that lets you explore, build, and integrate features from Azure Cognitive Service for Language into your applications.

Language Studio provides you with a platform to try several service features, and see what they return in a visual manner. It also provides you with an easy-to-use experience to create custom projects and models to work on your data. Using the Studio, you can get started without needing to write code, and then use the available client libraries and REST APIs in your application.

Get started using Language Studio
To use Language Studio, you will need an Azure Language resource for authentication. You can also use this resource to call the feature REST APIs and client libraries. Follow these steps to get started.

 Important

The setup process and requirements for custom features are different. If you're using one of the following custom features, we recommend using the quickstart articles linked below to get started more easily.

Conversational Language Understanding
Custom Text Classification
Custom Named Entity Recognition (NER)
Orchestration workflow
Create an Azure Subscription. You can create one for free.

Log into Language Studio. If it's your first time logging in, you'll see a window appear that lets you choose a language resource.
![image](https://user-images.githubusercontent.com/112709511/195116278-0d61108b-9491-4c32-8980-eb6e731aaf60.png)

Select Create a new language resource. Then enter information for your new resource, such as a name, location and resource group.

 Tip

When selecting a location for your Azure resource, choose one that's closest to you for lower latency.
We recommend turning the Managed Identity option on, to authenticate your requests across Azure.
If you use the free pricing tier, you can keep using the Language service even after your Azure free trial or service credit expires.
![image](https://user-images.githubusercontent.com/112709511/195116403-7ac32e93-4d11-4171-b0cb-e67e75cec8a8.png)
Select Done. Your resource will be created, and you will be able to try the different features offered by the Language service. For example, select Find linked entities.
![image](https://user-images.githubusercontent.com/112709511/195116529-1467bf1c-a0df-4cda-8fed-ac5dec495727.png)
This feature has a section for entering text, uploading a file, or choosing a text sample to demonstrate how the feature works. To try the demo, you will need to choose a resource and acknowledge it will incur usage according to your pricing tier
![image](https://user-images.githubusercontent.com/112709511/195116879-6c53c55a-9cbc-4ace-8aae-aff2e7bcd200.png)

6.After sending text, you'll be able to see a visualization, along with the JSON response. At the bottom of the page, you'll see next steps and the cURL command for the API request you just sent.
![image](https://user-images.githubusercontent.com/112709511/195116984-01ef6333-e794-455f-bb14-e8e12c9f8605.png)
Language Studio pre-configured features
The Language service offers multiple features that use prebuilt, pre-configured models for performing various tasks such as: entity linking, language detection, and key phrase extraction. See the Azure Cognitive Service for Language overview to see the list of features offered by the service.

Each of these features has a demo-like experience inside Language Studio that lets you input text, and presents the response both visually, and in JSON. These demos help you quickly test these prebuilt features without using code.

Language Studio customizable features
The Language service also offers multiple features that let you create, train, and deploy custom models to better fit your data. For example, custom content classification and custom question answering. For features with customization, Language Studio offers workflows that let developers and subject matter experts build models without needing machine learning expertise.


