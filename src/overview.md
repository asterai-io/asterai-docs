# asterai Documentation

## Overview
Create, integrate and deploy your AI agents with asterai - a platform for 
developing and deploying modular AI agents and fully featured AI applications.

## What is asterai?
asterai is a platform for developing and deploying modular AI agents and fully
featured AI applications.

asterai lets you create an agent or AI app and add features to it easily.
Program custom features and logic with plugins, or click to instantly add
existing functionality from the plugin marketplace.

With asterai, you can write plugins using different programming languages, such
as AssemblyScript, a TypeScript-like language, and deploy them from your
terminal into your agent to instantly activate the plugin.

This allows you to expose application functionality to LLMs
(Large Language Models, such as ChatGPT's GPT-4)
as well as to other plugins.

For example, your agent can fetch data from a knowledge base from files you
upload to let it answer questions based on your specific app.
Your agent can also perform authenticated actions for your users, such as
CRUD operations that would normally be used via buttons instead.

From within a plugin, you have access to a wide range of tools out of the box
such as AI search, LLM calls, HTTP requests, WebSocket connections, and more,
allowing you to seamlessly integrate an AI stack to your application.

asterai lets you focus on your app, saving your time by giving you all the
managed AI infra and tools you need in a simple way.

## Key Features of asterai
* Plugin-based, modular AI agent building framework
* AI search with a managed knowledge base and vector DBs
* SDK for building plugins
* SDK for querying agents: consume both structured data and natural language
* REST API endpoints for querying agents from any client
* CLI for deploying plugins
* Cloud console for managing agents

## What can I do with asterai?

With asterai, you can:

- make natural language an additional input type for your
application
- integrate AI search to make your app more efficient
- efficiently build custom, reliable chatbots
- create system workflows using AI agents for handling data in a structured way
- get instant access to AI tools without worrying about infrastructure or scaling

### Example use case
The following use case explains how asterai can be used in production.

Picture a digital art marketplace app.
You're using that app, and you are logged in.
You would like to purchase an abstract oil painting with specific colours.
For example, cyan and purple.
But the traditional search box is not showing any results to your query.
There are at least 2 ways you can use asterai to fix this problem:

1. Implement an AI assistant chatbox.
   The assistant is now able to parse the original user query and respond with
   the relevant art pieces.
   The user can even ask the assistant to add an art piece to their cart!
2. Enhance the legacy search box with AI: when the user executes their
   query, using natural language, the app responds with the relevant pieces.

This use case uses two core features from asterai: LLMs and Vector DBs.
And, like any other asterai project, it is developed as a plugin.
