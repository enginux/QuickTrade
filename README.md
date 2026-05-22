------------------------------------------------------------------------

# 📘 **QuickTrade – A Professional MT5 Trading Dashboard for WINDOWS**

**A professional-grade MetaTrader 5 panel that combines trade execution, real‑time risk management, and performance tracking – designed to enforce discipline and give you a quantifiable edge.**

------------------------------------------------------------------------

## 🚀 Overview

QuickTrade is an all‑in‑one trading assistant for MT5. The tool replaces chaotic manual entry and sloppy risk calculation with a visual, one‑click system that forces you to plan every trade **before** you enter. It transforms your chart into an interactive command center where you can:

- Plan every trade with precise entry, stop‑loss, take‑profit, and risk‑per‑trade (percentage or fixed USD).
- Execute market and pending orders (limit/stop) with one click.
- Manage open positions: close all/sell/buy, partial close, cancel pending, close only winners or losers.
- Apply automated and manual **Break Even** (moves SL to entry after a configurable profit) and **Trailing Stop** (manual or auto‑activation).
- Monitor **live performance metrics**:
  - Total unrealised P&L on your panel‑opened trades
  - Daily realized P&L, win rate (%), and open risk (total \$ risked)
  - Current drawdown from the daily peak equity
  - **Consistency Score** – alerts you when one trade dominates your daily result (\> target %)
- Persist all metrics across restarts and account switches (multi‑account safe).
- Choose from three color themes (Gold, Dark, Silver) and toggle sound alerts.

> **Core philosophy:** Plan your trade, then trade your plan. No impulsive market orders without pre‑defined SL/TP. The panel enforces a pre‑trade workflow and gives you instant feedback on risk and performance. Your edge isn’t just a strategy; it’s the discipline to follow it. QuickTrade keeps you accountable.

------------------------------------------------------------------------

## 📦 Installation

1.  Copy the `QuickTrade.ex5` file into your MT5 `File/Open Data Folder/MQL5/Services`folder.
2.  Open MetaTrader 5, go to **Navigator** → **Services**, right‑click and **Refresh**.
3.  Drag `QuickTrade` onto any chart (recommended: use a chart of the symbol you intend to trade).
4.  In your MT5, go to **Tools** → **Options**, under **Expert Advisors** tab **enable “Allow automated trading”** (the EA uses standard MT5 functions only).
5.  **Important:** The `QuickTrade` is locked to authorized account numbers. To run it on your own account, request for access to the email: **fundabrew\@gmail.com** or facebook: [**fb.me/iTrade.tools**](https://web.facebook.com/iTrade.tools "ITrade.Tools").

------------------------------------------------------------------------

## ⚙️ Input Parameters (Properties of QuickTrades)

| Input | Description |
|------------------------|------------------------------------------------|
| `InpMagic` | Unique Magic Number to identify trades opened by this panel (default 14091991). Do not change unless necessary. |
| `InpDefaultLots` | Fallback lot size when risk calculation is reset. |
| `InpRiskPercent` | Risk per trade as % of current balance (e.g., 1.0 = 1%). |
| `InpRiskUSD` | Fixed dollar risk per trade (used when Risk% = 0). |
| `InpSlippage` | Maximum slippage in points (10 = 1 pip for 5‑digit brokers). |
| `InpSound` | Enable/disable sounds on order execution / failure. |
| `InpLineWidth` | Thickness of the draggable Entry/SL/TP lines. |
| `InpEntryColor` | Color of Entry trend line. |
| `InpSLColor` | Color of Stop Loss trend line. |
| `InpTPColor` | Color of Take Profit trend line. |
| `InpTrailingPointsDist` | Distance (points) from price to trail the stop loss. |
| `InpConsistencyTarget` | Maximum allowed % of daily P&L from a single trade (default 20%). Exceeding this marks “(F)” in metrics. |

------------------------------------------------------------------------

## 🧭 How to Use – Daily Workflow

### 1️⃣ Set up your trade plan

Use the **ORDER SETTINGS** section: - **Entry Price**: type a value or click the input field after clicking the edit field (green “waiting” mode). - **Stop Loss / Take Profit**: type price or click input field. You can also enter the distance in **points** (SL Points / TP Points) and the panel will auto‑calculate the price. - **RR Ratio**: set reward:risk (e.g., 2.0 means TP is twice the SL distance). Click **AUTO TP** to set TP automatically.

### 2️⃣ Define your risk

- **Risk %** – % of current balance you are willing to lose on this trade.
- **Risk (USD)** – fixed dollar amount (overrides Risk% if \> 0).
- **Lot Size** – can be typed manually, or click **CALCULATE** to compute the correct lot size based on your SL distance and chosen risk.

> 🧠 *Pro tip:* Always use the CALCULATE button. It guarantees that every trade follows your fixed risk per trade – the cornerstone of long‑term profitability.

### 3️⃣ Execute the order

Choose your order type from the **EXECUTION** area: - **Market Buy / Sell** – immediate execution at current market price (entry price field is ignored). - **Buy/Sell Limit** – place pending order at a better price. - **Buy/Sell Stop** – place pending order at a worse price (breakout).

The panel will automatically validate stop distances against broker minimums and normalize lot size to your broker’s volume step.

### 4️⃣ Manage open positions

Use the **TRADE MANAGEMENT** buttons: - **CLOSE ALL / SELL / BUY** – close all, only sells, or only buys. - **LOSSES / WINS** – close only losing or winning positions. - **BREAK EVEN** (manual) - moves all stops at best price considering broker's minimum distance. - **TRAILING STOP** (manual) – moves SL to price minus `TrailingPointsDist` for buys, or price plus distance for sells. Can be applied any time. - **PARTIAL CLOSE** – halves the volume of each position. - **PENDING** – cancels all active pending orders.

### 5️⃣ Automated risk tools

Toggle **Auto Break Even ON** – the panel will continuously check each open trade; when floating profit exceeds the USD threshold, it moves SL to entry.

Toggle **Trailing Stop ON** – activates only when profit reaches the **activation USD** value. Afterwards, the stop trails price by `TrailingPointsDist`. Cooldown mechanism prevents excessive modifications.

### 6️⃣ Monitor your daily performance

The **METRICS DASHBOARD** (left side) shows:

- **TOTAL** – unrealized P&L of all panel trades on this symbol.
- **OPEN RISK** – sum of stop‑loss risk (in USD) for all open positions.
- **EQUITY / BALANCE** – live account data.
- **DAILY PNL** – realized profit/loss from today’s closed trades.
- **DRAWDOWN** – % drawdown from today’s highest equity.
- **WIN RATE** – winning trades / total closed today, with count.
- **CONSISTENCY** – largest winning trade as % of daily P&L. If it exceeds the `InpConsistencyTarget` (default 20%), you see **(F)** – a warning that you are relying on one lucky trade. Target **(P)** for consistent, repeatable performance. **(N/A)** – no profits or trades yet.
- **TIMER** – current server time.

All metrics are **per symbol** and **per account** and survive MT5 restarts (saved in global variables).

> 🧠 *Pro tip:* When switching accounts, make sure to delete or detach the QuickTrade tool from your current account before attaching it to the second account. Follow the same process when switching back to the first account.

------------------------------------------------------------------------

## 🔧 Advanced Features & Edge Enhancers

### Draggable Trade Levels

When **Show Trade Levels ON** is active, colored trend lines appear for Entry, SL, and TP. You can drag them directly on the chart – the edit fields update automatically. Useful for visual traders.

### Account Switching

The panel detects when you change the chart’s symbol or switch to a different account (e.g., demo ↔ live). It reloads the correct metrics for that account+symbol and refreshes the display.

### Consistency Score as a Psychological Tool

A common mistake: one huge win makes you overconfident, leading to oversized risks. The consistency metric flags this. Discipline means winning small and often, not relying on home runs. Keep your consistency above 80% (i.e., no single trade \>20% of daily P&L).

### Risk-First Position Sizing

Because the lot size is derived from your **SL distance** and fixed **risk %**, your risk per trade is constant regardless of volatility or account growth. This is the professional trader’s edge: **risk consistency**.

------------------------------------------------------------------------

## 📈 Practical Tips for Daily Use

1.  **Start each day** by checking the **DAILY PNL** and **DRAWDOWN** on the panel. If you are already down -2% of your account, consider reducing risk or stopping.
2.  **Before entering a trade**, always:
    - Set Entry, SL, and TP.
    - Verify RR ratio ≥ 1.5 (or your personal minimum).
    - Click **CALCULATE** – the lot size should adjust automatically.
3.  **Use Auto Break Even** after price moves 10–15 pips in your favor. This turns the trade into a “free trade” (no risk).
4.  **Use Trailing Stop** (auto) to lock in profits without watching the screen. Set activation at, say, +20 USD and trailing distance at 100 points.
5.  **If the consistency flag shows (F)** after a winning trade, reduce your next trade size or take a break. This usually indicates uneven performance. It often starts with an “F” rating during the first few trades because the system is still trying to balance and compare your results. Over time, the impact of one big trade gradually fades as it gets offset by smaller, more consistent trades.
6.  **At market close**, the metrics will reset automatically for the next day. The panel rebuilds today’s history from closed deals, so numbers remain accurate.

------------------------------------------------------------------------

## ⚠️ Troubleshooting & Maintenance Notes

| Problem | Possible Fix |
|---------------------------|---------------------------------------------|
| Panel does not appear | Check that you are on an **authorized account** (contact the developer). Also ensure automated trading is enabled. |
| “Order failed – Invalid stops” | Broker requires a minimum distance between price and stop. Increase your SL points. |
| Metrics show zero after restart | The QuickTrade saves data as Global Variables of the terminal. If you reset MT5’s global variables cache, data is lost. Rebuilding happens automatically after one closed trade. |
| Dragging trend lines does not update fields | Ensure **Show Trade Levels ON** is active and you drag from the line itself, not the handles. |
| Partial close does nothing | Your broker may not support partial closing, or the half volume is below the minimum lot size. |
| Account switching not working | The QuickTrade checks login every second. If you changed account via File → Login, wait a few seconds. |

## 📄 License & Disclaimer

This software is provided for educational and professional trading use. The author assumes no responsibility for financial losses incurred using this tool. Past performance does not guarantee future results. Always trade with risk capital only.

**Author:** Enginux\
**Version:** 1.0\
**Built for:** Windows MetaTrader 5 (build 4000+)
