An AI agent is an architecture that uses [[Large Language Model (LLM)]] to perform tasks autonomously.

Because LLM's are language models that only read prompts and generate responses, it needs extensions that allow it to integrate and work with other systems.

An agent is system that can perceive its environment, make decisions, and take actions to achieve goals. 
Unlike a traditional program that simply executes predefined instructions, an AI agent can be trained to analyze information, reason about it, and choose actions dynamically using one or more AI models.

The “environment” could be many things: a computer system, the internet, a database, a game world, or even a physical robot interacting with the environment.

### Real world uses

In a real world use, an AI system will be a trained language model that accepts a prompt from a user, the model will reason the prompt and decide if it needs to access outside tools such as databases and API's
If the model has the data to answer a prompt it will utilize it to generate a response, otherwise it will try to access and use additional tools to gather information from other sources.
It can be a local system (CPU data, Disk data, OS, local codebase etc..) or on the internet.

**Example:**

A model that has to provide current, up to forecast may not have the latest data locally, so it will have to access an outside weather API to get the latest forecast.
The way the model will access this remote API will be using an Agent.

### Additional cases

1. A model can aggregate data and use an agent to send emails.
2. A model can generate data in the correct format and the agent can send these requests to remote services.
3. A model can accept second party input and an Agent can evaluate if the input requires action escalation.
4. A model that lives in a system can accept a request from a customer and utilize an agent to fulfill his request (e.g. a User wants to change his subscription or payment plan).

## Tools

Tools are small programs or functions that an Agent uses to access other parts of the system for the LLM.
For a Kiosk Agent that provides helpful information to users, a Tool can be added that allows the LLM to query an existing Knowledge base or notify a human responder is case of abuse.

## Multi-Agent Systems

A Multi Agent system consists of multiple AI Agents working collectively to perform tasks on the behalf of a user.

There are 2 main patterns when working with multi-agent systems

1. Manager (Centralized, agents as tools): A central “manager” agent coordinates multiple specialized agents via tool calls, each handling a specific task or domain.
2. Decentralized (no manager, agents pass work between themselves): Multiple agents operate as peers, handing off tasks to one another based on their specializations.