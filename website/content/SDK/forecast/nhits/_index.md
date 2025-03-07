To obtain charts, make sure to add `chart=True` as the last parameter

## Get underlying data 
### forecast.nhits(data: Union[pandas.core.series.Series, pandas.core.frame.DataFrame], target_column: str = 'close', n_predict: int = 5, train_split: float = 0.85, past_covariates: str = None, forecast_horizon: int = 5, input_chunk_length: int = 14, output_chunk_length: int = 5, num_stacks: int = 3, num_blocks: int = 1, num_layers: int = 2, layer_widths: int = 512, pooling_kernel_sizes: Optional[Tuple[Tuple[int]]] = None, n_freq_downsample: Optional[Tuple[Tuple[int]]] = None, dropout: float = 0.1, activation: str = 'ReLU', max_pool_1d: bool = True, batch_size: int = 32, n_epochs: int = 100, learning_rate: float = 0.001, model_save_name: str = 'brnn_model', force_reset: bool = True, save_checkpoints: bool = True) -> Tuple[list[darts.timeseries.TimeSeries], List[darts.timeseries.TimeSeries], List[darts.timeseries.TimeSeries], Optional[float], Any]

Performs Nhits forecasting

    Args:
        data (Union[pd.Series, pd.DataFrame]):
            Input Data
        target_column (str, optional):
            Target column to forecast. Defaults to "close".
        n_predict (int, optional):
            Days to predict. Defaults to 5.
        train_split (float, optional):
            Train/val split. Defaults to 0.85.
        past_covariates (str, optional):
            Multiple secondary columns to factor in when forecasting. Defaults to None.
        forecast_horizon (int, optional):
            Forecast horizon when performing historical forecasting. Defaults to 5.
        input_chunk_length (int, optional):
            Number of past time steps that are fed to the forecasting module at prediction time. Defaults to 14.
        output_chunk_length (int, optional):
            The length of the forecast of the model. Defaults to 5.
        num_stacks int:
            The number of stacks that make up the whole model.
        num_blocks int:
            The number of blocks making up every stack.
        num_layers int:
            The number of fully connected layers preceding the final forking layers in each block
            of every stack.
        layer_widths int:
            Determines the number of neurons that make up each fully connected layer in each
            block of every stack. If a list is passed, it must have a length equal to num_stacks
            and every entry in that list corresponds to the layer width of the corresponding stack.
            If an integer is passed, every stack will have blocks with FC layers of the same width.
        pooling_kernel_size Optional[Tuple[Tuple[int]]]:
            If set, this parameter must be a tuple of tuples, of size (num_stacks x num_blocks),
            specifying the kernel size for each block in each stack used for the input pooling
            layer. If left to None, some default values will be used based on input_chunk_length.
        n_freq_downsample: Optional[Tuple[Tuple[int]]]:
            If set, this parameter must be a tuple of tuples, of size (num_stacks x num_blocks),
            specifying the downsampling factors before interpolation, for each block in each stack.
            If left to None, some default values will be used based on output_chunk_length.
        dropout float:
             The dropout probability to be used in fully connected layers.
        activation str:
            Supported activations: [‘ReLU’,’RReLU’, ‘PReLU’, ‘Softplus’, ‘Tanh’, ‘SELU’, ‘LeakyReLU’, ‘Sigmoid’]
        max_pool_1d bool:
            Use max_pool_1d pooling. False uses AvgPool1d.
        batch_size (int, optional):
            Number of time series (input and output sequences) used in each training pass. Defaults to 32.
        n_epochs (int, optional):
            Number of epochs over which to train the model. Defaults to 100.
        learning_rate (float, optional):
            Defaults to 1e-3.
        model_save_name (str, optional):
            Name for model. Defaults to "brnn_model".
        force_reset (bool, optional):
            If set to True, any previously-existing model with the same name will be reset (all checkpoints will be
            discarded). Defaults to True.
        save_checkpoints (bool, optional):
            Whether or not to automatically save the untrained model and checkpoints from training. Defaults to True.

    Returns:
        list[TimeSeries]
            Adjusted Data series
        list[TimeSeries]
            Historical forecast by best RNN model
        list[TimeSeries]
            list of Predictions
        Optional[float]
            Mean average precision error
        Any
            Best BRNN Model

## Getting charts 
### forecast.nhits(data: Union[pandas.core.series.Series, pandas.core.frame.DataFrame], target_column: str = 'close', dataset_name: str = '', n_predict: int = 5, past_covariates: str = None, train_split: float = 0.85, forecast_horizon: int = 5, input_chunk_length: int = 14, output_chunk_length: int = 5, num_stacks: int = 3, num_blocks: int = 1, num_layers: int = 2, layer_widths: int = 512, pooling_kernel_sizes: Optional[Tuple[Tuple[int]]] = None, n_freq_downsample: Optional[Tuple[Tuple[int]]] = None, dropout: float = 0.1, activation: str = 'ReLU', max_pool_1d: bool = True, batch_size: int = 32, n_epochs: int = 100, learning_rate: float = 0.001, model_save_name: str = 'rnn_model', force_reset: bool = True, save_checkpoints: bool = True, export: str = '', residuals: bool = False, forecast_only: bool = False, start_date: Optional[datetime.datetime] = None, end_date: Optional[datetime.datetime] = None, naive: bool = False, export_pred_raw: bool = False, external_axes: Optional[List[axes]] = None, chart=True)

Display Nhits forecast

    Parameters
    ----------
        data (Union[pd.Series, pd.DataFrame]):
            Input Data
        target_column (str, optional):
            Target column to forecast. Defaults to "close".
        dataset_name str
            The name of the ticker to be predicted
        n_predict (int, optional):
            Days to predict. Defaults to 5.
        train_split (float, optional):
            Train/val split. Defaults to 0.85.
        past_covariates (str, optional):
            Multiple secondary columns to factor in when forecasting. Defaults to None.
        forecast_horizon (int, optional):
            Forecast horizon when performing historical forecasting. Defaults to 5.
        input_chunk_length (int, optional):
            Number of past time steps that are fed to the forecasting module at prediction time. Defaults to 14.
        output_chunk_length (int, optional):
            The length of the forecast of the model. Defaults to 5.
        num_stacks int:
            The number of stacks that make up the whole model.
        num_blocks int:
            The number of blocks making up every stack.
        num_layers int:
            The number of fully connected layers preceding the final forking layers in each block
            of every stack.
        layer_widths int:
            Determines the number of neurons that make up each fully connected layer in each
            block of every stack. If a list is passed, it must have a length equal to num_stacks
            and every entry in that list corresponds to the layer width of the corresponding stack.
            If an integer is passed, every stack will have blocks with FC layers of the same width.
        pooling_kernel_size Optional[Tuple[Tuple[int]]]:
            If set, this parameter must be a tuple of tuples, of size (num_stacks x num_blocks),
            specifying the kernel size for each block in each stack used for the input pooling
            layer. If left to None, some default values will be used based on input_chunk_length.
        n_freq_downsample: Optional[Tuple[Tuple[int]]]:
            If set, this parameter must be a tuple of tuples, of size (num_stacks x num_blocks),
            specifying the downsampling factors before interpolation, for each block in each stack.
            If left to None, some default values will be used based on output_chunk_length.
        dropout float:
             The dropout probability to be used in fully connected layers.
        activation str:
            Supported activations: [[‘ReLU’,’RReLU’, ‘PReLU’, ‘Softplus’, ‘Tanh’, ‘SELU’, ‘LeakyReLU’, ‘Sigmoid’]
        max_pool_1d bool:
            Use max_pool_1d pooling. False uses AvgPool1d.
        batch_size (int, optional):
            Number of time series (input and output sequences) used in each training pass. Defaults to 32.
        n_epochs (int, optional):
            Number of epochs over which to train the model. Defaults to 100.
        learning_rate (float, optional):
            Defaults to 1e-3.
        model_save_name (str, optional):
            Name for model. Defaults to "brnn_model".
        force_reset (bool, optional):
            If set to True, any previously-existing model with the same name will be reset
            (all checkpoints will be discarded). Defaults to True.
        save_checkpoints (bool, optional):
            Whether or not to automatically save the untrained model and checkpoints from training.
            Defaults to True.
        export: str
            Format to export data
        residuals: bool
            Whether to show residuals for the model. Defaults to False.
        forecast_only: bool
            Whether to only show dates in the forecasting range. Defaults to False.
        start_date: Optional[datetime]
            The starting date to perform analysis, data before this is trimmed. Defaults to None.
        end_date: Optional[datetime]
            The ending date to perform analysis, data after this is trimmed. Defaults to None.
        naive: bool
            Whether to show the naive baseline. This just assumes the closing price will be the same
            as the previous day's closing price. Defaults to False.
        external_axes:Optional[List[plt.axes]]
            External axes to plot on
