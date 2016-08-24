The shopt command
=================

Lets suppose you want to list recursively all javascript files on a given directory.

You can easily do that with

    ls src/**/*js

The `**`, also known as `globstar`, from bash documentation, "in a filename expansion
context will match a files and zero or more directories and subdirectories.
If the pattern is followed by a /, only directories and subdirectories match.

Sometimes you may try it and it might not work though.

The flag `globstar` needs to be set on your bash to expand it. Bash has a lot of flags that you can list with

    shopt

and set or unset with `shopt -s FLAG` and `shopt -u FLAG`.

So to make it work you need to first set it as

    shopt -s globstar
