SunshineCTF

![Alt text](screenshots/sunshinectf1.png)

Hosted by Hack@UCF in Orlando, Florida

This document contains the writeup of three challenges which I worked on for my team.

-------------------------------------------------------------------------------------

Title: BeepBoop Blog
Category: Web
Points: 100

![Alt text](screenshots/beepboopblog1.png)

The challenge says "A few robots got together and started a blog! It's full of posts that make absolutely no sense, but a little birdie told me that one of them left a secret in their drafts. Can you find it?".

So first lets see what the link does.

![Alt text](screenshots/beepboopblog2.png)

Here, we see that this webpage contains a lot of posts. On checking with Find, we see that there are around 1023 such posts. When we click "View All...", we get the post contents.

Example:
![Alt text](screenshots/beepboopblog3.png)

Now, the first thought that came to my mind was to check contents of all the posts to see if they contain the flag. This could be easily done with Burp, as we could see the request and then search in the content of all visible posts at once.

On checking the source of the page, I saw that it fetches individual posts in the format /post/{post_id}.

![Alt text](screenshots/beepboopblog4.png)

So, let us access an individual post.

Example: https://beepboop.web.2023.sunshinectf.games/post/1/

Following was the result:

![Alt text](screenshots/beepboopblog5.png)

Here, we see '"hidden":false'. Seeing this, I knew that there would be posts which are hidden and would have hidden set as True. So, to search for such posts, I used a simple python script.

![Alt text](screenshots/beepboopblog6.png)

This script gave the flag.

![Alt text](screenshots/beepboopblog7.png)

-------------------------------------------------------------------------------------

Title: BeepBoop Cryptography
Category: Crypto
Points: 100

![Alt text](screenshots/beepboopcrypto1.png)

The challenge has given a file "BeepBoop" and says "Detected failure in challenge upload. Original author terminated. Please see attached file BeepBoop for your flag... human.". So, we know that the flag will be in the file.

Let's download the file and open it's contents with notepad.

![Alt text](screenshots/beepboopcrypto2.png)

We see that it contains the words "beep" and "boop" written multiple times. It can be binary data where "beep" is "0" and "boop" is "1", or it can be morse code too. Let's test the binary theory. On converting "beep" to "0" and "boop" to "1", we get the following:

0 0 0 0 1 0 1 0 0 1 1 0 0 1 1 0 0 1 1 0 1 0 0 0 0 1 1 0 0 0 0 1 0 1 1 1 1 0 1 1 0 1 1 1 0 0 1 0 0 1 1 0 1 0 1 1 0 1 1 0 0 1 1 1 0 1 1 1 0 0 1 0 0 1 1 0 0 1 0 1 0 1 1 1 1 0 1 0 0 1 1 1 0 1 1 0 0 1 1 0 0 0 0 1 0 1 1 0 1 1 1 0 0 1 1 0 0 1 1 1 0 1 1 1 0 0 1 0 0 0 1 0 1 1 0 1 0 1 1 1 0 0 1 0 0 1 1 0 1 0 1 1 0 1 1 0 0 1 1 1 0 1 1 1 0 0 1 0 0 1 1 0 0 1 0 1 0 1 1 1 1 0 1 0 0 1 1 1 0 1 1 0 0 1 1 0 0 0 0 1 0 1 1 0 1 1 1 0 0 1 1 0 0 1 1 1 0 1 1 1 0 0 1 0 0 0 1 0 1 1 0 1 0 1 1 1 0 0 1 0 0 1 1 0 1 0 1 1 0 1 1 0 0 1 1 1 0 1 1 1 0 0 1 0 0 1 1 0 0 1 0 1 0 1 1 1 1 0 1 0 0 1 1 1 0 1 1 0 0 1 1 0 0 0 0 1 0 1 1 0 1 1 1 0 0 1 1 0 0 1 1 1 0 1 1 1 0 0 1 0 0 1 1 1 1 1 0 1

Now, let's input it to https://cryptii.com/ and decode it with multiple available options.

When decoded with ROT13, we get the flag.

![Alt text](screenshots/beepboopcrypto3.png)

-------------------------------------------------------------------------------------

Title: Hotdog Stand
Category: Web
Points: 100

![Alt text](screenshots/hotdogstand1.png)

The link of the challenge sends us to a LogIn page, which accepts a Robot ID and an Access Code to give access.

![Alt text](screenshots/hotdogstand2.png)

First objective here is to bypass this. So, lets take a look at robots.txt file for the site, as they mention robot a lot. (No harm in trying)

![Alt text](screenshots/hotdogstand3.png)

Here, we get three things - /configs, /backups, /hotdog-database/ . When I tried to access these, nothing happened for /configs and /backups, but a file got downloaded.

![Alt text](screenshots/hotdogstand4.png)

As the extension is ".db", I tried to view it using "https://sqliteviewer.app/".

![Alt text](screenshots/hotdogstand5.png)

On checking the credentials tab, I can see the credentials in plain text.

![Alt text](screenshots/hotdogstand6.png)

Username: hotdogstand
Password: slicedpicklesandonions
Role: admin

Let us use these credentials to log in.

![Alt text](screenshots/hotdogstand7.png)

I was able to log in successfully and got the flag.

![Alt text](screenshots/hotdogstand8.png)
