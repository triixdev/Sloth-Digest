# SlothDigest

Two lines every morning. Paste your chats and get what happened and what to do today.
It runs on your own computer with the open model Gemma through Ollama.

## Website
The `site` folder is a static website. It talks only to Ollama on localhost.

    ollama pull gemma3:4b
    python3 -m http.server 8000 --directory site

Open http://localhost:8000 and press Load sample chats then Make my digest.

If you use the hosted site instead start Ollama like this with your own site address:

    OLLAMA_ORIGINS=https://your-site ollama serve

Use Chrome or Edge or Firefox. Safari blocks the connection to localhost from a hosted page.

## Command line

    pip install -r requirements.txt
    python digest.py --inbox sample

Put your real chats in `inbox` as .txt files. That folder is ignored by git.
The script writes `digest.md` and `digest.json`. Both are ignored by git.
Run it every morning at six with cron: `0 6 * * * cd /path/to/sloth-digest && python3 digest.py`

## Optional services
Both are off until you set a key yourself.
- Sentry tracing: set `SENTRY_DSN`. Sends timing and token counts only.
- ElevenLabs speech: run with `--speak` and set `ELEVENLABS_API_KEY`. Sends the final two lines.

Never commit keys. Use environment variables.

## Privacy and safety
- No analytics or cookies or accounts.
- A content security policy limits the page to connections with localhost.
- Output is written with textContent so model text can never run as code.
- Chat text is passed to the model as data with an instruction to ignore commands inside it.

## Deploy
Render reads `render.yaml` and publishes the `site` folder.

## License
MIT. See LICENSE.
