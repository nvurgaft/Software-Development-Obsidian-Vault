Here's a list of common workflows and patterns used when coding with AI models.

### Description/Specifications 

Provide the AI model with high-level requirement and it will turn them into an implementation plan.
An Implementation Plan is a document that covers all the steps, considerations and features the model proposes to implement.

Example:

Prompt the model to create a simple Snake game

```
> Write me a Snake like game using latest stable version of react js, use bootstrap for css. 
```

1. The model will create an implementation plan
2. It will generate a set of features to implement and will proceed to work on them
3. If the model encounters an error or a limitation, it will pause and ask the user to chose how to resolve the issue.
4. Continue, if any additional issue arises, repeat 3
5. An concrete implementation will be completed


### AI Pair Programming

A very common workflow, both the developer and the model program in a pair. 
In this approach, the developer keeps all responsibility and control, he does design, code review and corrects the model when needed.

No implementation plan needed, the user should know the correct design.

Example

```
> Implement a GET method using Spring Web, the url is "/user-details", the method also accepts and string query param of "username", it will return status 200 with the user data, if no use found return 404
```

The AI generates the implementation, and the developer reviews it.

### Codebase Q&A

Modern AI coding tools can index a repository and answer questions about the entire codebase.
Then you can ask the AI questions such as

```
Where is the user authentication handled ?
```

```
Where are the global error handlers for HTTP requests ?
```

This is extremely helpful when onboarding on an existing (big) project.