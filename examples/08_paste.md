### Combine two sorted files

Ever wanted to combine two files together where line 1 from file1 combines with line 1 for file 2. I do not think I have ever needed this but you live and learn.
```
paste -d ' ' data_files/places.txt data_files/animals.txt
```

Combine the two files for mashups
```
paste -d ' ' <(sort data_files/places.txt) data_files/animals.txt
```

If you have GNU sort or shuf, randomly combine the two files for mashups, mine are prefixed with g e.g. gshuf
```
paste -d ' ' <(gshuf data_files/places.txt) <(gshuf data_files/animals.txt)
```

Useful options:
+ `paste -s` Concatenate all of the lines of each separate input file in command line order
