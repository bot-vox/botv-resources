
## Commandline Interface

To use the BotVox Command Line Interface effectively, it's important to familiarize yourself with the common arguments across all scopes. 
However, it's important to note that the arguments may vary for different strategies and alerts as some may require additional arguments and flags. 

As a result, a comprehensive list of all possible command line arguments cannot be provided in this document.


| Argument    | Type    | Description                                                                                                     |   
|-------------|---------|-----------------------------------------------------------------------------------------------------------------|
| --install   | Boolean | Flag indicating the user wants to import a Custom Strategy into BotVox                                          |
| --list      | Boolean | List available (Strategies,Alerts,SimpleVox implementations, Exchanges, Exchange Details, Account Balances etc) |
| --help      | Boolean | Help Messages                                                                                                   |
| --config    | String  | Avoid annoying commandline arguments and simply provide a configuration to your Bots                            |
| --vox       | String  | Execution Context (see SimpleVox and VoxEngine to understand this better)                                       |
| --exchange  | String  | The Name Of the target exchange(binance, bybit,coinbase etc.)                                                   |
| --symbol    | String  | The Target Symbol (BTCUSDT,ADAUSDT,ETHUSDT) etc.                                                                |
| --timeframe | String  | Timeframe if the Execution Context relies on Candle data from a given timeframe                                 |
| --amount    | Number  | The Initial Starting amount of a Base Currency                                                                  |
| --profitPct | Number  | The Profit Target pct                                                                                           |
| --fee       | Number  | The Fee's an Exchange might charge for a trade                                                                  |
| --key       | String  | Your API Key ( This is never Stored or Shared)                                                                  |
| --secret    | String  | Your API Secret ( This is never Stored or Shared)                                                               |
| --life      | Boolean | Boolean value to indicate whether this is a life Bot or a Test Bot                                              |
| --interval  | String  | Configurable interval to poll and execute the Execution Context                                                 |

