# CTF Challenge: 'Rekall Web Application CTF'

![HTML](https://img.shields.io/badge/-HTML-E34F26?style=for-the-badge&logo=HTML5&logoColor=white)
![PHP](https://img.shields.io/badge/-PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)
![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Burp Suite](https://img.shields.io/badge/-Burp%20Suite-FF6400?style=for-the-badge&logo=burp%20suite&logoColor=white)

## Objective

Embarked on a Capture The Flag (CTF) challenge to exploit multiple vulnerabilities in the 'Rekall' web application to capture 15 flags. Each flag represented a common vulnerability found in insecure web applications.

## Preparation

After logging into Kali and navigating to the correct directory, started the Docker container that held the 'Rekall' web application. Accessed the application at `http://192.168.14.35` and clicked "Get Started".

## Flags

The detailed information about each flag and the corresponding exploitation technique are as follows. Click on the flags to see the associated images.

<details>
<summary><strong>Flag 1: Reflected XSS on 'Welcome' Page</strong></summary>
<br>
On the 'Welcome' page, a reflected Cross-Site Scripting (XSS) vulnerability was identified by inputting `<script>alert('XSS');</script>` in the 'Put Your Name Here' field, which triggered an alert pop-up. This vulnerability is a type of XSS, where malicious scripts are injected into otherwise benign and trusted websites.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/4f70f228-883e-40fd-b6ca-55baff4289e7" width="400" alt="Flag 1">
</p>
</details>

<details>
<summary><strong>Flag 2: XSS Payload in 'Choose Your Character' Field</strong></summary>
<br>
On the 'Memory-Planner' page, a Cross-Site Scripting vulnerability was identified. By bypassing input validation with the payload `<SCRscriptIPT>alert(“Hello”);</SCRscriptIPT>`, the second flag was revealed.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/4877b816-3146-4e23-9011-348ea27e8794" width="400" alt="Flag 2">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/b4d78dc2-c095-45ce-b29d-5f5f0e991be7" width="400" alt="Flag 2">
</p>
</details>

<details>
<summary><strong>Flag 3: Stored XSS on 'Comments' Page</strong></summary>
<br>
The 'Comments' page had a stored XSS vulnerability. By using the payload `<dummy<dummy<script>alert('Hello');</dummy</script></dummy>`, the third flag was revealed.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/985e4c09-6f46-45f5-a4a3-fb8eca046d63" width="400" alt="Flag 3">
</p>
</details>

<details>
<summary><strong>Flag 4: Sensitive Data Exposure in 'About Rekall' Response Header</strong></summary>
<br>
Sensitive information was found in the HTTP response headers of the 'About Rekall' page, leading to the discovery of the fourth flag.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/422cf223-656e-4277-9c20-5d194295bd6f" width="400" alt="Flag 4">
</p>
</details>

<details>
<summary><strong>Flag 5: Local File Inclusion on 'Memory-Planner' Page</strong></summary>
<br>
The 'Memory-Planner' page contained a Local File Inclusion (LFI) vulnerability. By uploading a .php file, the fifth flag was obtained.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/bf66a8b1-49ce-44b1-b3c2-05ea709fcc16" width="400" alt="Flag 5">
</p>
</details>

<details>
<summary><strong>Flag 6: LFI Exploit with File Name Manipulation</strong></summary>
<br>
Exploiting the LFI vulnerability on the 'Memory-Planner' page, the sixth flag was discovered by renaming a .jpg file to .php and uploading it.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/9a1b830b-d9c5-4cb9-9d6b-bb3272a57014" width="400" alt="Flag 6">
</p>
</details>

<details>
<summary><strong>Flag 7: SQL Injection on 'Login' Page</strong></summary>
<br>
A SQL Injection (SQLi) vulnerability was found on the 'Login' page. Exploiting this vulnerability using the username obtained from a directory traversal attack revealed the seventh flag.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/062f0fa3-7719-436f-98a5-1029c976d6ee" width="400" alt="Flag 7">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/9199a5c4-15f3-4cd6-b7b0-434aac20b776" width="400" alt="Flag 7">
</p>
</details>

<details>
<summary><strong>Flag 8: Sensitive Data Exposure on 'Login' Page</strong></summary>
<br>
The eighth flag was discovered within the HTML source code of the 'Login' page, where the login credentials were mistakenly exposed.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/3e50f856-c9c1-4bfa-98fa-570b22b5bacb" width="400" alt="Flag 8">
</p>
</details>

<details>
<summary><strong>Flag 9: Sensitive Data Exposure via 'Robots.txt'</strong></summary>
<br>
By accessing the 'robots.txt' file, sensitive data was uncovered, leading to the capture of the ninth flag.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/78d1b5c4-d8cc-441a-9e2b-885b48de7330" width="400" alt="Flag 9">
</p>
</details>

<details>
<summary><strong>Flag 10: Command Injection on 'Networking' Page</strong></summary>
<br>
Exploiting a command injection vulnerability on the 'Networking' page using the payload `www.example.com; cat vendors.txt`, the tenth flag was revealed.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/9ea1790f-bb86-414f-95f6-4e353d474f6f" width="400" alt="Flag 10">
</p>
</details>

<details>
<summary><strong>Flag 11: Advanced Command Injection on 'Networking' Page</strong></summary>
<br>
Using an advanced command injection payload `www.example.com | cat vendors.txt` on the 'Networking' page, the eleventh flag was secured.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/4fc43b23-9a1d-4f1a-bce0-c4d6086cc173" width="400" alt="Flag 11">
</p>
</details>

<details>
<summary><strong>Flag 12: Brute Force Attack on 'Login' Page</strong></summary>
<br>
A brute force attack was performed on the 'Login' page using a dictionary attack, uncovering the twelfth flag.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/fea02f16-4c3f-4abf-a1ee-192c1ce1bb24" width="400" alt="Flag 12">
</p>
</details>

<details>
<summary><strong>Flag 13: PHP Injection on 'Souvenirs' Page</strong></summary>
<br>
Exploiting a PHP injection vulnerability on the 'Souvenirs' page using the payload `;system(‘cat/etc/passwd’)` revealed the thirteenth flag.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/60ed656a-512f-4007-ad49-b7e5dc212363" width="400" alt="Flag 13">
</p>
</details>

<details>
<summary><strong>Flag 14: Session Management Vulnerability on 'admin_legal_data.php' Page</strong></summary>
<br>
Exploiting a session management vulnerability on the 'admin_legal_data.php' page using the Burp Intruder tool to brute force session IDs, the fourteenth flag was captured.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/d5d5c059-7d3e-42f1-93ba-7cb296ecb23e" width="400" alt="Flag 14">
</p>
</details>

<details>
<summary><strong>Flag 15: Directory Traversal on 'disclaimer.php' Page</strong></summary>
<br>
The fifteenth flag was achieved by exploiting a directory traversal vulnerability on the 'disclaimer.php' page. Navigating the contents of the directory due to a common injection exploit led to the exposure of the fifteenth and final flag.

<p align="center">
  <img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/1432e64b-3f84-4cc6-bbc6-0e9b570574c3" width="400" alt="Flag 15">
</p>
</details>


## Conclusion

This challenge has reinforced my understanding of various web application vulnerabilities and how they can be exploited in a real-world scenario. Through persistence, I was able to successfully capture all 15 flags and complete the CTF challenge. I'm eager to apply my expanded knowledge to future cybersecurity endeavors.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/0a6dc05c-b2e9-4746-bf15-265d8718ed68" width="550" height="450">

