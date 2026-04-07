# PlayerLog.ai

You upload a game log. You get a breakdown. No login, no tracking, no waiting. It runs on a single Cloudflare Worker you deploy and control.

**Live Demo:** [playerlog-ai.casey-digennaro.workers.dev](https://playerlog-ai.casey-digennaro.workers.dev)  
**License:** MIT  
**Stack:** Cloudflare Workers (Zero Dependencies)

---

## Why This Exists
Existing log analyzers often require accounts, insert ads, or use your data for training. This tool gives you direct, private analysis without handing your replays to a third party. It's for players who want feedback, not friction.

---

## What It Does
1.  **Private Analysis.** Your log is processed only within your own deployed Worker using your API keys.
2.  **Confidence Scoring.** Suggestions include a 1-10 reliability score, so you know what's speculative.
3.  **Fully Modifiable.** All application logic is in one file (`src/index.js`). Change prompts, adjust scoring, or add game support directly.

---

## Quick Start (Fork-First)
You will deploy and own your instance.
1.  **Fork** this repository.
2.  Clone your fork locally and enter the directory.
3.  Run `npx wrangler login` to connect to Cloudflare.
4.  Set your required API keys as secrets:
    ```bash
    npx wrangler secret put GITHUB_TOKEN
    npx wrangler secret put DEEPSEEK_API_KEY
    ```
5.  Deploy with `npx wrangler deploy`.

Your instance is live at your `*.workers.dev` subdomain. All edits are made in `src/index.js`.

---

## How It Works
A single Cloudflare Worker serves the HTML frontend and processes POST requests. It scrubs personal data from logs, then routes the query to your configured LLM (DeepSeek, OpenAI, or compatible endpoint). It can fetch structured live data like patch notes via the Cocapn Fleet network.

### Core Functions
*   **Local Data Scrubbing:** Player names and IDs are removed before any external API call.
*   **Configurable LLM:** Use any provider with a compatible chat API.
*   **Session Context:** Maintains conversation history for follow-up questions during your browser session.
*   **Fleet Data:** Can pull live game data (e.g., win rates) from other agents using the CRP-39 protocol.
*   **Transparent Scoring:** Each suggestion is tagged with a confidence rating.

**One Specific Limitation:** Analysis depth is constrained by your chosen LLM's context window. Very long logs may be truncated, potentially missing early-game events.

The quality of advice depends on the LLM you configure and the clarity of the log provided.

---

<div style="text-align:center;padding:16px;color:#64748b;font-size:.8rem"><a href="https://the-fleet.casey-digennaro.workers.dev" style="color:#64748b">The Fleet</a> &middot; <a href="https://cocapn.ai" style="color:#64748b">Cocapn</a></div>