
# Objection 

Be able to pull data in from IoT devices and perform data processing and ML in R/Python or Scala using notebooks




My Objection

Install Spark
Install Zeppelin
Install PostgreSQL and timescale DB

Use Python/Scala And R in spark
When using R in Zeppelin set the you need to use %spark.r if you want spark to process the data. Using %r will only have zeppelin talk with r-base

Connect spark/scala to timescale DB in Zeppelin using scala


The end end result you can pull data in using Python play with it store it in postgress. Use scala if need be using zeppelin z.get/set methods, Call the data from PostgreSQL using R

z.get set methods in zeppelin 

https://zeppelin.apache.org/docs/0.8.0/usage/other_features/zeppelin_context.html#object-exchange



# Data Processsing 

Apache Spark


# Notebooks
Apache Zeppelin
https://zeppelin.apache.org/


# DB

Timescale DB (Psotgres)

https://www.timescale.com/


# IoT data sync

## Haystack
We need to pull data from existing IoT projects using Haystack.

https://project-haystack.org/


## Json
Need to be able to get data from by method of json


# Setup 
## Spark
https://spark.apache.org/downloads.html

## Zeppelin 

Download and start in bin folder ./zeppelin.sh




