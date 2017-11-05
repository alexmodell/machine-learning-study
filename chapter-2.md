# Chapter 2: End-to-End Machine Learning Project

## Get the data

- `dataset = pd.read_csv(dataset.csv)`: loads dataset
- `dataset.head()`: displays first 5 rows of dataset
- `dataset.info()`: displays quick description of data
- `dataset.["my_field"].value_counts()`: displays the categories which exist in "my field" and their counts
- `dataset.describe()`: displays a summary of numerical attributes
- Display histograms:
  ```python
  import matplotlib.pyplot as plt
  
  housing.hist(bins=50, figsize=(20,15))
  plt.show()
  ```
- Split data into training set and test set:
  ```python
  from sklearn.model_selection import train_test_split
  
  train_set, test_set = train_test_split(housing, test_size=0.2, random_state=42)
  ```
- Create new column dividing continuous data into discrete categories:
  ```python
  dataset["continuous_attribute_cat"] = np.ceil(dataset["continuous_attribute"] / 1.5)
  dataset["continuous_attribute_cat"].where(dataset["continuous_attribute"] < 5, 5.0, inplace=True
  ```
- Use stratified sampling to create the train and test sets:
  ```python
  from sklearn.model_selection import StratifiedShuffleSplit

  split = StratifiedShuffleSplit(n_splits=1, test_size=0.2, random_state=42)
  for train_index, test_index in split.split(dataset, dataset["continuous_attribute_cat"]):
    strat_train_set = dataset.loc[train_index]
    strat_test_set = dataset.loc[test_index]
  ```
- Remove the `continuous_attribute_cat` to get data back into it's original form:
  ```python
  for set in (strat_train_set, strat_test_set):
    set.drop(["continuous_attribute_cat"], axis=1,  inplace=True)
  ```

  
  

