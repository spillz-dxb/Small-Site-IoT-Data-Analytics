

# pakages to use
- data.table
- zoo
- xts
- dplyr
- tidyr
- lubridate

### join data based of time

https://stackoverflow.com/questions/31876335/merge-2-dataframes-by-matching-dates

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


# Joining and renaming cols

https://stackoverflow.com/questions/46470099/r-combining-rows-and-renaming-values

# Joining Data in R with dplyr

https://rpubs.com/williamsurles/293454


## Ronding up time
lubridate
round_date: Round, floor and ceiling methods for date-time objects

```
x <- ymd_hms("2009-08-03 12:01:59.23")
round_date(x, ".5s")
round_date(x, "sec")
round_date(x, "second")
round_date(x, "minute")
round_date(x, "5 mins")
round_date(x, "hour")
round_date(x, "2 hours")
round_date(x, "day")
round_date(x, "week")
round_date(x, "month")
round_date(x, "bimonth")
```

## Save to a data.table (DF)
# Make into a DF using data.table
dt <- rbindlist(x)
dt$ts



## Joining Data
https://www.r-bloggers.com/understanding-data-table-rolling-joins/


## Cleaing data 

http://garrettgman.github.io/tidying/
