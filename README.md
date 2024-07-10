# RAII 2024

## Описание данных

Все данные лежат в /data. Поскольку файлы слишком большие я **не стала их добавлять**.

- raai_school_2024.csv - Оригинальные данные только с user_id
- original_data_with_anomaly_column.csv - Оригинальные данные но с добавлением колонки $is\_anomaly$ которая определяет аномалия ли объект
- filtered_unnormalized_data.csv - Оригинальные данные в которых лежат лишь неаномальные объекты
- filtered_scaled_data.csv - Данные в которых все NaN заполнены по правилам которые описаны в ноутбуке. Часть неопределенных данных нормализованы
- **anomaly_column.csv** - столбец аномалия/нет для оригинальной таблицы (с сохранением порядка)

Код для использования последней таблицы:
```python
data = pd.read_csv("data//raai_school_2024.csv", sep = ";")
anomaly_column = pd.read_csv("data//anomaly_column.csv", sep = ";")
data["is_anomaly"] = anomaly_column["is_anomaly"]
```

Что можно делать с filtered_scaled_data: кластеризовать стандартными методами и надеяться что получится что-то адекватное

Что хотелось бы сделать: смержть filtered_scaled_data с original_data_with_anomaly_column чтобы добавть is_na столбцы и применить иерархическую кластеризацию

Интересные ссылки: https://www.kaggle.com/search?q=Subsequence-Time-Series-Clustering