# get-poc

#medium #nitescu #web #php #command-injection #rce

> David-Andrei Popa (contact@popadavid.ro)

## Description

Can you get a working POC for this vulnerability?

Flag format: ctf{sha256sum}

## Solution

Analyzing the website, we find out that by adding the parameter `poc` to the URL (`http://34.89.210.219:31613/?poc=`), an error is generated. It turns out we can exploit this RCE-vulnerable parameter, according to this payload: `?poc=var_dump(phpinfo())`.

Using the php `file` function, we can output the contents of the `flag.php` file.

Final payload:

`?poc=var_dump(file('./flag.php'))`

