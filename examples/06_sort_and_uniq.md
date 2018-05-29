### Sort and uniqueify a file / stream

Ever had a file with duplicates that you needed to get a unique count of lines on, well know you can using these little beauties.

Sort a csv file by 3rd column
```
sort -t, -k3 data_files/deniro_rotten_tomato_scores.csv
```

Reverse sort a file
```
sort -t, -k3 -r data_files/deniro_rotten_tomato_scores.csv
```

Sort the csv file on the 2nd column
```
sort -t, -k2 data_files/deniro_rotten_tomato_scores.csv
```

Numerically sort the csv file on the 2nd column (try this without the n option)
```
sort -t, -k2n data_files/deniro_rotten_tomato_scores.csv
```

Get a unique list of rows in a file
```
sort data_files/duplicate_lines.txt | uniq
```

Use sort to do the same thing
```
sort -u data_files/duplicate_lines.txt
```

Compare the two results using diff
```
diff <(sort -u data_files/duplicate_lines.txt) <(sort data_files/duplicate_lines.txt | uniq)
```

Useful options:
+ `sort -f` ignore case
+ `sort -r` reverse sort order
+ `sort -R` scramble order
+ `uniq -c` count number of occurrences
+ `uniq -d` only print duplicate lines
