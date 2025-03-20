# Agentic ETL

This repository contains a collection of Cursor rules, helper scripts, and documentation to power a generalized agentic ETL process with minimal human intervention. The idea is to enable an automated AI agent to: 

1. Locate the most accessible and highest quality online data sources for information you want to retrieve
2. Determine the best way to extract the data using a combination of fetch requests, data APIs, sophisticated scraping systems, or LLM browser use
3. Design a JSON schema for chunking, extracting, or annotating the scraped information to turn it into usable structured data
4. Use LLM tools to perform the transformation according to the schema and save the results to JSON
5. Optionally upload the raw and/or structured JSON data to a database

This workflow is designed to power RAG pipelines, but can be used for any ETL process. 

## Workflow Documentation

Most ETL repositories on Github are mechanical software tools designed for a specific use case. This one is more like a generalized cookbook or recipe for an LLM-powered agent to follow for using existing tools to support a wider range of use cases. The workflow is designed to be executed by a Claude 3.7 Sonnet-powered Cursor Agent, with Cursor rules in the `.cursor/rules` directory and helpful scripts and documentation in the project root.

After presenting your use case to the agent, you should prompt the agent to follow the steps in the order listed below.

1. **Data Collection**
   - [`1-scraping.md`](workflow/1-scraping.md) - Scripted process for scraping or acquiring data
2. **Data Processing**
   - [`2-extracting-to-json.md`](workflow/2-extracting-to-json.md) - Scripted process for extracting scraped data to structured JSON

The workflow is supported by Cursor Rules in the `.cursor/rules` directory that provide additional context and guidelines for AI agents working with the codebase.

## Prerequisites

- [Cursor](https://www.cursor.com/)
- [Node.js](https://nodejs.org/en/download/)
- [uv](https://docs.astral.sh/uv/getting-started/installation/)
- [LLM CLI utility](https://llm.datasette.io/en/stable/)
- [Perplexity API Key](https://www.perplexity.ai/settings/api)
- Perplexity and Playwright MCP Tools - Put the following in `File > Cursor Settings > MCP > Add new global MCP server`, replacing `your_perplexity_api_key` with your actual Perplexity API key:
   ```json
   {
      "mcpServers": {
         "perplexity-mcp": {
            "env": {
            "PERPLEXITY_API_KEY": "your_perplexity_api_key",
            "PERPLEXITY_MODEL": "sonar"
            },
            "command": "uvx",
            "args": [
            "perplexity-mcp"
            ]
         },
         "playwright": {
            "command": "npx",
            "args": ["-y", "@executeautomation/playwright-mcp-server"]
         },
         "taskmanager": {
            "command": "npx",
            "args": [
            "-y",
            "@chriscarrollsmith/mcp-taskmanager"
            ]
         }
      }
   }
   ```

## Contributing

If you'd like to contribute to this project, please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.


