# Get Started

> [!NOTE]
> As you follow the instructions in this pane, whenever you see a `icon`, you can use it to copy text from the instruction pane into the virtual machine interface. This is particularly useful to copy code; but bear in mind you may need to modify the pasted code to fix indent levels or formatting before running it!

## Sign in to Windows

1. Sign in to your VM with the following credentials:

    - **Username: ++@lab.VirtualMachine(Win11-Pro-Base-VM).Username++**

    - **Password: +++@lab.VirtualMachine(Win11-Pro-Base-VM).Password+++**

## Table of contents

1. [Part 0 - Sign in to Azure and setup Azure resources](/instructions/part-0-setup-azure-resources.md)
2. [Part 1 - Connect to your Azure HorizonDB database using VS Code Extension for PostgreSQL](/instructions/part-1-connect-horizondb-to-vscode.md)
    1. [Open VS Code and set up database connection to Azure PostgreSQL](/instructions/part-1-connect-horizondb-to-vscode.md#open-vs-code-and-set-up-database-connection-to-azure-postgresql)
    2. [Create Connection](/instructions/part-1-connect-horizondb-to-vscode.md#create-connection-to-horizondb)
    3. [Explore VS Code Extension for PostgreSQL Dashboard](/instructions/part-1-connect-horizondb-to-vscode.md#explore-vs-code-extension-for-postgresql-dashboard)
3. [Part 2 and 3 - Data Setup and Agentic App Development](/instructions/part-2-3-data-setup-agentic-development.md)

## Overview

In this lab, you will build an **agentic Compliance Advisor application** end to end, powered by a single **Azure HorizonDB** (Postgres) instance acting as your relational store, full-text search engine, vector database, graph database, **and** long-term memory store for the agent.

You will load a real U.S. case-law dataset, light up the AI extensions inside HorizonDB, and then assemble a Microsoft Agent Framework agent that combines **BM25 keyword search**, **vector similarity (DiskANN)**, **citation-graph traversal (Apache AGE)**, **in-database entity extraction (`azure_ai`)**, and an **external weather API** to write a real legal brief, with persistent memory across turns.

The lab is intentionally hands-on: every concept is paired with a runnable notebook cell, a Technical Background Notes block explaining what is happening underneath, and a short Tasks list telling you what to look at in the output.

## What you will build

- A **Microsoft Agent Framework** agent that can reason over U.S. case law stored in Azure HorizonDB.
- **Hybrid retrieval**: BM25 full-text search (`pg_textsearch`) combined with vector similarity search (`pgvector` + `pg_diskann` for ANN with advanced filtering).
- **GraphRAG** over a citation graph built with **Apache AGE**, letting the agent expand from anchor cases to surrounding precedents in a single Cypher-style traversal.
- **In-database entity extraction** with the `azure_ai` extension, so structured fields (`holding`, `issues`, `statutes_cited`, `disposition`) are pulled directly inside Postgres instead of round-tripping opinions back to the application.
- **External evidence ingestion** through a tool that calls the Open-Meteo weather archive API.
- **Long-term memory** with **Mem0**, where memory embeddings are stored back in the same HorizonDB instance using `pgvector`. No separate vector database.
- A **Gradio chat UI** that surfaces a live Tool Trace panel and the agent's growing memory store next to the conversation.

## Next Steps

> Start with Part 0 to sign in to Azure and set up your Azure resources.