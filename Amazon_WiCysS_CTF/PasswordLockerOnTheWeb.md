Challenge: Password Locker on the Web
Points: 100
Category: Web

![Alt text](screenshots/passwordlocker1.png)

![Alt text](screenshots/passwordlocker2.png)

To start, lets try to understand the application.

![Alt text](screenshots/passwordlocker3.png)

The way in which the results change help us to determine that this is not a hash and might be a different kind of cipher. Using Burp, let's enter 100 "a"s and try to see the change in the value.

![Alt text](screenshots/passwordlocker4.png)

Now, let's try to identify what kind of cipher this is. We will use https://www.dcode.fr/cipher-identifier for it.

![Alt text](screenshots/passwordlocker5.png)

Checking the suggestions, we finally reached XOR Cipher. Entering our value we got by using 100 a's as input, we see that we get the flag at 61.

![Alt text](screenshots/passwordlocker6.png)

FLAG: Amazon{This_Flag_Is_Secret_front_end_validation_is_bullet_proof}