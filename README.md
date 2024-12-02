# Capstone Project - Team Enginuity
## Predicting Remaining Useful Life of Jet Engines

## 1.0 Synopsis
<p>This project included using simulated sensor data from jet engines to estimate the remaining useful life (RUL) of a jet engine. Notations and descriptions are included in the Jupyter Notebooks describing each step. There is also a report available for a general review of the project and it's results.</p>

## 2.0 Data Access Statement
<p>The data used in this project is publicly available without license or permission. It was created for a data competition at the International Conference for Prognostics and Health Management in 2008 by the following individuals: Abhinav Saxena of the NASA Ames Research Center, Kai Goebel with the NASA Ames Research Center, Don Simon with the NASA Glenn Research Center, and Neil Eklund with GE Global Research.</p>
<p>The data is hosted by the NASA Prognostics Center of Excellence (PCoE) and is located in the NASA Open Data Portal repository at the following link:</p>
<p>https://data.nasa.gov/Aerospace/CMAPSS-Jet-Engine-Simulated-Data/ff5v-kuh6/data</p>


## 3.0 Pipeline
<p>To replicate the modeling results, follow these steps:</p>
<ol>
<li>In the "data_processing" folder, run the workbook "data_cleaning.ipynb" from top to bottom. 
	<ul>
	<li>This provides exploratory visualizations, adds headers to the data, and outputs a "missing_indices.npy" file that designates which fields will be discarded in modeling.</li>
	<li>Inputs: Raw datafiles as provided by NASA - 'train_FD001.txt', 'test_FD001.txt', and 'RUL_FD001.txt'. </li>
	<li>Output: 'missing_indices.npy' - a list of indices of field to be dropped when modeling. Saved to the "data" folder.</li>
	</ul>
</li>
<li>In the "data_processing" folder, run the workbook "data_processing.ipynb" from top to bottom.
	<ul>
	<li>This scales, batches, adds a designated maximum RUL for each data row in the train set, and returns batched and unbatched data for input into the models.</li>
	<li>Inputs: 'missing_indices.npy', 'train_FD001.txt', 'test_FD001.txt', and 'RUL_FD001.txt'</li>
	<li>Outputs:<strong>THERE IS A BREAK IN THE PIPELINE HERE - FILENAMES NEED TO BE ADDRESSED</strong> 'train_data_batches.pkl', 'train_target_values.pkl', 'test_data_batches.pkl', 'true_rul_values.pkl', 'train_data_no_batches.pkl', and 'test_data_no_batches.pkl'</li>
	</ul>
</li>
<li>In the "models" folder, run the workbook "CNN.ipynb" from top to bottom.
	<ul>
	<li>This trains and tests a series of CNN models, saving the metrics in a log file.</li>
	<li>Deciding which parameters/variables to change in each tuning group was an iterative process and took some time.</li>
	<li>Rather than replicating Section 3.0, advised to look at the log results instead.</li>
	<li>Saves a log of the tuning iterations, a final trained model (as a pickle file), and results from the final model.</li>
	<li>Inputs: <strong>THERE IS A BREAK IN THE PIPELINE HERE - FILENAMES NEED TO BE ADDRESSED</strong></li>
	<li>Outputs: "CNN_log.csv", "CNN_model_trained.pkl", "CNN_model_trained_test_predictions.npy"
	</ul>
</li>
<li>In the "models" folder, run the workbook "LSTM.ipynb" from top to bottom.
	<ul>
	<li>This trains and tests a series of LSTM models using Optuna.</li>
	<li>The best model is saved as a separate file and then evaluated on the test set.</li>
	<li>Inputs: <strong>THERE IS A BREAK IN THE PIPELINE HERE - FILENAMES NEED TO BE ADDRESSED</strong></li>
	<li>Output: 'best_rul_lstm_model_optuna.h5'</li>
	</ul>
</li>
<li>In the "models" folder, run the workbook "RNN.ipynb" from top to bottom.
	<ul>
	<li>This trains and tests a series of RNN models using Optuna.</li>
	<li>The best model is saved as a separate file and then evaluated on the test set.</li>
	<li>Inputs: <strong>THERE IS A BREAK IN THE PIPELINE HERE - FILENAMES NEED TO BE ADDRESSED</strong></li>
	<li>Output: 'best_rul_rnn_model_optuna.h5'</li>
	</ul>
</li>
<li>In the "models" folder, run the workbook "SDAE.ipynb" from top to bottom.
	<ul>
	<li>This trains and tests a series of SDAE models using Optuna.</li>
	<li>The best model is saved as a separate file and then evaluated on the test set.</li>
	<li>Inputs: <strong>THERE IS A BREAK IN THE PIPELINE HERE - FILENAMES NEED TO BE ADDRESSED</strong></li>
	<li>Output: 'best_sdae_model_optuna_second.pth'</li>
	</ul>
</li>
<li>In the "models" folder, run the workbook "GBDT_Raw.ipynb" from top to bottom.
	<ul>
	<li>This trains and tests a series of GBDT models, saving the metrics in a log file.</li>
	<li>Due to GBDT characteristics, notebook takes in the original unprocessed data (along with the dropped columns list) and performs its own processing.</li>
	<li>Deciding which parameters/variables to change in each tuning group was an iterative process and took some time.</li>
	<li>Rather than replicating Section 3.0, advised to look at the log results instead.</li>
	<li>Saves a log of the tuning iterations, a final trained model (as a pickle file), and results from the final model.</li>
	<li>Inputs: 'missing_indices.npy', 'train_FD001.txt', 'test_FD001.txt', and 'RUL_FD001.txt'</li>
	<li>Outputs: "GBDT_log.csv", "GBDT_model_trained.pkl", "GBDT_model_trained_test_predictions.npy"
	</ul>
</li>
<li><strong>PIPELINE FOR TTM GOES HERE</strong></li>