The Model Context Protocol (MCP) is an open standard developed by Anthropic. It aims to standardize the integration of AI systems, particularly large language models (LLMs), with external tools, data sources, systems and AI model providers.

## What can MCP enable?

- Agents can access your Google Calendar using an MCP implemented by Google, acting as a more personalized AI assistant.
- Enterprise chatbots can connect to multiple databases across an organization, empowering users to analyze data using chat.
- AI models can create 3D designs on Blender and print them out using a 3D printer.

## Why does MCP matter?

Depending on where you sit in the ecosystem, MCP can have a range of benefits.

- **Developers**: MCP reduces development time and complexity by removing the need to write wrapper for external systems, the 3rd party implements an MCP and the developer integrates to it.
- **AI applications or agents**: MCP provides access to an ecosystem of data sources, tools and apps which will enhance capabilities and improve the end-user experience.
- **End-users**: MCP results in more capable AI applications or agents which can access your data and take actions on your behalf when necessary.

## Basic architecture

Today’s state-of-the-art LLMs use [deep learning](https://azure.microsoft.com/en-us/resources/cloud-computing-dictionary/what-is-deep-learning/) architectures like transformers and other deep neural network frameworks to process information from different data sources. Transformers are especially effective at handling sequential data, such as text, which allows them to understand and generate natural language for tasks such as language generation and translation. 

Transformers consist of two primary components: encoders and decoders. These components often work together to process and generate sequences. The encoder takes raw textual data and turns that input into discrete elements that can be analyzed by the model. The decoder then processes that data through a series of layers to produce the final output, which may, for instance, consist of a generated sentence. Transformers can also consist of encoders or decoders only, depending on the type of model or task.  

### Training process

The training process for LLMs consists of three main stages: data collection, model training, and fine-tuning. 

During the data collection phase, the model is exposed to large volumes of textual data from a wide variety of sources, including Internet resources, books, articles, and databases. The data is also cleaned, processed, standardized, and stored in a [NoSQL database](https://azure.microsoft.com/en-us/resources/cloud-computing-dictionary/what-is-nosql-database) so that it can be used to train the model on language patterns, grammar, information, and context.   

 In the pre-training phase, the model starts to build an understanding of the language in the data. This is accomplished through large-scale, unsupervised tasks where the model learns to predict text based on its context. Some techniques include autoregressive modeling, where the model learns to predict the next word in a sequence, as well as masked language modeling, where the model fills in masked words to understand the context.   

Lastly, during the fine-tuning phase, the model is further trained on a smaller, more task-specific dataset. This process refines the model's knowledge and enhances its performance for specific tasks, such as sentiment analysis or translation, so that it can be used for a variety of applications.  

### Components of MCP

|Component|Description|
|---|---|
|MCP Client|Resides within the AI application, facilitating communication with MCP servers.|
|MCP Server|External service that provides data or capabilities to the LLM.|
|Transport Layer|Utilizes JSON-RPC 2.0 for communication, supporting both local and remote resources.|

Source: https://modelcontextprotocol.io/docs/getting-started/intro