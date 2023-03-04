
### ByBitMarketMaker (SimpleVox)

A Market Maker strategy is a type of algorithmic trading strategy that aims to provide 
liquidity to a financial market  by continuously buying and selling an asset.

Market Makers constantly place both buy and sell orders in an effort to earn the bid-ask spread. 
This strategy can help to smooth out price volatility, increase market depth, and reduce the risk of il-liquidity for traders.
Market Maker strategies use complex algorithms to determine the optimal size and timing of their orders, and can quickly adapt to changes in market conditions. 
This type of strategy is commonly used in high-frequency trading and can be employed by both individual traders and institutional investors.

You can explore and start this bot by typing ``botvox --vox=ByBitMarketMaker``

Example usage cli:
```bash
botvox --symbol=ADAUSDT --vox=ByBitMarketMaker --qty=50 --fee=0.01 
       --spread=0.0009 --key=FAKE_KEY --secret=FAKE_SECRET --life=true
```

### SmartAccumulateVox (SimpleVox)

This bot is inspired by the Market Maker Strategy however it designed to act as an Accumulator thus,
if you set ``----accumulate=quote`` the bot only executes long trades, to accumulate quote currency 
if you set ``----accumulate=base``  the bot would only execute short trades to accumulate base currency

You can explore and start this bot by typing ``botvox --vox=SmartAccumulateVox``

Example usage:
```bash
botvox --vox=SmartAccumulateVox --exchange=bybit 
      --symbol ADAUSDT --accumulate=quote 
      --amount=50  --profitPct=0.1 --fee=0.01 
      --key=FAKE_KEY --secret=FAKE_SECRET --life=true
```


### VoxEngine SuperTrend (VoxEngine)

The SuperTrend indicator is a technical analysis tool used to identify market trends and generate trading signals.
It uses a combination of the average true range and a simple moving average to generate a signal that
changes from bullish to bearish and vice versa based on price action.

The SuperTrend indicator is often used as a trend-following indicator and can help traders determine
the direction of the trend, as well as potential entry and exit points.

The bot is configurable to place either buy or sell orders to accumulate either the base or quote currency.
This can be done by using the ```--sidePreference=<long|short|biDirectional>``` command line flag.

You can explore and start this bot by typing ``botvox --vox=SuperTrend``

Example usage:
```bash
botvox --vox=VoxEngine --strategy=SuperTrend --backtest=true 
       --exchange=bybit --symbol=ADAUSDT --timeframe=15m 
       --amount=100  --profitPct=0.003 --fee=0.02 
       --key=FAKE_KEY --secret=FAKE_SECRET --life=true --interval=10
```


### VoxEngine RSITrend

RSI and Moving Average Based Strategy designed to buy when the RSI is oversold and sell when the RSI overbought.
It uses a simple moving Average as confirmation for possible Trades
The bot is configurable to place either buy or sell orders to accumulate either the base or quote currency.
This can be done by using the ```--sidePreference=<long|short|biDirectional>``` command line flag.

You can explore and start this bot by typing ``botvox --vox=RSITrend``

Example usage:
```bash
botvox --vox=VoxEngine --sidePreference=biDirectional 
       --strategy=RSITrend --backtest=true --exchange=bybit 
       --symbol=ADAUSDT --timeframe=5m --amount=100  
       --profitPct=0.01 --fee=0.02 --key=FAKE_KEY 
       --secret=FAKE_SECRET --life=true --interval=1

```


### VoxEngine SmartAccumulate

The SmartAccumulate Bot is a trading bot that places buy or sell orders at the current support or resistance levels of the chart.
The support and resistance levels are calculated using floor pivots.
The bot is configurable to place either buy or sell orders to accumulate either the base or quote currency.
This can be done by using the ```--sidePreference=<long|short|biDirectional>``` command line flag.

You can explore and start this bot by typing ``botvox --vox=SmartAccumulate``

Example usage:
```bash
botvox --vox=VoxEngine --sidePreference=long --strategy=SmartAccumulate 
       --backtest=true --exchange=bybit --symbol=ADAUSDT --timeframe=5m
       --amount=100  --profitPct=0.003 --fee=0.02 
       --key=FAKE_KEY --secret=FAKE_SECRET --life=true --interval=10
```
