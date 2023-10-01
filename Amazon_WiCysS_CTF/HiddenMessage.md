Challenges: Hidden Message
Points: 100
Category: Steg

![Alt text](screenshots/hiddenmessage1.png)

Here, we are provided an image, logo.jpg. 

![Alt text](screenshots/hiddenmessage2.png)

Let's use exiftool in Kali Linux to get more information about the image.

exiftool logo.jpg

![Alt text](screenshots/hiddenmessage3.png)

We see the comment -> QW1hem9ue1N0M24wZ3JAcGh5XzEkX2hAcmR9. On decoding with Base64, we get the flag.

echo "QW1hem9ue1N0M24wZ3JAcGh5XzEkX2hAcmR9" | base64 -d

![Alt text](screenshots/hiddenmessage4.png)

FLAG: Amazon{St3n0gr@phy_1$_h@rd} 