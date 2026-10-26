# SlothDigest

Two lines every morning.

Line one says what happened. Line two says what to do today.

Paste your noisy group chats and press one button. Gemma writes the digest on your own computer.

## What makes it good

- **Private.** Your chats go to Ollama on localhost and nowhere else. A content security policy blocks every other connection.
- **Free.** No account. No key. No bill.
- **Offline.** Unplug the network and it still works.
- **Swappable.** Pick any model Ollama has installed. Gemma 3 is the default.
- **Safe.** Output is plain text. Commands hidden inside a chat are ignored.
- **Lazy.** Run it from a scheduler and read two lines instead of two hundred messages.

## Try it in two minutes

1. Install Ollama from ollama.com
2. Run `ollama pull gemma3:4b`
3. Download this repo and open a terminal in its folder
4. Run `python -m http.server 8000`
5. Open http://localhost:8000 in Chrome or Edge or Firefox
6. Click Load sample chats then Make my digest

Safari blocks the link to localhost from a web page so avoid it.

## Using the hosted site

A hosted page needs permission to reach Ollama. Quit Ollama first. Then start it with your site address.

Windows PowerShell:

    $env:OLLAMA_ORIGINS="https://your-site"; ollama serve

Mac or Linux:

    OLLAMA_ORIGINS=https://your-site ollama serve

## Command line version

1. Make a folder called `inbox`
2. Copy your chat exports into it as .txt files
3. Run `pip install -r requirements.txt`
4. Run `python digest.py`

It writes `digest.md` and `digest.json`. The three sample chats in this repo are good test files. Copy them into `inbox` first.

To run it every morning use cron on Mac and Linux or Task Scheduler on Windows.

## Optional services

Both stay off until you set a key yourself.

- **Sentry tracing.** Set `SENTRY_DSN`. It sends timing and token counts. Message text and file names are never sent.
- **ElevenLabs voice.** Run with `--speak` and set `ELEVENLABS_API_KEY`. It sends only the final two lines.

Never commit keys. Use environment variables.

## Safety choices

- No analytics and no cookies and no accounts
- Output is drawn with textContent so model text can never run as code
- Chat text goes to the model as data with a rule to ignore commands inside it
- Real chats and results are kept out of git by `.gitignore`
- A privacy policy and terms of service are included

## Built with

Gemma 3 and Ollama and plain HTML and CSS and JavaScript. The command line tool uses Python. The site is hosted on Render.

## License

MIT. See LICENSE.
