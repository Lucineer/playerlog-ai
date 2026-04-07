<p align="center">
  <img src="https://raw.githubusercontent.com/Lucineer/capitaine/master/docs/capitaine-logo.jpg" alt="Capitaine" width="120">
</p>

<h1 align="center">playerlog-ai</h1>

<p align="center">An AI assistant for analyzing and optimizing your gameplay.</p>

<p align="center">
  <a href="#quick-start">Quick Start</a> ·
  <a href="#how-it-works">How it Works</a> ·
  <a href="#limitations">Limitations</a>
</p>

---

**Status:** [playerlog-ai.casey-digennaro.workers.dev](https://playerlog-ai.casey-digennaro.workers.dev) · Open source MIT · Runs on Cloudflare Workers

You can use this tool to review your match history and discuss strategy. It is a local AI agent that runs on your own Cloudflare Workers deployment. It does not use a central service or retain your data.

It operates as a single Cloudflare Worker. You fork the repository, provide your own API keys, and deploy a private instance.

### Quick Start

1.  Fork this repository.
2.  Clone your fork and navigate to it.
3.  Run `npx wrangler login` and log in with your Cloudflare account.
4.  Set your API keys as secrets:
    ```bash
    npx wrangler secret put GITHUB_TOKEN
    npx wrangler secret put DEEPSEEK_API_KEY
    ```
5.  Deploy: `npx wrangler deploy`.

Your copy is now running at your own `*.workers.dev` subdomain.

### How it Works

- **Self-contained:** The agent logic and UI are served from a single Worker file.
- **Multi-model:** Routes requests to the LLM API you configure (defaults to DeepSeek).
- **Session Context:** Maintains a short-term memory of your conversation within a browser session.
- **Data Safety:** Filters out usernames and IDs from your logs before sending data to the AI model.
- **Fleet Protocol:** Can request structured data, like patch notes, from other verified agents in the network using the CRP-39 protocol.

### Limitations

This tool relies on manual updates to its knowledge base (e.g., game patch notes). Its strategic advice is based on the data it has been provided and the reasoning capabilities of the underlying LLM you configure. It does not automatically scrape live game servers for real-time data.

---

**Attribution:** Superinstance & Lucineer (DiGennaro et al.).

<div>
  <a href="https://the-fleet.casey-digennaro.workers.dev">The Fleet</a> · <a href="https://cocapn.ai">Cocapn</a>
</div>