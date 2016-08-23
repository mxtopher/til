Finding files that contain a string on command line
===================================================

There is a well known way to find files that contain a given
string on unix systems:

    grep -nri "string to search" path/to/search

searches for the string rescursively `(-r)`, ignoring case `(-i)`,
on `path/to/search`, and prints both the file name and the line `(-n)`
the string was found. you can even filter the files you are searching
into with something like `path/to/search/*controller.cs`

There is a less know counterpart on windows (cmd) that can be used for the same
result:

    findstr /s /n /i /p /c:"string to search" path/to/search

Searches for the literal string `(/c)`, with spaces and special characters
allowed, recursively `(/s)`, ignoring case `(/i)`, skipping any file that
contains non-printable characters `(/p)` on the folder `path/to/search`.
It will print the file name and the line number it was found `(-n)`
You can similarly use `path/to/search/*html` or any other format.

 
