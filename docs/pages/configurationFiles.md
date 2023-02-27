## Configuration Files

We Understand that BotVox Commandline Interface might be a little intimidating and complex, so 
to make things a little easier BotVox comes with a set of available Bot implementations.
We are aware of how Confusing Commandline usage can be so to make things super easy we are allowing users to start their bots
by providing a configuration file.

To get a look and feel for how a configuration file would look like type: ```botVox --list --items=configExamples```

The Output is a List of Configuration examples for many if not all integrated 
Strategy/Alert Bots plus some configuration for Utility Tools.



```js
[
  {
    symbol: 'ADAUSDT',
    vox: 'ByBitMarketMaker',
    qty: 50,
    fee: 0.01,
    spread: 0.0009,
    key: 'FAKE_KEY',
    secret: 'FAKE_KEY',
    life: true
  },
  {
    vox: 'SmartAccumulateVox',
    exchange: 'bybit',
    symbol: 'ADAUSDT',
    accumulate: 'quote',
    amount: 50,
    profitPct: 0.1,
    fee: 0.01,
    key: 'FAKE_KEY',
    secret: 'FAKE_KEY',
    life: true
  },
  {
    vox: 'SmartAccumulateVox',
    exchange: 'bybit',
    symbol: 'ADAUSDT',
    accumulate: 'base',
    amount: 50,
    profitPct: 0.1,
    fee: 0.01,
    key: 'FAKE_KEY',
    secret: 'FAKE_KEY',
    life: true
  },
  {
    vox: 'VoxEngine',
    strategy: './extensions/vox-strategies/SuperTrend',
    backtest: true,
    exchange: 'bybit',
    symbol: 'ADAUSDT',
    timeframe: '15m',
    amount: 100,
    profitPct: 0.003,
    fee: 0.02,
    key: 'FAKE_KEY',
    secret: 'JavaScript',
    life: true,
    interval: 10
  },
  {
    vox: 'VoxEngine',
    sidePreference: 'long',
    strategy: './extensions/vox-strategies/RSITrend',
    backtest: true,
    exchange: 'bybit',
    symbol: 'ADAUSDT',
    timeframe: '5m',
    amount: 100,
    profitPct: 0.01,
    fee: 0.02,
    key: 'FAKE_KEY',
    secret: 'FAKE_KEY',
    life: true,
    interval: 10
  },
  {
    vox: 'VoxEngine',
    sidePreference: 'short',
    strategy: './extensions/vox-strategies/RSITrend',
    backtest: 'true',
    exchange: 'bybit',
    symbol: 'ADAUSDT',
    timeframe: '5m',
    amount: 100,
    profitPct: 0.01,
    fee: 0.02,
    key: 'FAKE_KEY',
    secret: 'FAKE_KEY',
    life: true,
    interval: 10
  },
  {
    vox: 'VoxEngine',
    sidePreference: 'biDirectional',
    strategy: './extensions/vox-strategies/RSITrend',
    backtest: 'true',
    exchange: 'bybit',
    symbol: 'ADAUSDT',
    timeframe: '5m',
    amount: 100,
    profitPct: 0.01,
    fee: 0.02,
    key: 'FAKE_KEY',
    secret: 'FAKE_KEY',
    life: true,
    interval: 10
  },
  {
    vox: 'VoxEngine',
    sidePreference: 'long',
    strategy: './extensions/vox-strategies/SmartAccumulate',
    backtest: 'true',
    exchange: 'bybit',
    symbol: 'ADAUSDT',
    timeframe: '5m',
    amount: 100,
    profitPct: 0.003,
    fee: 0.02,
    key: 'FAKE_KEY',
    secret: 'FAKE_SECRET',
    life: true,
    interval: 10
  },
  /* List of Utility Tools*/
  { vox: 'Exchanges' },
  { vox: 'ExchangeDetails', exchange: 'binance' },
  { vox: 'IndicatorVox', action: 'indicators' },
  { vox: 'IndicatorVox', action: 'patterns' }

```

## Running Integrated Bots with Configuration Files

This Feature was introduced to remove the overhead of providing long strings of commandline 
arguments to the bot and allows the user to start Bots with ease with simple a simple command.

Example: ``botvox --vox=VoxEngine --config=path/to/a/strategy/bot-config.json``


### ByBitMarketMaker (SimpleVox)

A Market Maker strategy is a type of algorithmic trading strategy that aims to provide liquidity to a financial market
by continuously buying and selling an asset.

Market Makers constantly place both buy and sell orders in an effort to earn the bid-ask spread. This strategy can help to smooth out price volatility, increase market depth, and reduce the risk of illiquidity for traders. Market Maker strategies use complex algorithms to determine the optimal size and timing of their orders, and can quickly adapt to changes in market conditions. This type of strategy is commonly used in high-frequency trading
and can be employed by both individual traders and institutional investors.

You can explore and start this bot by typing ``botvox --vox=ByBitMarketMaker``

Example ``config.json``:

Create a Json file see example below

```js
{
    symbol: 'ADAUSDT',
    vox: 'ByBitMarketMaker',
    qty: 50,
    fee: 0.01,
    spread: 0.0009,
    key: 'FAKE_KEY',
    secret: 'FAKE_KEY',
    life: true
  }
```
save it as ```botvox-buyBitMarketMaker.json``` somewhere on your computer example ``users/USER_NAME/botvox/config/botvox-buyBitMarketMaker.json``.

Now you can run the ```ByBitMarketMaker``` Bot by invoking it with this command:

``botvox --config=users/USER_NAME/botvox/config/botvox-buyBitMarketMaker.json``

The bot is configurable to place either buy or sell orders to accumulate either the base or quote currency.
This can be done by using the ```--sidePreference=<long|short|biDirectional>``` command line flag.

### SmartAccumulateVox (SimpleVox)

This bot is inspired by the Market Maker Strategy however it designed to act as an Accumulator thus,
if you set ``----accumulate=quote`` the bot only executes long trades,
to accumulate quote currency if you set ``----accumulate=base`` the bot would only execute short trades to accumulate base currency_

You can explore and start this bot by typing ``botvox --vox=SmartAccumulateVox``


Example ``config.json``:

Create a Json file see example below

```js
 {
  vox: 'SmartAccumulateVox',
  exchange: 'bybit',
  symbol: 'ADAUSDT',
  accumulate: 'quote',
  amount: 50,
  profitPct: 0.1,
  fee: 0.01,
  key: 'FAKE_KEY',
  secret: 'FAKE_KEY',
  life: true
}
```
save it as ```botvox-SmartAccumulateVox.json``` somewhere on your computer example ``users/USER_NAME/botvox/config/botvox-SmartAccumulateVox.json``.

Now you can run the ```SmartAccumulateVox``` Bot by invoking it with this command:

``botvox --config=users/USER_NAME/botvox/config/botvox-SmartAccumulateVox.json``

### VoxEngine SuperTrend (VoxEngine)

The SuperTrend indicator is a technical analysis tool used to identify market trends and generate trading signals.
It uses a combination of the average true range and a simple moving average to generate a signal that
changes from bullish to bearish and vice versa based on price action.

The SuperTrend indicator is often used as a trend-following indicator and can help traders determine the direction of the trend,
as well as potential entry and exit points.

The bot is configurable to place either buy or sell orders to accumulate either the base or quote currency.
This can be done by using the ```--sidePreference=<long|short|biDirectional>``` command line flag.

You can explore and start this bot by typing ``botvox --vox=SuperTrend``

Example ``config.json``:

Create a Json file see example below

```js
 {
  vox: 'VoxEngine',
  strategy: './extensions/vox-strategies/SuperTrend',
  backtest: true,
  exchange: 'bybit',
  symbol: 'ADAUSDT',
  timeframe: '15m',
  amount: 100,
  profitPct: 0.003,
  fee: 0.02,
  key: 'FAKE_KEY',
  secret: 'JavaScript',
  life: true,
  interval: 10
}
```
save it as ```botvox-VoxEngine-SuperTrend.json``` somewhere on your computer example ``users/USER_NAME/botvox/config/botvox-VoxEngine-SuperTrend.json``.

Now you can run the ```VoxEngine-SuperTrend``` Bot by invoking it with this command:

``botvox --config=users/USER_NAME/botvox/config/botvox-VoxEngine-SuperTrend.json``

### VoxEngine RSITrend

RSI and Moving Average Based Strategy designed to buy when the RSI is oversold and sell when the RSI overbought.
It uses a simple moving Average as confirmation for possible Trades
The bot is configurable to place either buy or sell orders to accumulate either the base or quote currency.
This can be done by using the ```--sidePreference=<long|short|biDirectional>``` command line flag.

You can explore and start this bot by typing ``botvox --vox=RSITrend``

Example ``config.json``:

Create a Json file see example below

```js
{
  vox: 'VoxEngine',
  sidePreference: 'short',
  strategy: './extensions/vox-strategies/RSITrend',
  backtest: 'true',
  exchange: 'bybit',
  symbol: 'ADAUSDT',
  timeframe: '5m',
  amount: 100,
  profitPct: 0.01,
  fee: 0.02,
  key: 'FAKE_KEY',
  secret: 'FAKE_KEY',
  life: true,
  interval: 10
}
```
save it as ```botvox-VoxEngine-RSITrend.json``` somewhere on your computer example ``users/USER_NAME/botvox/config/botvox-VoxEngine-RSITrend.json``.

Now you can run the ```VoxEngine-RSITrend``` Bot by invoking it with this command:

``botvox --config=users/USER_NAME/botvox/config/botvox-VoxEngine-RSITrend.json``


### VoxEngine SmartAccumulate

The SmartAccumulate Bot is a trading bot that places buy or sell orders at the current support or resistance levels of the chart.
The support and resistance levels are calculated using floor pivots.
The bot is configurable to place either buy or sell orders to accumulate either the base or quote currency.
This can be done by using the ```--sidePreference=<long|short|biDirectional>``` command line flag.

You can explore and start this bot by typing ``botvox --vox=SmartAccumulate``

Example ``config.json``:

Create a Json file see example below

```js
 {
  vox: 'VoxEngine',
  sidePreference: 'long',
  strategy: './extensions/vox-strategies/SmartAccumulate',
  backtest: 'true',
  exchange: 'bybit',
  symbol: 'ADAUSDT',
  timeframe: '5m',
  amount: 100,
  profitPct: 0.003,
  fee: 0.02,
  key: 'FAKE_KEY',
  secret: 'FAKE_SECRET',
  life: true,
  interval: 10
}
```
save it as ```botvox-VoxEngine-SmartAccumulate.json``` somewhere on your computer example ``users/USER_NAME/botvox/config/botvox-VoxEngine-SmartAccumulate.json``.

Now you can run the ```VoxEngine-SmartAccumulate``` Bot by invoking it with this command:

``botvox --config=users/USER_NAME/botvox/config/botvox-VoxEngine-SmartAccumulate.json``
