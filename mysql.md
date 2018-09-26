# MySQL queries

Some useful tricks for working with data from MySQL tables.

## Aggregation

### Getting aggregated data by period

Given a table like:

id | create_date | value
-- | ----------- | -----
1 | 2018-12-01 19:00:00 | 10
2 | 2018-11-30 18:30:00 | 7
3 | 2018-11-20 12:15:00 | 3
4 | 2018-11-10 16:32:00 | 6

we want to obtain the totals from the `value` column grouped by different periods of time, using the available [MySQL date and time functions](https://dev.mysql.com/doc/refman/5.7/en/date-and-time-functions.html).


#### By day

```sql
select 
	date(create_date) as day, 
	sum(value) as total
from my_table 
group by day
order by day desc
```

#### By week

```sql
select 
	yearweek(create_date) as week, 
	sum(value) as total
from my_table 
group by week
order by week desc
```

#### By month

Grouping by month is the only case where MySQL doesn't have a dedicated date function, so we'll use `date_format` to extract the year and month from the date:

```sql
select 
	date_format(create_date, "%Y-%m") as month, 
	sum(value) as total
from my_table 
group by month
order by month desc
```

Alternatively, we can use `extract(year_month from create_date)` instead of `date_format`.

#### By year

```sql
select 
	year(create_date) as year, 
	sum(value) as total
from my_table 
group by year
order by year desc
```

### Aggregation on more than one column

Given a table like:

id | create_date | currency | value
-- | ----------- | -------- | -----
1 | 2018-12-01 19:00:00 | usd | 10
2 | 2018-11-30 18:30:00 | eur | 7
3 | 2018-11-20 12:15:00 | eur | 3
4 | 2018-11-10 16:32:00 | usd | 6

You can group them by period and currency:

```sql
select 
	date(create_date) as day, 
	currency,
	sum(value) as total
from my_table 
group by day, currency
order by day desc
```

To give results in the form:

day | currency | total
--- | -------- | -----
2018-12-01 | usd | 10
2018-12-01 | eur | 7
2018-11-30 | usd | 5
2018-11-30 | eur | 3

Say you want to turn the values of the `currency` column into individual columns. I don't know (yet) any other method of pivoting the chart than creating the columns manually:

```sql
select 
	date(create_date) as day, 
	sum(case when currency = 'usd' then value else 0 end) as usd,
	sum(case when currency = 'eur' then value else 0 end) as eur,
	sum(value) as total
from my_table 
group by day, currency
order by day desc
```

To obtain:

day | usd | eur | total
--- | --- | --- | -----
2018-12-01 | 10 | 7 | 17
2018-11-30 | 5 | 3 | 8

(This, of course, breaks down when there are several possible unique values for the column, but it's not to bad when they're a handful.)