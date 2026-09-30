# big-data-notes
Мои конспекты по Big Data
# 📊 Big Data — мои конспекты

## Что такое Big Data?

Big Data — это совокупность данных, которые слишком велики или сложны для обработки традиционными инструментами. Характеризуются тремя V:

- **Volume** — объём (терабайты, петабайты)
- **Velocity** — скорость поступления
- **Variety** — разнообразие форматов (структурированные, полуструктурированные, неструктурированные)

---

## Технологии, которые я изучил

| Технология | Назначение |
| :--- | :--- |
| **Hadoop** | Распределённое хранение и обработка данных (HDFS + MapReduce) |
| **Spark** | Быстрая обработка данных в памяти |
| **Kafka** | Потоковая передача данных |
| **Flink** | Потоковая обработка с низкой задержкой |
| **Airflow** | Оркестрация пайплайнов |

---

## Пример кода: Word Count на PySpark

```python
from pyspark import SparkContext

sc = SparkContext("local", "WordCount")
text = sc.textFile("input.txt")
counts = text.flatMap(lambda line: line.split(" ")) \
             .map(lambda word: (word, 1)) \
             .reduceByKey(lambda a, b: a + b)
counts.saveAsTextFile("output")
