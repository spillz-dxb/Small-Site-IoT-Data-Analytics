
Install Postgres

https://linuxhint.com/install-postgresql-10-arch-linux/

sudo systemctl start postgresql





## R lang 

```
# install.packages("RPostgreSQL")
require("RPostgreSQL")

# create a connection
# save the password that we can "hide" it as best as we can by collapsing it
pw <- {
  ""
}

# loads the PostgreSQL driver
drv <- dbDriver("PostgreSQL")
# creates a connection to the postgres database
# note that "con" will be used later in each connection to the database
con <- dbConnect(drv, dbname = "postgres",
             
                 host = "127.0.0.1", port = 5432,
                 user = "postgres", password = pw)
rm(pw) # removes the password

# check for the cartable
dbExistsTable(con, "cartable")


# creates df, a data.frame with the necessary columns
data(mtcars)
df <- data.frame(carname = rownames(mtcars), 
                 mtcars, 
                 row.names = NULL)
df$carname <- as.character(df$carname)
rm(mtcars)

# writes df to the PostgreSQL database "postgres", table "cartable" 
dbWriteTable(con, "cartable", 
             value = df, append = TRUE, row.names = FALSE)

# query the data from postgreSQL 
df_postgres <- dbGetQuery(con, "SELECT * from cartable")
df_postgres
# compares the two data.frames
identical(df, df_postgres)
# TRUE

# Basic Graph of the Data
require(ggplot2)
ggplot(df_postgres, aes(x = as.factor(cyl), y = mpg, fill = as.factor(cyl))) + 
  geom_boxplot() + theme_bw()
```



## Python

https://pynative.com/python-postgresql-tutorial/#Install_Psycopg2_using_pip_command


```
%pyspark
%pyspark

import psycopg2
from psycopg2 import Error

connection = psycopg2.connect(user = "postgres",
                                  password = "password",
                                  host = "127.0.0.1",
                                  port = "5432",
                                  database = "postgres")
cursor = connection.cursor()
    # Print PostgreSQL Connection properties
# print ( connection.get_dsn_parameters(),"\n")
    # Print PostgreSQL version
cursor.execute("SELECT version();")
record = cursor.fetchone()
# print("You are connected to - ", record,"\n")


# Get Coloum names

cursor.execute("Select * FROM mergesql")
colnames = [desc[0] for desc in cursor.description]
print(colnames)


PostgreSQL_select_Query = "select * from mergesql limit 10"
cursor.execute(PostgreSQL_select_Query)
mergesql = cursor.fetchall()

# print(mergesql)

# for row in mergesql:
#     print (row)


mergesql = spark.createDataFrame(mergesql)
mergesql.show()


```

