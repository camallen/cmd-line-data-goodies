### Edit streams of data

Ever wanted to edit a stream of data, line by line on the fly? Then sed is for you! Sed will remove your specified matches and replace them with your desired changes.

Remove all $ signs with £ from the example file
```
sed 's/\$/£/g' data_files/balances.csv
```

Remove the commas from the monetary columns using capture groups with ()
```
sed 's/\([0-9]\),\([0-9]\)/\1\2/g' data_files/balances.csv
```

Remove a line that matches your search
```
sed '/jack/d' data_files/balances.csv
```

Edit a file in place of itself (this will change the source file)
```
sed -i '' 's/\$/£/g' data_files/balances.csv
````

Useful options:
+ `sed -i '.bak'` Edit files in-place, saving backups with the specified extension.
+ `sed -i ''` Edit in place with a zero-length extension to not create a backup.
+ `sed -E` use extended (modern) regular expressions
