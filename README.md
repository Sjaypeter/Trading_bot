# AI Trading Bot

An intelligent automated trading system with AI-powered portfolio management capabilities. This bot executes systematic trading strategies on the Alpaca trading platform while providing real-time portfolio analysis through GPT-4 integration.

## Features

### 🤖 Automated Trading
- **Multi-Level Entry System**: Configure multiple price levels with customizable drawdown percentages
- **Systematic Position Building**: Automatically places limit orders at predetermined levels
- **Real-Time Order Management**: Monitors and manages open orders and positions
- **Paper Trading Support**: Safe testing environment using Alpaca's paper trading API

### 💬 AI Portfolio Manager
- **GPT-4 Integration**: Chat interface for portfolio analysis and insights
- **Risk Assessment**: Evaluates exposure across holdings
- **Strategy Recommendations**: Suggests adjustments based on market conditions
- **Real-Time Insights**: Analyzes current positions and pending orders

### 📊 Portfolio Tracking
- **Live Position Monitoring**: Track all active positions in real-time
- **Entry Price Tracking**: Records and displays average entry prices
- **P&L Monitoring**: Unrealized profit/loss tracking
- **Order Status**: View all open limit orders

## Screenshots

```
+--------------------------------------------------+
|  Symbol: [____]  Levels: [__]  Drawdown%: [__]  |
|                                    [Add Equity]  |
+--------------------------------------------------+
| Symbol | Position | Entry Price | Levels | Status|
|--------|----------|-------------|--------|-------|
| AAPL   |    3     |   150.25    | {...}  |  on   |
| TSLA   |    2     |   245.80    | {...}  |  off  |
+--------------------------------------------------+
|        [Toggle Selected]  [Remove Selected]      |
+--------------------------------------------------+
| AI Chat: [Type your question here...] [Send]    |
| You: How is my portfolio performing?             |
| AI: Based on your current positions...           |
+--------------------------------------------------+
```

## Installation

### Prerequisites
- Python 3.7+
- Alpaca Trading Account (Paper or Live)
- OpenAI API Key

### Required Packages
```bash
pip install tkinter
pip install alpaca-trade-api
pip install openai
```

### Setup

1. Clone the repository:
```bash
git clone https://github.com/yourusername/ai-trading-bot.git
cd ai-trading-bot
```

2. Configure API credentials in `bot.py`:
```python
# Alpaca API
key = "YOUR_ALPACA_API_KEY"
secret_key = "YOUR_ALPACA_SECRET_KEY"
BASE_URL = "https://paper-api.alpaca.markets/"  # Use paper trading

# OpenAI API
api_key = "YOUR_OPENAI_API_KEY"  # In chatgpt_response function
```

3. Run the application:
```bash
python bot.py
```

## Usage

### Adding a Trading System

1. **Enter Symbol**: Type the stock ticker (e.g., AAPL, TSLA)
2. **Set Levels**: Number of price levels for position building (e.g., 3)
3. **Set Drawdown**: Percentage decrease between levels (e.g., 2.5 for 2.5%)
4. **Click "Add Equity"**: System will be added in "off" status

### Activating Trading

1. Select an equity from the table
2. Click "Toggle Selected System" to turn it "on"
3. The bot will:
   - Place an initial market order
   - Calculate level prices based on entry and drawdown
   - Place limit orders at each level
   - Monitor and execute automatically

### AI Portfolio Analysis

Type questions in the chat interface such as:
- "How is my portfolio performing?"
- "What are my biggest risks?"
- "Should I adjust my positions?"
- "Analyze my current exposure"

## How It Works

### Trading Logic

1. **Initial Entry**: When activated, places a market order for 1 share
2. **Level Calculation**: Computes price levels using formula:
   ```
   Level Price = Entry Price × (1 - Drawdown% × Level Number)
   ```
3. **Order Placement**: Sets limit orders at each calculated level
4. **Position Building**: Executes orders as price reaches each level
5. **Continuous Monitoring**: Auto-updates every 5 seconds

### Example

```
Symbol: AAPL
Entry Price: $150.00
Levels: 3
Drawdown: 2%

Calculated Levels:
Level 1: $150.00 × (1 - 0.02 × 1) = $147.00
Level 2: $150.00 × (1 - 0.02 × 2) = $144.00
Level 3: $150.00 × (1 - 0.02 × 3) = $141.00
```

## File Structure

```
ai-trading-bot/
│
├── bot.py              # Main application file
├── equities.json       # Saved trading systems (auto-generated)
└── README.md          # Documentation
```

## Data Persistence

All trading systems are automatically saved to `equities.json` and persist between sessions. The file stores:
- Symbol configurations
- Entry prices
- Level prices
- Current positions
- System status (on/off)

## Safety Features

- **Paper Trading Default**: Uses Alpaca paper trading API by default
- **Manual Activation**: Systems start in "off" mode
- **Error Handling**: Comprehensive error catching and logging
- **Thread Safety**: Protected against race conditions

## Limitations & Disclaimers

⚠️ **IMPORTANT**: This is an educational project. 

- Not financial advice
- Use at your own risk
- Test thoroughly in paper trading before considering live trading
- Past performance doesn't guarantee future results
- Always do your own research and risk assessment

## Future Enhancements

- [ ] Stop-loss and take-profit levels
- [ ] Multi-timeframe analysis
- [ ] Backtesting capabilities
- [ ] Email/SMS notifications
- [ ] Advanced charting
- [ ] Multiple strategy templates
- [ ] Performance analytics dashboard

## Troubleshooting

### Common Issues

**"Invalid entry price -1"**
- Cause: No filled orders found for the symbol
- Solution: Ensure initial market order executes successfully

**Thread errors**
- Cause: Equity deleted while trading system is running
- Solution: Toggle system off before removing

**API errors**
- Cause: Invalid API keys or rate limiting
- Solution: Verify credentials and check API status

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License - feel free to use this project for learning and development.

## Acknowledgments

- Alpaca Markets for trading API
- OpenAI for GPT-4 integration
- Python community for excellent libraries

## Contact

Questions or feedback? Open an issue or reach out!

---

**Disclaimer**: Trading involves risk. This bot is for educational purposes. Always thoroughly test strategies and understand the risks before trading with real money.