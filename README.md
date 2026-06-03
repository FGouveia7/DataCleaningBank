# Data Cleaning - Bank Marketing

Project for cleaning and formatting raw data from `bank_marketing.csv`, generating three analysis-ready files: `client.csv`, `campaign.csv`, and `economics.csv`.

## Requirements

Python 3.10 or later, with the following libraries:

* pandas
* numpy

To install:

```bash
pip install pandas numpy
```

## How to Run

1. Make sure `bank_marketing.csv` is located in the project's root directory.
2. Open the notebook `Project_DataCleaningBank.ipynb`.
3. Run all cells in order.
4. The files `client.csv`, `campaign.csv`, and `economics.csv` will be generated in the project folder.

## Data Cleaning Rules

### client.csv

| Column           | Transformation                                   |
| ---------------- | ------------------------------------------------ |
| `job`            | Replace `.` with `_`                             |
| `education`      | Replace `.` with `_`; convert `"unknown"` to NaN |
| `credit_default` | 1 if `"yes"`, otherwise 0                        |
| `mortgage`       | 1 if `"yes"`, otherwise 0                        |

### campaign.csv

| Column              | Transformation                                                      |
| ------------------- | ------------------------------------------------------------------- |
| `campaign_outcome`  | 1 if `"yes"`, otherwise 0                                           |
| `previous_outcome`  | 1 if `"success"`, otherwise 0                                       |
| `last_contact_date` | Created from `day` + `month` + fixed year 2022; format `YYYY-MM-DD` |

### economics.csv

| Column                 | Transformation            |
| ---------------------- | ------------------------- |
| `cons_price_idx`       | Kept as float, no changes |
| `euribor_three_months` | Kept as float, no changes |

## Notes

The helper function `one_if(column, value)` centralizes the conversion of categorical columns into binary values (0/1), avoiding repeated logic throughout the notebook.

The year 2022 is fixed when building `last_contact_date`. If the data corresponds to a different period, adjust the year directly in the notebook before running it.

If any expected column cannot be found, verify that the column names in the input CSV exactly match those used in the notebook.
