# Exam Notes: file names and columns

Exam runs on Windows. The notebooks were tested on Linux with the files from the Datasets zip.

## Windows basics (no change needed)
- `pd.read_csv("datasets/xyz.csv")` works on Windows. Forward slashes are fine in Python.
- File names are case-insensitive on Windows, so `Diabetes.csv` also opens `diabetes.csv`.
- Names with spaces or brackets work as long as they are inside the quotes, e.g. `"datasets/Social_Network_Ads (2).csv"`.
- If a file is not found: run `import os; print(os.listdir("datasets"))` and copy the exact name.
- If a column is not found: run `print(df.columns.tolist())` and copy the exact name.

## Expected file per question (what the code loads)

| Q | File in code | Columns the code uses | If the exam file differs |
|---|---|---|---|
| 1, 2, 5, 7 | `Diabetes.csv` | all features, target `Outcome` | PDF says `label`; change `"Outcome"` to `"label"` |
| 3, 4, 36, 50 | `iris.csv` | target `variety` (values `Setosa`, `Versicolor`, `Virginica`) | may be `species` with `Iris-virginica`; change the column name and value in Q50 |
| 31, 37 | `Breast Cancer.csv` | drop `id`, `Unnamed: 32`; target `diagnosis` (M/B) | if there's no `Unnamed: 32` column, drop only `id` |
| 32, 35 | `wine.csv` | target `Wine` (1, 2, 3) | may be `Class` / `target`; change the name |
| 39, 40 | `house-prices.csv` | drop `Home`; target `Price`; one-hot `Brick`, `Neighborhood` | any house file works; set the target + ID column names |
| 41 | `Social_Network_Ads (2).csv` | `Age`, `EstimatedSalary` -> `Purchased` | PDF name is `Social_Network_Ads.csv`; fix the name only |
| 45 | `PIMA.csv` | target `Outcome` | |
| 46 | `IMDB_Dataset.csv` (not in zip) | `review`, `sentiment` (code lowercases column names) | Kaggle file is often `IMDB Dataset.csv` (with a space) |
| 49 | `customer_churn.csv` (not in zip) | columns exactly as the PDF lists them | |
| 51 | `Salary.csv` | `Years of Experience` -> `Salary` | PDF names `years_of_experience`, `salary` |
| 52, 54 | `HousePrices.csv` (not in zip) | `square_feet` -> `price` | if only `house-prices.csv` exists: use `SqFt` and `Price` |
| 53 | `CarPrices.csv` | age = `months_old`, mileage = `km` -> `price` | PDF names `age`, `mileage` |
| 55 | `CarPrices.csv` | all columns (one-hot `fuel_type`) -> `price` | |
| 56 | `HouseData.csv` | `Bedrooms`, `SqFt`, `Neighborhood` -> `Price` | PDF names `num_rooms`, `square_feet`, `location`, `house_price` |
| 57 | `EmployeeData.csv` (not in zip) | `years_of_experience`, `education_level` -> `salary` | `Salary.csv` has the same idea: `Years of Experience`, `Education Level`, `Salary` (dropna first) |
| 58 | `HousingData.csv` | `Bedrooms`, `SqFt`, `Bathrooms` -> `Price` | PDF names `num_rooms`, `area`, `age`; the zip file has no age column |
| 59 | `Diabetes.csv` | target variable `target = "Outcome"` | PDF wants `diabetes_progression`; change the one `target` line |
| 60 | `WineQuality.csv` | drop `Id`; target `quality` | |
| 61 | `HealthData.csv` | target `health_score` | |

"Not in zip" = tested only with dummy data. The code follows the PDF's column names.

## Library / network notes
- Family 03 (K-Medoids): `from sklearn_extra.cluster import KMedoids` needs the `scikit-learn-extra` package (said to be installed in the lab).
- Q47 `fetch_20newsgroups` downloads ~14 MB the first time. With no internet in the lab it fails; nothing to fix in the code.
- Every other "sklearn dataset" question (`load_iris`, `load_wine`, `load_breast_cancer`, `load_digits`, `make_*`) is built in and needs no files.
