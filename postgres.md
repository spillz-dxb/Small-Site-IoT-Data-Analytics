
Install Postgres

https://linuxhint.com/install-postgresql-10-arch-linux/






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
