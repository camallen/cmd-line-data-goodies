### Join files together using matching conditions

Join allows you to decide how to combine two files, by default it'll attempt to match on the 1st columns and use an inner join.

Join the first file (-1) by the second column and the second file (-2) by the first
```
join -t, data_files/animals.txt data_files/animal_locations.csv
```

Join the first file (-1) by the 1st column and the second file (-2) by the 2nd
```
join -t, -1 1 -2 2 data_files/plant_locations.csv data_files/animal_locations.csv
```

Outer join via -a. Join the files on 1st file 2nd column and that will replace blanks with 'MISSING PLANT' in the output. The resulting output is defined by -o '0,1.1,2.2' i.e. the join column, the 1st file 1st column, 2nd file 2nd column.
```
join -t, -1 2 -a 1 -e ' MISSING PLANT' -o '0,1.1,2.2' <(cat data_files/animal_locations.csv <(echo Hogwarts, Unicorn)) data_files/plant_locations.csv
```

Useful options:
+ `join -a` print unpairable lines
+ `join -e` replace missing input fields
+ `join -j` equivalent to -1 FIELD -2 FIELD
