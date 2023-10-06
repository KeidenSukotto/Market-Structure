# Market Structure Indicator Script (TradingView Pine Script)

This script is designed to analyze and visualize market structure on price charts in the TradingView platform. It identifies trends, impulse waves, retracement phases, and break of structure (BOS) points. Below is a detailed breakdown of the code's components and logic:

## Variables

The script uses various variables to keep track of important data points:

- `trendDirection`: Tracks the current trend direction.
- `waveLeg`: Indicates whether the current phase is an "impulse" or "retracement."
- `trendHigh` and `trendLow`: Store the highest and lowest prices during a trend.
- `trendhighTime` and `trendlowTime`: Store the corresponding times for trend high and low.
- `previousCandle`: Stores data from the previous candle.
- `previouscandleTime`: Stores the time of the previous candle.
- `firstCandle`: Stores data from the first candle when the trend is not yet established.
- `firstcandletime`: Stores the time of the first candle.
- `trendnotEstablished`: A flag to indicate whether the trend has been established.
- `retracement_count` and `impulse_count`: Counters for retracement and impulse phases.

## User Inputs

The script allows users to customize its behavior using the following input options:

- `highs_lows`: A boolean input to control the display of high and low lines.
- `boslines`: A boolean input to control the display of break of structure lines.

## Custom Functions

The script defines several custom functions for various tasks:

- `highestPrice(length)`: Finds the highest price within a specified number of bars.
- `lowestPrice(length)`: Finds the lowest price within a specified number of bars.
- `legLine(time1, point1, time2, point2)`: Draws a line between two points.
- `bosLine(time1, time2, point)`: Draws a BOS line.
- `bosLabel(time1, time2, point)`: Places a label on a BOS line.

## Logic

The core logic of the script is executed when a new historical bar is encountered (`if barstate.ishistory`). Here's how the logic flows:

- On the first historical bar (`barstate.isfirst`), the script determines the initial trend direction based on the open and close prices and initializes relevant variables.

- If the trend is not established yet (`trendnotEstablished`), the script checks the first candle to determine the trend direction.

- Once the trend is established, the script continuously monitors each new bar to identify whether it's part of an impulse or retracement phase within the trend.

- Depending on the trend direction and wave leg, it decides whether the current bar belongs to an impulse or retracement phase and updates variables accordingly.

- When a retracement phase is identified, the script plots high and low lines (if specified by the user) and checks for break of structure conditions. If a BOS occurs, it plots BOS lines and labels.

- The script keeps track of impulse and retracement counts and adjusts trend direction and wave leg as necessary.

Please note that this script is designed for use in the TradingView platform and is primarily intended for technical analysis and visualizing market structure on price charts. Users can customize input options to tailor it to their trading strategies.
