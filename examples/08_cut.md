### Cut a column from a file

Cut out the 1st(year) and 3rd(title) columns of Deniro's movies
```
cut -d, -f 1,3 data_files/deniro_rotten_tomato_scores.csv
```

And sort them by descending year order
```
cut -d, -f 1,3 data_files/deniro_rotten_tomato_scores.csv | sort -t, -k1nr
```

Select all columns apart from the 1st one.
```
cut -d, -f 2- data_files/deniro_rotten_tomato_scores.csv
```

Finding out the number of years (2nd column unique values) Deniro has been acting.
```
cut -d, -f 1 data_files/deniro_rotten_tomato_scores.csv | sort -u | wc -l
```

How many unique titles per year
```
cut -d, -f 1 data_files/deniro_rotten_tomato_scores.csv | sort | uniq -c
```

Skip the header line as it's polluting my output data (*note the composition of different commands all chained together*)
```
tail -n+2 data_files/deniro_rotten_tomato_scores.csv | cut -d, -f 1,3 | sort -t, -k1nr
```

Useful options:
+ `cut -s` Suppress lines with no field delimiter characters
