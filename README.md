
# SniperBot-Solana-PumpSwap

A high-performance sniper bot built in Rust for the Solana blockchain, optimized for trading on DEXs like **Pump.fun** and **PumpSwap**. It leverages advanced strategies for real-time token monitoring and automated buy/sell execution.

---

## 🔧 Key Features

1. Real-time token tracking via Yellowstone gRPC
2. Automatic buy execution based on configurable price drop
3. Profit-taking and stop-loss management (with adjustable slippage)
4. Inverse trading strategy (buy when target sells)
5. Telegram integration for live control and notifications
6. Jito and ZeroSlot support for high-priority transactions

---

## 🧠 Technical Overview

- Real-time copy trading logic
- Configurable `.env` strategy settings
- Multi-phase sell logic (up to 7 steps)
- Scheduled execution with built-in timer
- Data persistence and smart recovery
- Blacklisting and bundle detection

---

## 📊 Advanced Selling Strategies

- Configurable TP/SL (Take Profit / Stop Loss)
- ATH tracking for retracement-based sells
- Step-by-step sell strategy using timers
- Private Logic (PL): custom sell paths ignoring target

---

## 🔁 Inverse Mode

- Buys when the tracked target sells
- Optionally switches to PL mode after buy

---

## ⏱ Timer Support

- Starts and stops bot on a time schedule
- Automatically sells remaining tokens on exit
- Handles manual restart scenarios safely

---

## 🧩 Architecture

| Module       | Description                                              |
|--------------|----------------------------------------------------------|
| `core`       | Token and transaction logic                              |
| `engine`     | Strategy engine, price tracking, monitor & timers        |
| `dex`        | DEX integrations (Pump.fun, PumpSwap)                    |
| `services`   | Telegram, Jito, ZeroSlot integration                     |
| `common`     | Logging, config, blacklist, filter utils                 |

---

## 💬 Telegram Commands

- `/start` – Start the bot
- `/settings` – Show and edit filters
- `/tokens` – Show tracked tokens
- `/sell <token_address> <percentage>` – Manual sell
- `/tp <token> <percent>` – Set take-profit
- `/sl <token> <percent>` – Set stop-loss

---

## ⚙️ .env Configuration

```env
# Telegram Settings
TELEGRAM_BOT_TOKEN="your_bot_token"
TELEGRAM_CHAT_ID="your_chat_id"

# Strategy Settings
MARKET_CAP_ENABLED=true
MIN_MARKET_CAP=8.0
MAX_MARKET_CAP=15.0

VOLUME_ENABLED=true
MIN_VOLUME=5.0
MAX_VOLUME=12.0

BUY_SELL_COUNT_ENABLED=true
MIN_NUMBER_OF_BUY_SELL=50
MAX_NUMBER_OF_BUY_SELL=2000

SOL_INVESTED=1.0
SLIPPAGE=2.0
TP_PERCENTAGE=40.0
SL_PERCENTAGE=15.0

LAUNCHER_SOL_ENABLED=true
DEV_BUY_ENABLED=true
BUNDLE_CHECK=true

INVERSE_MODE=ON
PRIVATE_LOGIC=ON
```

---

## ▶️ How to Run

### Build the bot

```bash
make build
```

### Start the bot

```bash
make start
```

### Stop the bot

```bash
make stop
```

### Run (dev mode)

```bash
cargo run
```

### Run test for dev wallet detection

```bash
cargo run -- --test-dev-wallet
```

---

## 🧱 Dependencies

- `tokio` – Async runtime
- `anchor_client` – Solana program access
- `yellowstone-grpc` – Real-time data stream
- `spl_token` – Token operations
- `reqwest`, `serde`, `colored` – Util libraries

---

## 🔐 Security

- Private key loaded via `.env` (never hardcoded)
- Blacklist logic to avoid malicious tokens
- Transaction simulation before execution
- Fail-safe and retry mechanisms built-in

---

## 🧑‍💻 Maintainer

Feel free to reach out for contributions, questions or partnerships:

- Telegram: [@FaceOFWood](https://t.me/FaceOFWood)
- Email: [bernardo@example.com](mailto:bernardo@example.com)

---

## ✅ Contributions

Pull requests are welcome. For major changes, open an issue to discuss what you’d like to change.

---

