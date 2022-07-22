# Data-Proc-GCS


Загрузила таблицу для ДЗ в bigquery

И выполнила команды в SSH консоли Dataproc:
pyspark --jars=gs://spark-lib/bigquery/spark-bigquery-latest_2.12.jar -запуск spark с библиотекой bigquery

bucket = "gs://buc_netology"
spark.conf.set(“temporaryGcsBucket”, bucket) -определили бакеты

c = spark.read.format(‘bigquery’)
.option(‘table’, ‘stunning-chain-332714.DS.movie’)
.load() - прочитали таблицу из bigquery

c.createOrReplaceTempView(‘movie’) - создали временную таблицу

c - выгрузили наименование столбцов
DataFrame[movieId: bigint, title: string, genres: string]

movies = spark.sql(‘select movieId, title, genres from movie’) - загрузили таблицу во временную в DP
movies.show() - посмотрели результат:

![image](https://user-images.githubusercontent.com/85709710/180517446-42cd5c75-b7e7-456e-9780-5bbf1f5487b0.png)

