# asterai Documentation

## Overview
Create, integrate and deploy your AI agents with asterai - a platform for 
developing and deploying modular AI agents and fully featured AI applications.

## What is asterai?
asterai is a platform for developing and deploying modular AI agents and fully
featured AI applications.

asterai lets you create an AI application such as an agent or assistant
and easily add integrations and features to it in a modular way.
Program custom features and logic with plugins, or click to instantly add
existing functionality from the plugin marketplace.

With asterai, you can write plugins using different programming languages, such
as AssemblyScript, a TypeScript-like language, and deploy them from your
terminal into your agent to instantly activate the plugin.

This allows you to expose application functionality to LLMs
(Large Language Models, such as ChatGPT's GPT-4)
as well as to other plugins.

From within a plugin, you have access to a wide range of tools out of the box
such as AI search, LLM calls, HTTP requests, WebSocket connections, and more,
allowing you to seamlessly integrate a powerful AI stack to your application.

asterai lets you focus on your app, saving your time by giving you all the
managed AI infra and tools you need in a simple way.

## Key Features of asterai
- Plugin-based, modular AI agent building framework
- AI search with a managed knowledge base and vector DBs
- SDK for building plugins
- SDK for querying agents: consume both structured data and natural language
- REST API endpoints for querying agents from any client
- CLI for deploying plugins
- Cloud console for managing agents

## What can I do with asterai?
Lots cool of things!

- make natural language an additional input type for your
  application
- integrate AI search to make your app more efficient
- easily build custom, reliable chatbots, assistants and AI agents
- create system workflows capable of handling natural language
- get instant access to AI tools without worrying about infrastructure or scaling


## Example use cases

### Knowledge Base and AI search
Upload files to a knowledge base and connect it to your agent so that it can
answer questions specific to your application.
Your agent can also perform authenticated actions for your users, such as
CRUD operations that would normally be used via buttons instead.

Or, with the knowledge base, return structured results to build an AI search
engine rather than an assistant or agent.
You can also do both, for different parts of your app, with the same knowledge
base.
That is, your search bar and chatbot can use the same underlying technology.

### Function Calls and Structured Outputs
Query your application from any environment using our REST API or our SDKs,
and consume structured outputs as well as natural language, allowing you to
show front-end widgets and triggering front-end function calls
alongside an AI assistant response.

For example, create an agent with a Weather plugin.
The plugin can respond with an object containing the city name and temperature,
allowing your front-end to consume that object to show a weather "widget"
along with the natural language provided by the LLM.
