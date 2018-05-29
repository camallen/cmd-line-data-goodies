### File Encodings

Convert files between different encodings, sometimes useful for when receive a file in non UTF encoding scheme or you need to send a file in another scheme.

What does the original file look like? Simples right...
```
cat data_files/example-text.txt
```

Example Converting from US-ASCII to UTF-8
```
iconv -f US-ASCII -t UTF-8 < data_files/example-text.txt
```

Example Converting from latin1 (ISO-8859-1) to UTF-8
```
iconv -f ISO-8859-1 -t UTF-8 < data_files/example-text.txt
```

Note the error converting to the US-ASCII?

Useful options:
+ `iconv -l` list all known encodings
+ `iconv -c` silently discard characters that cannot be converted

Converting
-f (from) latin1 (ISO-8859-1)
-t (to) standard UTF_8
```
iconv -f ISO-8859-1 -t UTF-8 < input.txt > output.txt
```
