[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/hoangwiki-tcinvest-mcp-server-badge.png)](https://mseep.ai/app/hoangwiki-tcinvest-mcp-server)

# TCInvest MCP Server

This project is a Model Context Protocol (MCP) server for TCInvest, designed to help users build LLM-powered applications with real-time and historical stock and bond data from the TCBS APIs. The goal is to enable users to interact with financial data using large language models (LLMs), similar to how DeepSeek operates in the Chinese stock market—using LLMs to replace traditional brokers and provide intelligent, automated investment support.

## Purpose
- Enable seamless integration of LLMs (such as GPT, DeepSeek, etc.) with Vietnamese stock and bond data from TCBS.
- Allow users to query, analyze, and visualize financial data using natural language.
- Provide a foundation for building next-generation AI investment assistants and tools.
- Continuously expand features and API coverage to support more financial products and use cases.

## Features
- Retrieve stock and bond data from the TCBS API
- Loads configuration from a `.env` file
- Logs activity to `app.log`
- Designed for easy extension with new APIs and features

## Project Structure
```
tcinvest_mcp_server/
  __init__.py
  __main__.py
  constant.py
  requirements.txt
  server.py
  api/
    __init__.py
    client.py         # API client for TCBS endpoints
  services/           # Business logic for tcinvest api will be added here
    __init__.py
    bond_trading.py
  ...
.env                # Environment variables (API key, base URL)
app.log             # Log file
PYTHON_SDK_README.md
llms-full.txt
README.md
```
## Getting Started

### Installation

#### Install from PyPI

To install the package directly from PyPI, run:

```bash
pip install tcinvest-mcp-server
```

#### Install from Source

Alternatively, clone the repository and install the dependencies manually:

```bash
git clone https://github.com/hoangWiki/tcinvest_mcp_server.git
cd tcinvest_mcp_server
pip install -r requirements.txt
```

### Configuration

Set up your environment by copying the `.env` file and adding your `TCBS_API_KEY`:

```env
TCBS_API_KEY=your_api_key_here
```

### Running the Server

If installed from PyPI, you can start the server using:

```bash
python -m tcinvest_mcp_server --env path/to/your/.env
```

Or:

```bash
tcinvest-mcp-server --env path/to/your/.env
```

If installed from source, run:

```bash
python -m tcinvest_mcp_server --env path/to/your/.env
```
### MCP Client Setup - VsCode for example

To configure the MCP client, use the following JSON structure:

```json
{
  "servers": {
    "tcinvest": {
      "url": "http://localhost:8000/sse",
      "type": "sse"
    }
  }
}
```

- `url`: The endpoint for the TCInvest server. Replace `http://localhost:8000/sse` with the actual server URL if different.
- `type`: The connection type. For TCInvest, this is set to `sse` (Server-Sent Events).
- Ensure the server is running and accessible at the specified URL before using the client.
## Usage
- The server exposes MCP tools for bond data retrieval.
- Logs are written to `app.log`.

## Roadmap
- Add more TCBS API endpoints for stocks, funds, and other financial products
- Community contributions and feature requests welcome!

## Disclaimer
See `disclaim.md` for important legal and usage information.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
