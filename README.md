# CTF Challenge: 'Rekall Web Application CTF'

![HTML](https://img.shields.io/badge/-HTML-E34F26?style=for-the-badge&logo=HTML5&logoColor=white)
![PHP](https://img.shields.io/badge/-PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)
![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Networking](https://img.shields.io/badge/-Burpsuite-00000?style=for-the-badge&logo=cisco&logoColor=white)

## Objective

I embarked on a Capture The Flag (CTF) challenge that required me to exploit multiple vulnerabilities in the 'Rekall' web application to capture 15 flags. Each flag represented a common vulnerability found in insecure web applications.

## Preparation

After logging into Kali and navigating to the correct directory, I started the Docker container that held the 'Rekall' web application. I accessed the application at `http://192.168.14.35` and clicked "Get Started".

## Flags

### Flag 1: Reflected XSS on 'Welcome' Page

I entered `<script>alert('XSS');</script>` in the 'Put Your Name Here' field, triggering an alert pop-up and revealing the first flag due to a reflected Cross-Site Scripting (XSS) vulnerability.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/4f70f228-883e-40fd-b6ca-55baff4289e7" width="600" height="450">

### Flag 2: XSS Payload in 'Choose Your Character' Field

On the 'Memory-Planner' page, I bypassed input validation by using a cleverly formatted script: `<SCRscriptIPT>alert(“Hello”);</SCRscriptIPT>`. This confirmed an XSS vulnerability and revealed the second flag.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/4877b816-3146-4e23-9011-348ea27e8794" width="600" height="450">
<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/b4d78dc2-c095-45ce-b29d-5f5f0e991be7" width="600" height="450">

### Flag 3: Stored XSS on 'Comments' Page

On the 'Comments' page, I exploited a stored XSS vulnerability with the payload `<dummy<dummy<script>alert('Hello');</dummy</script></dummy>`, which revealed the third flag.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/985e4c09-6f46-45f5-a4a3-fb8eca046d63" width="600" height="450">

### Flag 4: Sensitive Data Exposure in 'About Rekall' Response Header

By inspecting the response headers of the 'About Rekall' page, I found sensitive information and captured the fourth flag.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/422cf223-656e-4277-9c20-5d194295bd6f" width="600" height="450">

### Flag 5: Local File Inclusion on 'Memory-Planner' Page

On the 'Memory-Planner' page, I exploited a Local File Inclusion (LFI) vulnerability by uploading a .php file, obtaining the fifth flag.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/bf66a8b1-49ce-44b1-b3c2-05ea709fcc16" width="600" height="450">

### Flag 6: LFI Exploit with File Name Manipulation

To reveal the sixth flag, I further exploited the LFI vulnerability on the 'Memory-Planner' page by renaming a .jpg file to .php and uploading it.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/9a1b830b-d9c5-4cb9-9d6b-bb3272a57014" width="600" height="450">

### Flag 7: SQL Injection on 'Login' Page

With the username obtained from a later directory traversal attack, I performed a simple SQL Injection attack on the 'Login' page to capture flag seven.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/062f0fa3-7719-436f-98a5-1029c976d6ee" width="600" height="450">
<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/9199a5c4-15f3-4cd6-b7b0-434aac20b776" width="600" height="450">

### Flag 8: Sensitive Data Exposure on 'Login' Page

I discovered the eighth flag within the HTML source code of the 'Login' page, where the login credentials were exposed.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/3e50f856-c9c1-4bfa-98fa-570b22b5bacb" width="600" height="450">

### Flag 9: Sensitive Data Exposure via 'Robots.txt'

By accessing the 'robots.txt' file, I was able to uncover sensitive data and capture the ninth flag.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/78d1b5c4-d8cc-441a-9e2b-885b48de7330" width="600" height="450">

### Flag 10: Command Injection on 'Networking' Page

I executed a command injection on the 'Networking' page using the payload `www.example.com; cat vendors.txt`, revealing the tenth flag.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/9ea1790f-bb86-414f-95f6-4e353d474f6f" width="600" height="450">

### Flag 11: Advanced Command Injection on 'Networking' Page

Using an advanced command injection payload `www.example.com | cat vendors.txt` on the 'Networking' page, I secured the eleventh flag.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/4fc43b23-9a1d-4f1a-bce0-c4d6086cc173" width="600" height="450">

### Flag 12: Brute Force Attack on 'Login' Page

I performed a brute force attack on the 'Login' page using a dictionary attack, uncovering the twelfth flag.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/fea02f16-4c3f-4abf-a1ee-192c1ce1bb24" width="600" height="450">

### Flag 13: Privilege Escalation on 'Comments' Page

By exploiting a privilege escalation vulnerability on the 'Comments' page, I uncovered the thirteenth flag.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/60ed656a-512f-4007-ad49-b7e5dc212363" width="600" height="450">

### Flag 14: Directory Traversal Attack

I performed a Directory Traversal Attack, which exposed sensitive user data and led to the fourteenth flag.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/d5d5c059-7d3e-42f1-93ba-7cb296ecb23e" width="600" height="450">

### Flag 15: Arbitrary File Upload on 'Profile Picture' Page

I uploaded a malicious .php file disguised as a .jpg file on the 'Profile Picture' page, exposing the final flag.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/1432e64b-3f84-4cc6-bbc6-0e9b570574c3" width="600" height="450">

## Conclusion

This challenge has reinforced my understanding of various web application vulnerabilities and how they can be exploited in a real-world scenario. Through persistence, I was able to successfully capture all 15 flags and complete the CTF challenge. I'm eager to apply my expanded knowledge to future cybersecurity endeavors.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/0a6dc05c-b2e9-4746-bf15-265d8718ed68" width="550" height="450">

