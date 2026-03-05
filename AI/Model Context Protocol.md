MCP (Model Context Protocol) is an open-source standard for connecting AI applications to external systems. Using MCP, AI applications like Claude or ChatGPT can connect to data sources (e.g. local files, databases), tools (e.g. search engines, calculators) and workflows (e.g. specialized prompts)—enabling them to access key information and perform tasks.

## What can MCP enable?

- Agents can access your Google Calendar and Notion, acting as a more personalized AI assistant.
- Claude Code can generate an entire web app using a Figma design.
- Enterprise chatbots can connect to multiple databases across an organization, empowering users to analyze data using chat.
- AI models can create 3D designs on Blender and print them out using a 3D printer.

## Why does MCP matter?

Depending on where you sit in the ecosystem, MCP can have a range of benefits.

- **Developers**: MCP reduces development time and complexity when building, or integrating with, an AI application or agent.
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

### Key components

The transformer model breaks raw text down into smaller, basic units of text called tokens. Tokens may consist of words, parts of words, or even individual characters, depending on the use case. These tokens are then converted into dense numerical representations that capture order, semantic meaning, and context. These representations, called embeddings, are then passed through a stack of layers consisting of two sub-layers: self-attention and neural networks.

While both layers assist in converting text into a form that the model can process effectively, the self-attention mechanism is a key component to the transformer architecture. The self-attention mechanism is what permits the model to home in on different parts of a text sequence and dynamically weigh the value of information relative to other tokens in the sequence, regardless of their position. This mechanism is also what gives LLMs the capacity to capture the intricate dependencies, relationships, and contextual nuances of written language.

Source: https://modelcontextprotocol.io/docs/getting-started/intro