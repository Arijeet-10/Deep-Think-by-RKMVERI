# Deep-Think-by-RKMVERI

# Sales Forecasting with Facebook Prophet

## Overview

This Jupyter Notebook demonstrates a time series forecasting approach for predicting sales using the Facebook Prophet library. It focuses on a dataset containing historical sales data for multiple stock-keeping units (SKUs) across different warehouses and regions. The primary goal is to forecast sales for June 2021.

## Dataset

The notebook utilizes a CSV dataset (`Data.csv`) with the following structure:

*   **Warehouse id:** Identifier for the warehouse.
*   **Region:** The region where the warehouse is located (e.g., NORTH, SOUTH, EAST, WEST).
*   **SKU id:**  Unique identifier for each stock-keeping unit (product).
*   **Apr-18, May-18, ..., May-21:** Monthly sales data for each SKU from April 2018 to May 2021.

Additionally, a `Submission Format.csv` file is used as a template for the final output.

## Methodology

The forecasting process involves the following steps:

1. **Data Loading and Preprocessing:**
    *   The `Data.csv` dataset is loaded into a Pandas DataFrame.
    *   The sales data is melted into a long format with `Month` and `Sales` columns.
    *   The `Month` column is converted to datetime objects.
    *   Missing sales values are filled with 0, assuming that missing data likely indicates zero sales.

2. **Exploratory Data Analysis (EDA) and Visualization:**
    * The code includes extensive visualization and EDA, exploring overall sales trends, regional variations, warehouse performance, sales distributions, and top-selling SKUs.

3. **Feature Engineering:**
    *   **Monthly and Yearly Averages:** Calculated to capture seasonal and annual trends.
    *   **Rolling Average:** A 12-month rolling average is computed to smooth out short-term fluctuations.
    *   **Lagged Sales:** A lagged sales feature (sales from 12 months prior) is created to capture potential autocorrelation.
    *   **Dummy Variables:**
        *   `is_holiday`: Binary indicator (0 or 1) for months containing a dummy holiday (January and July are treated as holidays).
        *   `is_promotion`: Binary indicator (randomly generated in this example) to represent the presence of promotional activities.

4. **Forecasting with Prophet:**
    *   The Facebook Prophet library is used for time series forecasting.
    *   A separate Prophet model is trained for each unique combination of `Warehouse id`, `Region`, and `SKU id`.
    *   The models predict sales for one month ahead (June 2021).
    *   If an error occurs during model fitting for a specific SKU, the average of the last three months' sales is used as a fallback prediction.

5. **Submission File Generation:**
    *   The predicted June 2021 sales from the Prophet models are merged with the `Submission Format.csv` template.
    *   Missing predictions are filled with 0.
    *   The final forecast is saved as `Shuvam_Podder.csv`.

## Requirements

*   Python 3.x
*   Pandas
*   NumPy
*   Scikit-learn
*   fbprophet (Facebook Prophet)
*   Matplotlib
*   Seaborn

## Installation

1. **Clone the repository:**
    ```bash
    git clone https://github.com/Arijeet-10/Deep-Think-by-RKMVERI.git
    ```

2. **Install required packages:**
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn prophet
    ```

## Usage

1. Ensure the `Data.csv` and `Submission Format.csv` files are in the same directory as the notebook.
2. Open and run the `fbProphet_Forecasting.ipynb` notebook in a Jupyter environment (e.g., Jupyter Notebook, JupyterLab, Google Colab).
3. The output file `Shuvam_Podder.csv` will be generated with the June 2021 sales forecasts.

## Notes

*   The code assumes a specific date format ('%b-%y') in the input data.
*   The `create_dummy_holidays` and `create_dummy_promotions` functions are simplified examples. In a real-world scenario, you would likely use actual holiday and promotion data.
*   The Prophet model fitting process may take some time, depending on the size of the dataset and the number of unique SKUs.
*   The accuracy of the forecasts can be improved by further refining the model parameters and incorporating additional relevant features.

## Author

Shuvam Podder

## License

This project is licensed under the [MIT License](LICENSE) - see the LICENSE file for details. (You should add a LICENSE file to your repository).
