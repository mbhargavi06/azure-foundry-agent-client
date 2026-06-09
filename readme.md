# Azure Foundry Agent Client

Project overview

A full-stack AI agent application that demonstrates integrating a Microsoft Foundry Agent with a Flask backend and a browser-based chat UI. The repository contains a small Flask app (`computer-history-client/`) that authenticates with Azure and calls the Foundry Agent via the OpenAI Responses-compatible endpoint.

Architecture (text-based)

```text
Browser (templates/static)
    ↓
Flask backend (`computer-history-client/app.py`)
    ↓
Agent client (`computer-history-client/agent_client.py`)
    ↓
Microsoft Foundry Agent (via OpenAI Responses endpoint)
```

Features

- Interactive chat UI for multi-turn conversations
- Microsoft Foundry Agent integration
- Azure Entra ID authentication (uses environment configuration)
- Markdown rendering and sanitized output

Technology stack

- Python 3.10+
- Flask
- Microsoft Foundry / Azure AI (agent)
- OpenAI Responses-compatible API
- HTML / CSS / JavaScript (frontend)

Setup instructions

1. Create a Python virtual environment in the project root:

```bash
python -m venv .venv
```

2. Activate it and install dependencies:

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
pip install -r computer-history-client/requirements.txt
```

Running locally

1. Copy `computer-history-client/.env.example` to `computer-history-client/.env` and set the `AGENT_ENDPOINT` value (do not commit this file):

```text
AGENT_ENDPOINT=your_agent_endpoint_here
```

2. Authenticate with Azure (if using Azure credentials locally):

```bash
az login
```

3. Start the Flask app:

```bash
python computer-history-client/app.py
```

4. Open `http://localhost:5000` in your browser.

Screenshots

Place screenshots in the `screenshots/` folder. Example references used in the README:

![Chat UI](screenshots/chat_ui.png)
![Conversation Example](screenshots/conversation.png)

Project structure

See `PROJECT_STRUCTURE.md` for an expanded layout and recommendations.

Azure Foundry Agent configuration

- Use `computer-history-client/.env.example` as the template for environment variables. Keep real endpoints and keys out of source control. This repository previously contained a committed `.env` file with a real Foundry endpoint; that file has been removed.
- In production, prefer Azure Key Vault or pipeline secrets instead of `.env` files.

Keeping secrets out of the repo

- `.gitignore` contains entries to ignore `.venv/`, `__pycache__/`, `*.pyc`, `.env`, and `.env.*`. Ensure you never commit your `.env` or API keys.
- If you find secrets accidentally committed, rotate them immediately and remove them from git history.

Future improvements

- Streaming responses and partial rendering
- Persistent conversation storage (database)
- Authentication/authorization for users
- CI/CD pipeline and deployment to Azure App Service or Container Apps

Author

Bhargavi Manda

Contact / GitHub: https://github.com/mbhargavi06
