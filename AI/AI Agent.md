An AI agent is an architecture that uses [[Large Language Model (LLM)]] to perform goal-driven tasks autonomously. 

Because LLM's are language models that only read and generate text, it needs extensions that allow it to integrate and work with other systems.

An agent is system that can perceive its environment, make decisions, and take actions to achieve these goals. Unlike a traditional program that simply executes predefined instructions, an AI agent can analyze information, reason about it, and choose actions dynamically using one or more AI models.

The “environment” could be many things: a computer system, the internet, a database, a game world, or even a physical robot interacting with the real world.

### Real world use

In a real world use, an AI system will be a trained language model that accepts a prompt from a user, the model will reason the prompt and decide if it needs to access outside tools such as databases and API's, if the model has the data to answer a prompt it will utilize it to generate a response, otherwise it will try to access additional tools to gather information from someplace else.
It can be a local system (CPU data, Disk data, OS, local codebase etc..) or on the internet.

**Example:**

A model that has to provide current, up to data weather data will not have it locally in it's dataset, it will have to access an outside weather API to get the latest forecast.

### Additional cases

1. A model can aggregate data and use an agent to send emails.
2. A model can generate data in the correct format and the agent can send these requests to remote services.
3. A model can accept second party input and an Agent can evaluate if the input requires action escalation.
4. A model that lives in a system can accept a request from a customer and utilize an agent to fulfill his request (e.g. a User wants to change his subscription or payment plan).