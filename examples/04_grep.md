### Find matching character fragments in files / streams

Have you ever wanted to find which files a word occurs in, especially if you have lots of files? Desire no more with this little utensil.

Find the word 'taxi' in a file
```
grep -lr 'taxi' data_files
```

Let's try that again but this time ignore case
```
grep -lri 'taxi' data_files
```

Count number of files containing the word fockers
```
grep -lri 'fockers' data_files | wc -l
```

Count total number of lines containing word / pattern.
```
grep -ci 'fockers' data_files/deniro_rotten_tomato_scores.csv
```

List the number of times 'fockers' appears in all data files
```
grep -ci 'fockers' data_files/*
```

Search for more than one term at once
```
grep -ci "fockers\|bronco\|glasgow" data_files/*
```

Useful options:
+ `grep --color=auto` make grep colorful
+ `grep -E` use extended regexps
+ `grep -w` only match whole words
+ `grep -l` print name of files with match
+ `grep -v` inverted matching
