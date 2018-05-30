### File Encodings

Convert files between different encodings, sometimes useful for when receive a file in non UTF encoding scheme or you need to send a file in another scheme.

What does the original file look like? Simples right...
```
cat data_files/example-text.txt
```

Example Converting from UTF-8 to US-ASCII
```
iconv -f UTF-8 -t US-ASCII < data_files/example-text.txt
```

Note the error converting to the US-ASCII, try -c
```
iconv -c -f UTF-8 -t US-ASCII < data_files/example-text.txt
```

Example Converting to latin1 (ISO-8859-1) from UTF-8
```
iconv -f UTF-8 -t ISO-8859-1 < data_files/example-text.txt
```

Useful options:
+ `iconv -l` list all known encodings
+ `iconv -c` silently discard characters that cannot be converted
