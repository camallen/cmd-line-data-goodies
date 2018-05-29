### Previewing parts of a stream / file

Who knows what is headers or data is contained in a new data file. How about a way to quick look at the first 10 lines by default.
```
head data_files/deniro_rotten_tomato_scores.csv
```

Just get first line (the headers)
```
head -n 1 data_files/deniro_rotten_tomato_scores.csv
```

Test a comma to slash conversion on a sample of data
```
head -n 3 data_files/deniro_rotten_tomato_scores.csv | sed 's/,/|/g'
```

Useful options:
+ `head -n` print a specific number of lines
+ `head -c` print a specific number of bytes

Conversely there is a cmd called `tail` that gets takes from the last line of the file instead of the first
```
tail data_files/deniro_rotten_tomato_scores.csv
```
Get the last two rows
```
tail -n2 data_files/deniro_rotten_tomato_scores.csv
```

Get all data rows, skip the the header
```
tail -n+2 data_files/deniro_rotten_tomato_scores.csv
```
