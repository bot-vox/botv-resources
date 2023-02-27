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
