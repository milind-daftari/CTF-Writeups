# Bad Actor and Secret Server Challenges

**Points:** 100 + 200 = 300  
**Category:** Recon  

## Bad Actor Challenge

### Task
Find a social media account for the user "mickey_z_scott".

![IDCrawl Search Result](screenshots/bass1.png)

### Process
1. **Search on IDCrawl:**  
   Searched for `mickey_z_scott` on [IDCrawl](https://www.idcrawl.com/u/mickey_z_scott).

2. **Findings:**  
   - Discovered a Twitter account and found the flag in the bio.
   - Also found the username `scottyisthebest`.
   ![Twitter Account and Flag](screenshots/bass2.png)

### Flag for Bad Actor
`Amazon{0S1NT_1s_c00l}`

## Secret Server Challenge

### Task
Search for "scottyisthebest" on GitHub.

### Process
1. **GitHub Profile Search:**  
   Found a GitHub profile with a few commits.
   ![GitHub Profile](screenshots/bass3.png)

2. **Commit Analysis:**  
   Checked every commit and discovered a link in the first commit: [https://discord.gg/VKPPBvpMcv](https://discord.gg/VKPPBvpMcv).  
   ![First Commit Link](screenshots/bass4.png)

3. **Joining Discord Server:**  
   Joined the Discord server using the provided link.
   ![Discord Server Invitation](screenshots/bass5.png)

### Flag
`Amazon{Y0u_h@v3_m@st3red_0S1NT}`
