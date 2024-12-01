# Capstone Project - Team Enginuity
## Predicting Remaining Useful Life of Jet Engines

## 1.0 Synopsis
<p>This project included using simulated sensor data from jet engines to estimate the remaining useful life of that jet engine. Notations and descriptions are included in the Jupyter Notebooks describing each step. There is also a report available for a general review of the project and it's results.</p>

## 2.0 Process
<p>To replicate the modeling results, follow these steps:</p>
<ol>
<li>In the "data_processing" folder, run the workbook "data_cleaning.ipynb" from top to bottom. This provides exploratory visualizations, adds headers to the data, and outputs a "missing_indices.npy" file, which is used in the next step. </li>
	<ul>
	<li>Input: Raw datafiles as provided by NASA - 'train_FD001.txt', 'test_FD001.txt', and 'RUL_FD001.txt'. </li>
	<li>Output: 'missing_indices.npy' - a list of indices of field to be dropped when modeling. </li>
	</ul>
<li>In the "data_processing" folder, run the workbook "data_processing.ipynb" from top to bottom.