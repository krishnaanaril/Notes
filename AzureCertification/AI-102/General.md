# AI 102 Topics

- The Language Understanding (LUIS) container loads your trained or published Language Understanding model.
- QnA Maker is a cloud-based Natural Language Processing (NLP) service that allows you to create a natural conversational layer over your data. It is used to find the most appropriate answer for any input from your custom knowledge base (KB) of information.
- The **Dispatch** takes representative utterances from your bot’s one or more LUIS models, and QnAMaker knowledge bases to build a machine-learned dispatch model that is used to route requests to the right component.
- Computer Vision resource will be used to generate captions of images automatically.
- The supported file types for training a Form Recognizer model are PDF, PNG, and JPEG, BMP, TIFF.
- Customer-managed keys (CMK) require an additional billable service, Azure Key Vault, which can be in a different region, but under the same subscription, as Azure Cognitive Search. 
- Enabling CMK encryption will increase index size and degrade query performance.
- You should create a private link with private endpoint.
- Private Endpoints for Azure Cognitive Search allow a client on a virtual network to securely access data in a search index over a Private Link. The private endpoint uses an IP address from the virtual network address space for your search service. Network traffic between the client and the search service traverses over the virtual network and a private link on the Microsoft backbone network, eliminating exposure from the public internet.
- Anomaly Detector is an AI service with a set of APIs, which enables you to monitor and detect anomalies in your time series data with little machine learning (ML) knowledge, either batch validation or real-time inference.
- When you create a QnAMaker resource, you host the data in your own Azure subscription. Azure Search is used to index your data.
- When you create a QnAMaker resource, you host the runtime in your own Azure subscription. App Service is the compute engine that runs the QnA Maker queries for you.
- To add a contributor to LUIS - n the Azure portal, find your Language Understanding (LUIS) authoring resource. It has the type LUIS.Authoring. In the resource's Access Control (IAM) page, add the role of contributor for the user that you want to contribute.
- To extract data from receipts using Form Recognizer and the SDK, while using a prebuilt model, you should use the `FormRecognizerClient` client and the `StartRecognizeReceiptsFromUri` method. The `StartRecognizeContentFromUri` method is used for general content recognition, not specifically for receipts.
- A multi-service resource references "Cognitive Services" as the offering, rather than individual services, with access granted through a single API key. 
- A private endpoint is a network interface that uses a private IP address from your virtual network. This network interface connects you privately and securely to a service powered by Azure Private Link. By enabling a private endpoint, you're bringing the service into your virtual network.
The service could be an Azure service such as:
    - Azure Storage
    - Azure Cosmos DB
    - Azure SQL Database
    - Your own service using a Private Link Service.
- Direct Line Speech is a robust, end-to-end solution for creating a flexible, extensible voice assistant. It is powered by the Bot Framework and its Direct Line
Speech channel, that is optimized for voice-in, voice-out interaction with bots.
- A knowledge store that's composed of tables in Azure Storage work best in Power BI. If the tables contain projections from the same skillset and projection group, you can easily "join" them to build table visualizations that include fields from related tables.
- Cognitive search indexing:
    - Retrievable: Include the category field in the search results.
    - Searchable: Ensure that users can search for words in the category field.
    - Facetable: Ensure that users can perform drill down filtering based on category.
- **Metrics Advisor** is a part of Azure Applied AI Services that uses AI to perform data monitoring and anomaly detection in time series data. The service automates the process of applying models to your data, and provides a set of APIs and a web-based workspace for data ingestion, anomaly detection, and diagnostics - without needing to know machine learning. Developers can build AIOps, predicative maintenance, and business monitor applications on top of the service.
- The API call you should perform to provide an output in complete sentences for users who are vision impaired is `describeImageInStreamAsync`. The describe feature of the Computer Vision API generates a human-readable sentence to describe the contents of an image.
- You can configure Cognitive Services resources to allow access only from specific subnets. The allowed subnets may belong to a VNet in the same subscription, or in a different subscription, including subscriptions belonging to a different Azure Active Directory tenant.
- Multivariate Anomaly Detection - If your goal is to detect system level anomalies from a group of time series data, use multivariate anomaly detection APIs.
- **Azure Stack Hub** is an extension of Azure that provides a way to run apps in an on-premises environment and deliver Azure services in your datacenter.
- The Eula, Billing, and ApiKey options must be specified to run the container; otherwise, the container won't start.
- The process for copying a project consists of the following steps:
    - First, you get the ID of the project in your source account you want to copy.
    - Then you call the ExportProject API using the project ID and the training key of your source account. You'll get a temporary token string.
    - Then you call the ImportProject API using the token string and the training key of your target account. The project will then be listed under your target account.
-  Customers can build custom Person models and enable Azure Video Indexer to recognize faces that are not recognized by default. Customers can build these Person models by pairing a person's name with image files of the person's face.
- The different face detection models are optimized for different tasks.
    - detection_02 -> Improved accuracy on small, side-view, and blurry faces.
- One option to manage your Computer Vision containers on-premises is to use Kubernetes and Helm. Using Kubernetes and Helm to define a Computer Vision container image, we'll create a Kubernetes package. This package will be deployed to a Kubernetes cluster on-premises.
- Document extraction, is a skill that extracts specific pieces of information from documents, but it does not address the challenge of recognizing and extracting text from handwritten letters.
- You can detect head gestures like nodding and head shaking by tracking HeadPose changes in real time. You can use this feature as a custom liveness detector.
- Liveness detection is the task of determining that a subject is a real person and not an image or video representation. A head gesture detector could serve as one way to help verify liveness, especially as opposed to an image representation of a person.
- The overall image quality regarding whether the image being used in the detection is of sufficient quality to attempt face recognition on. The value is an informal rating of low, medium, or high. Only "high" quality images are recommended for person enrollment, and quality at or above "medium" is recommended for identification scenarios.
- To minimize the time it takes to build the index for the documents and images in the Azure Storage account, the best approach would be to use parallel indexing.
- Configuring parallel indexing allows you to process multiple documents or images simultaneously.
- Smart Labeler to generate suggested tags for images. This lets you label a large number of images more quickly when training a Custom Vision model. But the exisiting model need to be extended and retrained.
- Requests to Translator are, in most cases, handled by the datacenter that is closest to where the request originated. If there's a datacenter failure when using the global endpoint, the request may be routed outside of the geography.
- To enable active learning, you must log user queries. This is accomplished by calling the endpoint query with the log=true query string parameter and value.
- A voice training dataset includes audio recordings, and a text file with the associated transcriptions. Each audio file should contain a single utterance (a single sentence or a single turn for a dialog system), and be less than 15 seconds long.
- A collection (.zip) of audio files (.wav) as individual utterances. Each audio file should be 15 seconds or less in length, paired with a formatted transcript (.txt).
- Bot Framework Emulator is a desktop application that allows bot developers to test and debug bots, either locally or remotely.
- **ngrok** is a cross-platform application that can create a tunneling or forwarding URL, so that internet requests reach your local machine. Use ngrok to forward messages from external channels on the web directly to your local machine to allow debugging, as opposed to the standard messaging endpoint configured in the Azure portal.
- The optional settings for a Q&A pair include:
    - Alternate forms of the question
    - Metadata
    - Multi-turn prompts
- Use Content Moderator's text moderation models to analyze text content, such as chat rooms, discussion boards, chatbots, e-commerce catalogs, and documents. The service response includes the following information:
    - Profanity: term-based matching with built-in list of profane terms in various languages
    - Classification: machine-assisted classification into three categories
    - Personal data
    - Auto-corrected text
    - Original text
    - Language
- Question answering provides multi-turn prompts and active learning to help you improve your basic question and answer pairs.
- Multi-turn `prompts` give you the opportunity to connect question and answer pairs. This connection allows the client application to provide a top answer and provides more questions to refine the search for a final answer.
- You can use the `tts.speech.microsoft.com/cognitiveservices/voices/list` endpoint to get a full list of voices for a specific region or endpoint.
- Within a search service, synonym maps are a global resource that associate equivalent terms, expanding the scope of a query without the user having to actually provide the term. For example, assuming "dog", "canine", and "puppy" are mapped synonyms, a query on "canine" will match on a document containing "dog".
- Azure Video Indexer supports automatic speech recognition through integration with the Microsoft Custom Speech Service. You can customize the Language model by uploading adaptation text, namely text from the domain whose vocabulary you'd like the engine to adapt to. Once you train your model, new words appearing in the adaptation text will be recognized, assuming default pronunciation, and the Language model will learn new probable sequences of words.
- The identity information you need to add depends on the bot's application type. Provide the following values in your configuration file.
    - MicrosoftAppId  -The bot's app ID.
    - MicrosoftAppPassword/App secret - The bot's app password.
- Properties associated with the active dialog. Properties in the dialog scope are kept until the dialog ends.
- Content Moderator's machine-assisted text classification feature supports English only, and helps detect potentially undesired content. The flagged content may be assessed as inappropriate depending on context. It conveys the likelihood of each category. The feature uses a trained model to identify possible abusive, derogatory or discriminatory language. This includes slang, abbreviated words, offensive, and intentionally misspelled words.
- Category1 refers to potential presence of language that may be considered sexually explicit or adult in certain situations.
- A trace activity is an activity that your bot can send to the Bot Framework Emulator. You can use trace activities to interactively debug a bot, as they allow you to view information about your bot while it runs locally.