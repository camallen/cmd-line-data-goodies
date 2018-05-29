### Split a file into smaller chunks

Ever had a mail list that you wanted to randomly split up into smaller lists? Now you can use `split` to make your life happy again.

Split a CSV into new_filename every 20 lines
```
split -l 20 data_files/deniro_rotten_tomato_scores.csv data_files/deniro_rotten_tomato_scores_
```

Inspect what was created by the split cmd
```
ls -alh data_files/deniro_*
```

Rename the files created by split to have a csv extension. this firstly finds all data files that have no file extension and then issues a move command on each to add .csv extension.
```
find data_files -type f ! -name "*.*" -exec mv '{}' '{}'.csv \;
```

Useful options:
+ `split -b` split by certain byte size
+ `split -a` generate suffixes of length N
+ `split -x` split using hex suffixes
