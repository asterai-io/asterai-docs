# asterai Documentation
This documentation book covers asterai's core features in this initial section,
followed by usage guides to get started with asterai step-by-step in the next
section.

It is recommended that this documentation is read in a book format, from start
to end.

## What is asterai?
asterai is a Framework as a Service (FaaS) for efficiently integrating
emerging AI technologies into existing applications.

With asterai, you are able to write a few lines of TypeScript-like code
(AssemblyScript), run a deployment command from your terminal and harness
the raw power of LLMs integrated into your existing application. 

With asterai, you can make natural language an additional input type for your
application.

### Core features
asterai provides the following features at its core:

1. A plugin-based, modular application building framework.
2. LLM endpoints: choose your preferred LLM for the job.
3. Vector DBs: add the magic of similarity search to your application.
4. An SDK for building your plugins
5. A CLI for deploying your plugins
6. A cloud console for managing your applications


## Why do I need asterai?
LLMs have several use cases.
The main use case of an LLM is an AI assistant, a.k.a. a chatbot

Building an AI assistant from scratch that reliably integrates to your application's context
and features is not a task that can normally be done within a day, or perhaps
even a week.
But with asterai, it can.

### Example use case
The following use case explains how asterai can be used in production.

Picture a digital art marketplace app.
You're logged in as a user.
You would like to purchase an abstract oil painting with specific colours.
For example, cyan and purple.
But the traditional search box is not showing any results to your query.
There are at least 2 ways you can use asterai to fix this problem:

1. Implement an AI assistant chatbox.
   The assistant is now able to parse the original user query and respond with
   the relevant art pieces.
   The user can even ask the assistant to add an art piece to their cart!
2. Enhance the legacy search box with AI: when the user executes their
   query, using natural language, tne app responds with the relevant pieces.

This use case uses two core features from asterai: LLMs and Vector DBs.
And, like any other asterai project, it is developed as a plugin.
