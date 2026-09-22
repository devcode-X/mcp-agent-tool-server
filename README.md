# mcp-agent-tool-server

MCP (Model Context Protocol) server exposing reusable tools for agent-native API calls, SQLite database queries, and document retrieval. Integrated with a LangGraph agent client via LangSmith tracing and Pydantic-validated structured tool execution.

## Architecture

`
LangGraph Agent (Client)
        |
        v  MCP Protocol (SSE / Streamable HTTP)
MCP Tool Server  (FastAPI + FastMCP)
        |
        |-- query_db()       -> SQLite
        |-- api_call()       -> External REST APIs
        -- retrieve_doc()   -> Document store
`

## Features

- FastMCP server with tool discovery and Pydantic schema validation
- Retry middleware for transient tool failures
- LangSmith tracing for end-to-end agent observability
- LangGraph client with persistent state and checkpointing
- FastAPI with Streamable HTTP transport

## Quickstart

`ash
git clone https://github.com/devcode-X/mcp-agent-tool-server.git
cd mcp-agent-tool-server
pip install uv && uv sync
cp .env.example .env
uvicorn server.main:app --reload
`

## Tech Stack

Python · FastAPI · FastMCP · LangGraph · LangChain · SQLite · SQLAlchemy (async) · Pydantic · LangSmith

## Author

Devansh Awasthi — https://github.com/devcode-X
