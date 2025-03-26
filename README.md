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

1. **Data Collection** - The agent can reference the Bash or Python scraping rules for help with locating and scraping data.
2. **Data Processing** - The agent can reference the Bash or Python cleaning rules for help with transforming scraped data into clean JSON.
3. **Data Upload** - The agent can reference the Digital Ocean PostgreSQL setup and upload rules for help with setting up a database and uploading the data.

More languages, tools, and deployment options can be supported by adding additional Cursor rules to the `.cursor/rules` folder.

## Prerequisites

Before getting started, I highly recommend installing at least the following:

- [Cursor](https://www.cursor.com/)
- [Node.js](https://nodejs.org/en/download/)
- [uv](https://docs.astral.sh/uv/getting-started/installation/)

Your Cursor Agent will walk you through the setup process for any additional required tools and resources for your use case, or perhaps even obtain and install them itself.

## Contributing

If you'd like to contribute to this project, please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.


