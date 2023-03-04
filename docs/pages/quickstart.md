# Getting Started

## Installing BotVox Cli

to install BotVox globally open up any command prompt and type:

```bash
npm install -g botvox
```

## Invoking botvox 
Once Installation has finished type ``botvox`` on the commandline, you should see a commandline output like below:

![bv-1](https://github.com/bot-vox/botv-resources/blob/main/_resources/bv-1.png?raw=true)

## Understanding botvox execution context's
As you can see in above screenshots botvox provide 3 execution Contexts or flows,

* Vox ``--vox``
* Install ``--install``
* List ``--list``

If you are starting botvox with the ``--vox`` flag, botvox expects you supply an internal Execution Process or flow.

Execution or Process flows are just Javascript classes that live in the ``vox-vault`` i.e.
in:

1. ``botvox\vox-vault``
2. ``botvox\vox-vault\extensions\vox-strategies``
3. ``botvox\vox-vault\extensions\vox-alerts``

As a general thumb of rule

1. everything that lives in ``botvox\vox-vault`` is considered a Simple Vox and will be phased out in future releases

2. everything that lives in ``botvox\vox-vault\extensions\vox-strategies`` is considered a VoxEngine Strategy execution flow, meaning the ``--vox`` argument is supplied like this ``--vox=VoxEngine`` and needs to be followed by the ``--strategy`` flag to make sure the VoxEngine can pick up the target Strategy to execute!

3. everything that lives in ``botvox\vox-vault\extensions\vox-alerts`` is considered a VoxEngine Alert execution flow, meaning the ``--vox`` argument is supplied like this ``--vox=VoxEngine`` and needs to be followed by the ``--alert`` flag to make sure the VoxEngine can pick up the target Alerting implementation to execute!

To get a better sense on what is possible with botvox, we recommend to start exploring the cli by typing ```botvox --help```

![bv-2](https://github.com/bot-vox/botv-resources/blob/main/_resources/bv-2.png?raw=true)

# Core Concepts

Before we get started exploring botvox let us get familiar with a few core concepts.

## VoxEngine

This is really the Heart and Soul of BotVox, If you are leveraging the VoxEngine, using, developing and creating Strategies
is very Easy The VoxEngine will execute your Strategies and handle all Trading Activities for you based
on whatever you define in your Strategies.

It may sound a little confusing but its actually very simple.

``botvox --vox=VoxEngine``

is the command that tells bot vox to use the internal VoxEngine for the execution process,

the following ``--strategy=<path to Strategy>``or ``--alert=<path to Strategy>``

tells the VoxEngine to execute the logic in the Strategies or Notification Executions Contexts.

Don't worry if you don't yet fully understand this core concept, we will get into that a little deeper when we look at Creating new Custom Strategies or Notifications.


## SimpleVox

While SimpleVox may be useful for testing and creating standalone bots, it's not a recommended workflow.

**SimpleVox workflows will be phased out in the future** and all current implementations will be migrated to the Strategy domain or to utility command line tools. SimpleVox execution contexts are straightforward and don't typically require Kline candle imports or indicator data. The ByBitMarker and SmartAccumulateVox are examples of simple Vox instances.

At the time of writing, BotVox comes with a few preloaded SimpleVox implementations that serve as utility processes.

* ExchangeDetails
    * Prints out some important information about an Exchange
* Exchanges
    * Prints all available exchanges that can be used
* IndicatorVox
    * Prints out a List of Available Indicators and Candlestick Pattern that can be used inside a Strategy
* TradUtil
    * Utility to calculate Profit Targets, Stop Loss Limits, Show Available Balances etc.

Each of these has somewhat of a utility function baked in thus they are considered SimpleVox Execution Contexts
More on these later when we run through a few examples.


## Starting Your First Bot 

In order to start a new Bot, we need first decide what Bot We would like to run, we can get a good idea about installed bots by leveraging
the botvox command ``botvox --list --items=strategy``

Example output:

![bv-strategy](https://github.com/bot-vox/botv-resources/blob/main/_resources/bv-strategy-list.jpg?raw=true)

As you can see in above output there are already a few Bots that you can start using right away.

- RSIStrategy.js
- RSITrend.js
- SmartAccumulate.js
- StrategyTemplate.js
- SuperTrend.js
- RSIStrategy.js
- RSITrend.js
- SmartAccumulate.js
- StrategyTemplate.js
- SuperTrend.js

For this Quick Start we will be learning how to start The SuperTrend Trading bot. 
We can start this bot easily from the commandline in 2 ways.

1. Just provide all required Arguments on the commandline
2. Execute this Bot via a provided ``json`` configuration file.

But before we can use any of these methods we should know what arguments this bot requires botvox strategies usually 
have an option to list usage information in order to show an example command to start this bot enter
``botvox --vox=VoxEngine --strategy=SuperTrend --usage``

Example Output:

![bv-strategy](https://github.com/bot-vox/botv-resources/blob/main/_resources/bv-strategy-usage.jpg?raw=true)

``
--vox=VoxEngine --strategy=SuperTrend --backtest=true|false
--exchange=bybit --symbol=ADAUSDT --timeframe=15m
--amount=100  --profitPct=0.003 --fee=0.02
--key=FAKE_KEY --secret=FAKE_SECRET --life=true|false --interval=10
--sidePreference=long|short|biDirectional --period=7 --multiplier=3
``

Keep in mind that you need to make sure the entire command is executed as one-liner the output above is just for readability and cosmetics!

so the command you would be executing on the commandline looks a little more like this:

```bash
botvox --vox=VoxEngine --strategy=SuperTrend --backtest=true|false --exchange=bybit --symbol=ADAUSDT --timeframe=15m --amount=100  --profitPct=0.003 --fee=0.02--key=FAKE_KEY --secret=FAKE_SECRET --life=true|false --interval=10 --sidePreference=long|short|biDirectional --period=7 --multiplier=3
```

There is a lot of going on in this command so let's break down each commandline flag dow and explore what function they serve.

* ``--vox=VoxEngine``

  This flag indicates that we want to leverage the VoxEngine to manage Trade Activity for us

* ``--strategy=SuperTrend``

  This flag indicates that we want to use the SuperTrend Strategy 

* ``--backtest=true|false``

  This flag tells the VoxEngine wether we want to back test this Strategy or not no real trades are executed in this mode

* ``--exchange=bybit``

  This flag tells the VoxEngine to use bybit as the target exchange, botvox supports many exchanges you can find out what exchanges are supported 
  by entering running ``botvox --list --items=exchanges``

* ``--symbol=ADAUSDT``

  This flag tells the VoxEngine to execute trades for the ADAUSDT pair you can find out what Symbols are supported by either visiting the exchange or
  try ``botvox --vox=ExchangeDetails --exchange=bybit`` which will provide you with a detailed report about symbols and other exchange information 

* ``--timeframe=15m``

  This flag tells the VoxEngine to pull Candlestick data for a given period here it is 15m, but you can change it to whatever you want.
  try ``botvox --vox=ExchangeDetails --exchange=bybit`` to see all valid timeframes.

* ``--amount=100``

  This is the Amount of base currency you would like to enter for each trade execution, in this case ADA is our base currency so 100 ADA for each trade!  

* ``--profitPct=0.003`` 

  This is the profit Target you would like the VoxEngine to use before exiting your trades 

* ``--fee=0.02``

  Not really in play yet but this will be part of upcoming release we will integrate fee calculation to manage profit taking.

* ``--key=FAKE_KEY``

  This is important you need to have api access credentials to your exchange, visit your exchange to find out how to generate API access credentials 

* ``--secret=FAKE_SECRET``

  This is important you need to have api access credentials to your exchange, visit your exchange to find out how to generate API access credentials

* ``--life=true|false``

  Another important flag which tells the VoxEngine weather too mock trading or to execute real trades!

* ``--interval=10`` 
  
  This value is the interval for the Indicator Data look up and generation of new candles, the default is set to 1 minute, but you can change this interval to whatever you like.
  The Interval flag is a flag that tells the VoxEngine to poll new data and check Strategy results in certain intervals. 

* ``--sidePreference=long|short|biDirectional`` 
  
  This flag tells the Vox engine what your preferred Trade Side or direction is, if you specify long, only long trades will be executed, if you specify short only short trades will be executed.
  If you specify biDirectional bot long and short trades will be executed.
* ``--period=7``
* ``--multiplier=3``

  These are Strategy specific parameters if you are Familiar with the Super Trend Strategy and its implementation you know that it uses a period for averages and a multiplier for off setting bands.
  Those parameters are optional and default to 3 for the multiplier and 7 for the atr period. you can change them if you like.
 
