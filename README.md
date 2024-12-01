# Capstone Project - Team Enginuity
## Predicting Remaining Useful Life of Jet Engines

## 1.0 Synopsis
<p>This project included using simulated sensor data from jet engines to estimate the remaining useful life (RUL) of a jet engine. Notations and descriptions are included in the Jupyter Notebooks describing each step. There is also a report available for a general review of the project and it's results.</p>

## 2.0 Data Access Statement
<p>The data used in this project is publicly available without license or permission. It was created for a data competition at the International Conference for Prognostics and Health Management in 2008 by the following individuals: Abhinav Saxena of the NASA Ames Research Center, Kai Goebel with the NASA Ames Research Center, Don Simon with the NASA Glenn Research Center, and Neil Eklund with GE Global Research.</p>
<p>The data is hosted by the NASA Prognostics Center of Excellence (PCoE) and is located in the NASA Open Data Portal repository at the following link:</p>
<p>https://data.nasa.gov/Aerospace/CMAPSS-Jet-Engine-Simulated-Data/ff5v-kuh6/data</p>


## 3.0 Process
<p>To replicate the modeling results, follow these steps:</p>
<ol>
<li>In the "data_processing" folder, run the workbook "data_cleaning.ipynb" from top to bottom. </li>
	<ul>
	<li>This provides exploratory visualizations, adds headers to the data, and outputs a "missing_indices.npy" file, which is used in the next step. </li>
	<li>Inputs: Raw datafiles as provided by NASA - 'train_FD001.txt', 'test_FD001.txt', and 'RUL_FD001.txt'. </li>
	<li>Output: 'missing_indices.npy' - a list of indices of field to be dropped when modeling. Saved to the "data" folder.</li>
	</ul>
<li>In the "data_processing" folder, run the workbook "data_processing.ipynb" from top to bottom.</li>
	<ul>
	<li>This scales, batches, adds a designated maximum RUL for each data row in the train set, 