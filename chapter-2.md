# Chapter 2: End-to-End Machine Learning Project

## Get the data

- `dataset = pd.read_csv(dataset.csv)`: loads dataset
- `dataset.head()`: displays first 5 rows of dataset
- `dataset.info()`: displays quick description of data
- `dataset.["my_field"].value_counts()`: displays the categories which exist in "my field" and their counts
- `dataset.describe()`: displays a summary of numerical attributes
- Display histograms:
  ```python3
  housing.hist(bins=50, figsize=(20,15))
  plt.show()
  ```

