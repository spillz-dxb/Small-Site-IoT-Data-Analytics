

# Use data.table pakage
library(data.table)


~~~
new <- data.table( date = as.POSIXct( c( "2016-03-02 12:20:00", "2016-03-07 12:20:00", "2016-04-02 12:20:00" ) ), data.new = c( "t","u","v" ) )
head( new, 2 )

                  date data.new
1: 2016-03-02 12:20:00        t
2: 2016-03-07 12:20:00        u

old <- data.table( date = as.POSIXct( c( "2016-03-02 12:20:00", "2016-03-07 12:20:00", "2016-04-02 12:20:00", "2015-03-02 12:20:00" ) ), data.old = c( "a","b","c","d" ) )
head( old, 2 )


                  date data.old
1: 2016-03-02 12:20:00        a
2: 2016-03-07 12:20:00        b

setkey( new, date )
setkey( old, date )

combined <- new[ old, roll = "nearest" ]
combined

                  date data.new data.old
1: 2015-03-02 12:20:00        t        d
2: 2016-03-02 12:20:00        t        a
3: 2016-03-07 12:20:00        u        b
4: 2016-04-02 12:20:00        v        c

~~~



## Ronding up time
lubridate
round_date: Round, floor and ceiling methods for date-time objects


## Joining Data
https://www.r-bloggers.com/understanding-data-table-rolling-joins/


## Cleaing data 

http://garrettgman.github.io/tidying/