# One Billion Lines: Data Processing Challenge with Python

## Introduction

The goal of this project is to demonstrate how to efficiently process a massive data file containing 1 billion rows (~14GB), specifically to calculate statistics (including aggregation and sorting, which are heavy operations) using Python.

This challenge was inspired by the [The One Billion Row Challenge](https://github.com/gunnarmorling/1brc), originally proposed for Java.

The data file consists of temperature measurements from various weather stations. Each record follows the format `<string: station name>;<double: measurement>`, with the temperature presented with one decimal place of precision.

Here are ten example lines from the file:

```
Hamburg;12.0
Bulawayo;8.9
Palembang;38.8
St. Johns;15.2
Cracow;12.6
Bridgetown;26.9
Istanbul;6.2
Roseau;34.4
Conakry;31.2
Istanbul;23.0
```

The challenge is to develop a Python program capable of reading this file and calculating the minimum, average (rounded to one decimal place), and maximum temperature for each station, displaying the results in a table sorted by station name.

| station      | min_temperature | mean_temperature | max_temperature |
|--------------|-----------------|------------------|-----------------|
| Abha         | -31.1           | 18.0             | 66.5            |
| Abidjan      | -25.9           | 26.0             | 74.6            |
| Abéché       | -19.8           | 29.4             | 79.9            |
| Accra        | -24.8           | 26.4             | 76.3            |
| Addis Ababa  | -31.8           | 16.0             | 63.9            |
| Adelaide     | -31.8           | 17.3             | 71.5            |
| Aden         | -19.6           | 29.1             | 78.3            |
| Ahvaz        | -24.0           | 25.4             | 72.6            |
| Albuquerque  | -35.0           | 14.0             | 61.9            |
| Alexandra    | -40.1           | 11.0             | 67.9            |
| ...          | ...             | ...              | ...             |
| Yangon       | -23.6           | 27.5             | 77.3            |
| Yaoundé      | -26.2           | 23.8             | 73.4            |
| Yellowknife  | -53.4           | -4.3             | 46.7            |
| Yerevan      | -38.6           | 12.4             | 62.8            |
| Yinchuan     | -45.2           | 9.0              | 56.9            |
| Zagreb       | -39.2           | 10.7             | 58.1            |
| Zanzibar City| -26.5           | 26.0             | 75.2            |
| Zürich       | -42.0           | 9.3              | 63.6            |
| Ürümqi       | -42.1           | 7.4              | 56.7            |
| İzmir        | -34.4           | 17.9             | 67.9            |            |

## Dependencies

To run the scripts in this project, you will need the following libraries:

* Polars: `0.20.3`
* DuckDB: `0.10.0`
* Dask[complete]: `^2024.2.0`

Also, you need to use Python 3.12.1 version.

## Results

The tests were performed on a laptop equipped with a 3th Gen Intel(R) Core(TM) i7-13700H 2.40 GHz processor, 16GB of RAM and 64-bit operating system. The implementations used purely Python approaches, as well as Pandas, Dask, Polars, and DuckDB. The execution time results for processing the 1 billion row file are presented below:

| Implementation | Time |
| --------------- | ---- |
| Python | 20 minutes |
| Python + Pandas | 263 sec |
| Python + Dask | 155.62 sec |
| Python + Polars | 33.86 sec |
| Python + DuckDB | 14.98 sec |

## Conclusion

This challenge clearly highlighted the effectiveness of different Python libraries in handling large volumes of data. Traditional methods such as pure Python (20 minutes), and even Pandas (5 minutes) required several tactics to implement batch processing, while libraries like Dask, Polars, and DuckDB proved to be exceptionally effective, requiring fewer lines of code due to their inherent ability to efficiently stream and batch data. DuckDB stood out, achieving the shortest execution time thanks to its execution and processing strategy.

These results emphasize the importance of selecting the right tool for large-scale data analysis, demonstrating that Python, with the right libraries, is a powerful choice to tackle big data challenges.

DuckDB also wins with 1 million rows — it really is the best.

## How to Run

To run this project and reproduce the results:

1. Clone this repository.
2. Set the Python version using `pyenv local 3.12.1`.
3. Run `poetry env use 3.12.1`, `poetry install --no-root` and `poetry lock --no-update`.
4. Execute `python src/create_measurements.py` to generate the test file.
5. Be patient and grab a coffee — it will take about 10 minutes to generate the file.
6. Make sure you have installed the specified versions of Dask, Polars, and DuckDB libraries.
7. Run the scripts `python src/using_python.py`, `python src/using_pandas.py`, `python src/using_dask.py`, `python src/using_polars.py`, and `python src/using_duckdb.py` via a terminal or a Python-supported development environment.

This project showcases the versatility of the Python ecosystem for data processing tasks, offering valuable lessons on tool selection for large-scale analysis.


