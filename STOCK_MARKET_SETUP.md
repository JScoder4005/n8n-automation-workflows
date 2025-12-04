# Indian Stock Market Daily Report Bot

Get daily market summaries, top news, and investment insights delivered to your WhatsApp/Email after market close.

## Features

- 📈 Nifty 50 & Sensex performance
- 📰 Top 3 market news headlines
- 💹 Stocks to watch
- 📊 Sector performance
- ⏰ Delivered daily at 4 PM IST (after market close at 3:30 PM)
- 📅 Only on weekdays (Mon-Fri)

## Setup Steps

### 1. Get API Keys (All Free)

#### Alpha Vantage (Stock Data)
1. Go to: https://www.alphavantage.co/support/#api-key
2. Enter your email
3. Get your free API key
4. Free tier: 25 requests/day (enough for daily reports)

#### NewsAPI (Market News)
1. Go to: https://newsapi.org/register
2. Sign up for free account
3. Get your API key
4. Free tier: 100 requests/day

### 2. Import Workflow to n8n

1. Open n8n (http://localhost:5678)
2. Click menu → Import from File
3. Select `stock-market-workflow.json`
4. The workflow will be imported

### 3. Configure the Workflow

#### Schedule Trigger Node:
- Already set to run at **4:00 PM IST** on **weekdays only**
- Cron expression: `0 16 * * 1-5`
- (Mon-Fri, 4 PM after market closes at 3:30 PM)

#### Get Stock Data Node:
- Replace `YOUR_ALPHAVANTAGE_API_KEY` with your Alpha Vantage key
- You can change the stock symbol (default: RELIANCE.BSE)

#### Get Market News Node:
- Replace `YOUR_NEWSAPI_KEY` with your NewsAPI key
- Set to get Indian business news

#### Send to WhatsApp Node:
- Add your WhatsApp credentials (same as weather bot)
- Set recipient phone number

### 4. Customize Your Report

You can edit the "Format Report" node to include:
- Specific stocks you're tracking
- More/fewer news items
- Custom analysis
- Links to detailed reports

## Indian Market Data Sources

### Free APIs:
- **Alpha Vantage**: Global stocks including BSE/NSE
- **Yahoo Finance**: Indian market indices
- **MoneyControl RSS**: Indian market news
- **NSE India**: Official NSE data (limited)

### Stocks You Can Track:
- Nifty 50 index
- Sensex index
- Individual stocks: RELIANCE, TCS, INFY, HDFC, etc.
- Sector indices

## Example Report Format

```
📊 *Daily Market Report*
📅 04 Dec 2025

*Market Summary:*
• Nifty 50: 21,456 (+0.8%)
• Sensex: 71,234 (+1.2%)

*Top News:*
1. RBI keeps repo rate unchanged at 6.5%
2. IT sector rallies on strong Q3 results
3. FII inflows hit 3-month high

💡 *Happy Investing!*
```

## Next Steps

1. Get your API keys (5 minutes)
2. Import the workflow
3. Add API keys to the nodes
4. Test it manually first
5. Activate for daily reports!

## Upgrade Options

Later you can add:
- Email delivery (in addition to WhatsApp)
- Technical indicators (RSI, Moving Averages)
- Portfolio tracking
- Price alerts for specific stocks
- AI-powered analysis using ChatGPT API
