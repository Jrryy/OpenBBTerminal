## Get underlying data 
### crypto.candles(candles_df: 'pd.DataFrame', volume: 'bool' = True, ylabel: 'str' = '', title: 'str' = '', external_axes: 'list[plt.Axes] | None' = None, yscale: 'str' = 'linear') -> 'None'

Plot candle chart from dataframe. [Source: Binance]

    Parameters
    ----------
    candles_df: pd.DataFrame
        Dataframe containing time and OHLCV
    volume: bool
        If volume data shall be plotted, by default True
    ylabel: str
        Y-label of the graph, by default ""
    title: str
        Title of graph, by default ""
    external_axes : Optional[List[plt.Axes]], optional
        External axes (1 axis is expected in the list), by default None
    yscale : str
        Scaling for y axis.  Either linear or log
