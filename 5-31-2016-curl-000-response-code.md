The 000 curl response code
==========================

000 is not a defined HTTP response code. Nevertheless you can
still receive this response code when using curl.

```bash
curl -sL -w "%{http_code} %{url_effective}\n" "url" -o /dev/null
```

will print `000 http://url` if curl didn't receive a HTTP response code.
Reason can be

- failed dns resolution
- connection refused
- connection timed out
- illegal characters in url

among other reasons.
The illegal characters in the url may happen because of new-line differences
between windows and linux formats, if you're doing something similar to

```bash
for url in $(cat urls_file); do
  curl -sL -w "%{http_code} %{url_effective}\n" "$url" -o /dev/null
done
```

and $url was written in a windows machine.

A simple way to solve it is to run the program `dos2unix` over your file, to convert
the line-ends to the right format

```
dos2unix urls_file
```
