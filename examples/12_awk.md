### AWK for amazing text processing on files / streams

Want to do some complicated processing or reporting but can't find the right tools to get the job done. AWK may be just the trick, it's a fully fledged programming language designed to process text data. https://en.wikipedia.org/wiki/AWK

find words in a file (like grep)
```
awk '/Fockers/' data_files/deniro_rotten_tomato_scores.csv
```
this time ignoring case, note the function call on the $0 variable
```
awk 'tolower($0) ~ /fockers/' data_files/deniro_rotten_tomato_scores.csv
```

Print the 2nd and 3rd columns of the match, ala grep + cut. -F, tells awk it's a csv delimted file
```
awk -F, '/Fockers/ { print $2 " - " $3 }' data_files/deniro_rotten_tomato_scores.csv
```

Get the 5th line (NumRecord) from the file
```
awk -F, 'NR == 5' data_files/deniro_rotten_tomato_scores.csv
```

Print the line number and content when the 3rd column contains fockers
```
awk -F, ' $3 ~ /Fockers/ { print NR, $0 } ' data_files/deniro_rotten_tomato_scores.csv
```

Or a straight string match if you know what you are looking for, note the \" escaping as the row has these values in it
```
awk -F, ' $3 == " \"Little Fockers\"" { print NR, $0 } ' data_files/deniro_rotten_tomato_scores.csv
```

Find me all the lines that are from the year 2000 and what line number they are on
```
awk -F, ' $1 == 2000 { print NR, $0 } ' data_files/deniro_rotten_tomato_scores.csv
```

Now let's find all the movies between 1979 and 1983
```
awk -F, ' $1 >= 1979 && $1 <= 1983 { print NR, $0 } ' data_files/deniro_rotten_tomato_scores.csv
```

How about all movies after 2000 with a score on or over 80
```
awk -F, ' $1 >= 2000 && $2 >= 80 { print NR, $0 } ' data_files/deniro_rotten_tomato_scores.csv
```

Sum all the scores
```
awk -F, '{ x+=$2 } END { print x }' data_files/deniro_rotten_tomato_scores.csv
```

Sum all the scores for movies before 2000
```
awk -F, '$1 < 2000 { x+=$2 } END { print x }' data_files/deniro_rotten_tomato_scores.csv
```

Average of the scores for movies before 2000, note we can't use of num rows(NR) here, instead we have to use another variable to count the matches
```
awk -F, '$1 < 2000 { x+=$2;y+=1 } END { print x / y }' data_files/deniro_rotten_tomato_scores.csv
```

Get the dimensions of a file
```
awk -F, 'END { print NF, NR }' data_files/deniro_rotten_tomato_scores.csv
```
With some context
```
awk -F, 'BEGIN { print "COLS", "ROWS" }; END { print NF, NR }' data_files/deniro_rotten_tomato_scores.csv
```
Or with string formatting
```
awk -F, 'END { printf "Num columns: %s, Num rows: %s\n", NF, NR }' data_files/deniro_rotten_tomato_scores.csv
```

Print lines that appear only twice
```
awk -F, '++seen[$0] == 2' data_files/duplicates.csv
```

Print lines that appear more than two times. What happens when you replace the > with >=?
```
awk -F, '++seen[$0] > 2' data_files/duplicates.csv
```

Remove duplicate lines
```
# Consecutive lines
awk 'a !~ $0; {a=$0}' data_files/duplicates.csv

# Nonconsecutive lines
awk '! a[$0]++' data_files/duplicates.csv

# more efficient way
awk '!($0 in a) {a[$0];print}' data_files/duplicates.csv
```

Substitute values ala the command sed
```
awk '{gsub(/Taxi|Fockers/, "Rabbit"); print}' data_files/deniro_rotten_tomato_scores.csv | grep Rabbit
```

Combine CSV files ignoring but keeping the header in output
```
awk 'FNR==1 && NR!=1{next;}{print}' data_files/balances*.csv
```

Split large files up and rename on the fly, ala the command split
```
sed '1d' data_files/deniro_rotten_tomato_scores.csv | awk 'NR%50==1{x="data_files/deniro_rotten_tomato_scores_"++i".csv";}{print > x}'
```

Useful options:
+ There is so much in awk, read the man page and tutorials for more information
