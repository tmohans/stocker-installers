# Stock-er

Your portfolio deserves better than tracking.

Stock-er is an AI portfolio manager for Indian investors. It reads the holdings you already have, debates every stock, and tells you what to do next: **Buy, Hold, or Sell**, lined up with your life goals. The product site is [stock-er.com](https://stock-er.com/).

It runs on your laptop. Broker tokens and AI keys stay on that machine.

## The old way

- You log in, stare at charts, and still feel unsure.
- Nothing tells you what to buy or sell next.
- Holdings are not checked against the life you are actually saving for.
- A heavy sector or a single oversized stock can sit there unnoticed.

## The Stock-er way

- You open the app and get clear actions: Buy, Hold, or Sell.
- Each call is tied to your timeline, risk appetite, and goals.
- Separate AI agents argue the case for and against every holding.
- Risk checks flag concentration and sector limits before a call stands.

In the desktop app, a buy is labeled **Buy More**. Sell and Hold use those words. Calls are sorted so Sell comes first, then Buy More, then Hold.

## How a decision is made

Stock-er does not send your portfolio to a single prompt and accept the first answer. A small committee of agents works in order, the same way the product describes a review before a recommendation:

1. **Profile.** Your age, retirement target, risk appetite, corpus, monthly surplus, and sector preferences are summarized into the brief every later agent sees.
2. **Bull and Bear.** Two agents argue each holding at the same time. One builds the case to keep or add. The other builds the case to trim or avoid.
3. **Review.** A third agent weighs those arguments and the market context, then chooses Buy More, Hold, or Sell, with a rationale and a confidence level.
4. **Risk.** Concentration and sector caps are checked against your limits. Risk can override an earlier call.
5. **Compare.** A separate pass splits new monthly savings across mutual funds, ETFs, stocks, and debt.

Without an AI key, the same screens still fill from a rule-based engine: concentration, sector, profit and loss, and how close you are to the retirement aim.

## What you can do

### Portfolio intelligence

Zerodha Kite and Dhan holdings sit in one portfolio. You see balance, allocation, and which names dominate the account. Groww has no public retail API, so those holdings are tracked by hand.

### Actions, not another chart

Each stock gets Buy More, Hold, or Sell, plus confidence and a written reason. The examples on [stock-er.com](https://stock-er.com/) (a Sell where one name is too large, a Buy where a stock fits the core plan) are the kind of call the pipeline is built to produce.

### Goals

Life goals are part of the input, not a sidebar. Retirement age, target corpus, risk appetite, and how much you can invest each month change the recommendations.

### SIP plan

The allocation view spreads new money across mutual funds, ETFs, stocks, and debt using that same profile. The site’s sample “target corpus” card is an illustration of this planning view, not a promised return.

### Stock discovery

When an AI key is configured, Stock-er can suggest names you do not already hold and rank them against the gaps in the current portfolio.

### Risk guardrails

You set a per-stock cap and sector preferences or restrictions. The app warns when a holding or a sector breaks those limits.

## What it is not

| Typical portfolio app | Stock-er |
| --- | --- |
| Data and charts | A decision on each holding |
| Static rules only | Agents that argue, then a risk check |
| Generic tips | Your goals, horizon, and caps |
| Passive tracking | A next action |

Stock-er is not a broker and it does not place orders. Kite access is read-only. It is not SEBI-registered investment advice. Treat every call as a starting point you still have to judge.

## Privacy

The desktop app is local. The interface and the API run on your computer, on port **3001**. Keys live in the app’s data folder, not in this repository. The screen shows masked previews of secrets.

This public repository only distributes the installer. Source code stays in the private project.

## Download

**Stock-er 2.5.2 for Windows**

[Stock-er.Setup.2.5.2.exe](https://github.com/tmohans/stocker-installers/releases/download/v2.5.2/Stock-er.Setup.2.5.2.exe)

The installer is unsigned, so Windows SmartScreen may warn before it opens. Choose **More info**, then **Run anyway**, if you trust this release.

The 2.5.2 package does not include a Zerodha API key, Kite secret, Dhan token, or any AI key. Life goals, the SIP amount, and per-stock horizons start empty.

## First launch

1. Install and open Stock-er.
2. If port 3001 is already in use, close the other program. The app needs that port so Zerodha can return to `http://localhost:3001/api/callback`.
3. In the [Kite developer console](https://developers.kite.trade/apps), create an app whose redirect URL is exactly:

   `http://localhost:3001/api/callback`

4. In Stock-er, open **Settings → Environment** and paste your own Kite API key and secret. Leave the redirect URL, frontend URL, and port as they are unless you know you need to change them.
5. Open **Settings → Brokers** and choose **Connect with Kite**. Approve read-only access on Zerodha. Kite sessions expire daily, so connect again when the app says the session has expired.
6. Optional: under **Brokers**, add a Dhan client ID and access token from Dhan → Profile → DhanHQ APIs. The app checks the token before saving it.
7. Optional: under **AI Agents**, add a Claude, OpenAI, or DeepSeek key. With no key, recommendations use the built-in rules.
8. Optional: under **Market Data**, add an [IndianAPI](https://indianapi.in) key for charts and market stats.
9. Under **Life Goals** and **SIP Plan**, enter your real numbers, then save. Re-run recommendations after you change them.

Until a broker is connected, the app can show a labeled sample portfolio so you can look around. That sample is not your Zerodha or Dhan account.

## Where settings live

On the installed app, settings and the optional `.env` file are in the user-data folder:

- Windows: `%APPDATA%\stocker\`
- macOS: `~/Library/Application Support/stocker/`
- Linux: `~/.config/stocker/`

Values you save in Settings override that file.

## Learn more

Product overview: [https://stock-er.com/](https://stock-er.com/)
