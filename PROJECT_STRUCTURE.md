Suggested clean project structure for a Flask + Microsoft Foundry AI agent application

Top-level layout (minimal, production-friendly):

```
README.md
.gitignore
requirements.txt
.env.example
computer-history-client/      # Flask app package (application code)
    ├── app.py               # Flask app entrypoint
    ├── agent_client.py      # Agent integration + client logic
    ├── config.py            # Configuration loader (from env)
    ├── routes/              # Blueprints / HTTP routes
    ├── services/            # Agent wrappers, Azure helpers
    ├── templates/           # Jinja2 HTML templates
    └── static/              # CSS / JS / images
screenshots/                 # Project screenshots for README
docs/                        # Optional: how-to, architecture, deployment notes
tests/                       # Optional: unit / integration tests
```

Files to keep in version control
- Application code: `computer-history-client/` (all .py, templates, static)
- Documentation: `README.md`, `PROJECT_STRUCTURE.md`, `docs/`
- Requirements: `requirements.txt`, `.env.example`

Files to exclude from version control (examples already in `.gitignore`)
- `.venv/` virtual environment
- `__pycache__/` and `*.pyc` build artifacts
- `.env`, `.env.*` local environment files containing secrets

Deployment notes
- Keep secrets out of the repo; use Azure Key Vault or CI/CD pipeline secrets
- Pin your `requirements.txt` for reproducible installs
- Add a small `Procfile` or GitHub Actions workflow in `docs/` for deployment steps
