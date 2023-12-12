# SunshineCTF Writeup

Hosted by Hack@UCF in Orlando, Florida.

This document contains the writeup of three challenges which I worked on for my team.

![SunshineCTF Overview](screenshots/sunshinectf1.png)

---

## Challenge 1: BeepBoop Blog

**Category**: Web  
**Points**: 100

### Challenge Description

"A few robots got together and started a blog! It's full of posts that make absolutely no sense, but a little birdie told me that one of them left a secret in their drafts. Can you find it?"

![BeepBoop Blog Challenge](screenshots/beepboopblog1.png)

### Investigation Process

1. **Exploring the Webpage**: The webpage contains about 1023 posts.

   ![BeepBoop Blog Posts](screenshots/beepboopblog2.png)

2. **Post Example**: Viewing individual posts to check their contents.

   ![Post Example](screenshots/beepboopblog3.png)

3. **Analyzing Source Code**: Found that posts are fetched individually in the format `/post/{post_id}`.

   ![BeepBoop Blog Source Code](screenshots/beepboopblog4.png)

4. **Accessing Individual Posts**: Example - `https://beepboop.web.2023.sunshinectf.games/post/1/` revealed a property '"hidden":false'.

   ![Individual Post Access](screenshots/beepboopblog5.png)

5. **Python Script for Hidden Posts**: Used a script to search for posts with 'hidden' set as True.

   ![Python Script](screenshots/beepboopblog6.png)

6. **Flag Discovery**: The script successfully uncovered the flag.

   ![Flag](screenshots/beepboopblog7.png)

---

## Challenge 2: BeepBoop Cryptography

**Category**: Crypto  
**Points**: 100

### Challenge Description

"Detected failure in challenge upload. Original author terminated. Please see attached file BeepBoop for your flag... human."

![BeepBoop Cryptography Challenge](screenshots/beepboopcrypto1.png)

### Steps Taken

1. **File Analysis**: Opening the file showed repetitions of the words "beep" and "boop".

   ![BeepBoop Cryptography File](screenshots/beepboopcrypto2.png)

2. **Decoding Approach**: Interpreted as binary, with "beep" as "0" and "boop" as "1".

3. **Online Decoding Tool**: Inputted binary data into https://cryptii.com/ and decoded with ROT13 to reveal the flag.

   ![Decoded Flag](screenshots/beepboopcrypto3.png)

---

## Challenge 3: Hotdog Stand

**Category**: Web  
**Points**: 100

### Challenge Description

The link of the challenge sends us to a LogIn page, which accepts a Robot ID and an Access Code.

![Hotdog Stand Challenge](screenshots/hotdogstand1.png)

### Investigation Process

1. **Login Page**: Encountered a login page requiring a Robot ID and Access Code.

   ![Login Page](screenshots/hotdogstand2.png)

2. **Exploring robots.txt**: This led to finding directories `/configs`, `/backups`, `/hotdog-database/`.

   ![robots.txt File](screenshots/hotdogstand3.png)

3. **Accessing Directories**: A file was downloaded from `/hotdog-database/`.

   ![Database File Download](screenshots/hotdogstand4.png)

4. **Database Analysis**: Examined the database using "https://sqliteviewer.app/", revealing plain-text credentials.

   ![Database Credentials](screenshots/hotdogstand5.png)

5. **Using the Credentials**: Logged in with the found credentials to access and reveal the flag.

   ![Login Success](screenshots/hotdogstand6.png)

   ![Flag](screenshots/hotdogstand8.png)

---

