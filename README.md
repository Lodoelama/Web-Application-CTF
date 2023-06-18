# CTF Challenge: 'Rekall Memory Intrusion'

![HTML](https://img.shields.io/badge/-HTML-E34F26?style=for-the-badge&logo=HTML5&logoColor=white)
![PHP](https://img.shields.io/badge/-PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)
![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Networking](https://img.shields.io/badge/-Networking-5896AB?style=for-the-badge&logo=cisco&logoColor=white)

## Objective

I embarked on a Capture The Flag (CTF) challenge that required me to exploit multiple vulnerabilities in the 'Rekall' web application to capture 15 flags. Each flag represented a common vulnerability found in insecure web applications.

## Preparation

After logging into Kali and navigating to the correct directory, I started the Docker container that held the 'Rekall' web application. I accessed the application at `http://192.168.14.35` and clicked "Get Started".

## Flags

### Flag 1: Reflected XSS on 'Welcome' Page
![flag 1](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/4f70f228-883e-40fd-b6ca-55baff4289e7)


I entered `<script>alert('XSS');</script>` in the 'Put Your Name Here' field, triggering an alert pop-up and revealing the first flag due to a reflected Cross-Site Scripting (XSS) vulnerability.

### Flag 2: XSS Payload in 'Choose Your Character' Field
![flag 2 xss input validation bypass](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/4877b816-3146-4e23-9011-348ea27e8794)

On the 'Memory-Planner' page, I bypassed input validation by using a cleverly formatted script: `<SCRscriptIPT>alert(“Hello”);</SCRscriptIPT>`. This confirmed an XSS vulnerability and revealed the second flag.
![flag 2 ](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/b4d78dc2-c095-45ce-b29d-5f5f0e991be7)

### Flag 3: Stored XSS on 'Comments' Page
![Flag 3 ](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/985e4c09-6f46-45f5-a4a3-fb8eca046d63)

On the 'Comments' page, I exploited a stored XSS vulnerability with the payload `<dummy<dummy<script>alert('Hello');</dummy</script></dummy>`, which revealed the third flag.

### Flag 4: Sensitive Data Exposure in 'About Rekall' Response Header
![flag 4 ](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/422cf223-656e-4277-9c20-5d194295bd6f)

By inspecting the response headers of the 'About Rekall' page, I found sensitive information and captured the fourth flag.

### Flag 5: Local File Inclusion on 'Memory-Planner' Page
![flag 5](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/bf66a8b1-49ce-44b1-b3c2-05ea709fcc16)

On the 'Memory-Planner' page, I exploited a Local File Inclusion (LFI) vulnerability by uploading a .php file, obtaining the fifth flag.

### Flag 6: LFI Exploit with File Name Manipulation
![flag 6](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/9a1b830b-d9c5-4cb9-9d6b-bb3272a57014)

To reveal the sixth flag, I further exploited the LFI vulnerability on the 'Memory-Planner' page by renaming a .jpg file to .php and uploading it.

### Flag 7: SQL Injection on 'Login' Page
![flag 7 process cred dump](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/062f0fa3-7719-436f-98a5-1029c976d6ee)

![flag 7 ](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/9199a5c4-15f3-4cd6-b7b0-434aac20b776)

With the username obtained from a later directory traversal attack, I performed a simple SQL Injection attack on the 'Login' page to capture flag seven.

### Flag 8: Sensitive Data Exposure on 'Login' Page
"C:\Users\Lodoe Lama\Desktop\flag 8 creds .png"
I discovered the eighth flag within the HTML source code of the 'Login' page, where the login credentials were exposed.
![flag 8](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/3e50f856-c9c1-4bfa-98fa-570b22b5bacb)

### Flag 9: Sensitive Data Exposure via 'Robots.txt'
![flag 9 ](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/78d1b5c4-d8cc-441a-9e2b-885b48de7330)

By accessing the 'robots.txt' file, I was able to uncover sensitive data and capture the ninth flag.

### Flag 10: Command Injection on 'Networking' Page
![flag 10](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/9ea1790f-bb86-414f-95f6-4e353d474f6f)

I executed a command injection on the 'Networking' page using the payload `www.example.com; cat vendors.txt`, revealing the tenth flag.

### Flag 11: Advanced Command Injection on 'Networking' Page
![flag 11](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/4fc43b23-9a1d-4f1a-bce0-c4d6086cc173)

Using an advanced command injection payload `www.example.com | cat vendors.txt` on the 'Networking' page, I secured the eleventh flag.

### Flag 12: Brute Force Attack on 'Login' Page
![flag 12](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/fc1f8d08-21cf-4d0b-931c-700a88dfb8b2)

I brute-forced the login credentials on the 'Login' page using Burp Suite Intruder and the password 'melina', leading me to the twelfth flag.

### Flag 13: PHP Injection on 'Souvenirs' Page
![flag 13](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/b83e64ad-afbb-47e4-970a-edb715fe7adf)

By appending `;system('cat/etc/passwd')` to the URL of the 'Souvenirs' page, I executed a PHP Injection attack which unveiled the thirteenth flag.

### Flag 14: Session Management Exploit on 'Admin Legal Data' Page
![flag 14](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/e4de9aff-0e65-444b-9d50-93af844ba019)

I brute-forced the session ID using the Burp Suite Intruder tool on the 'Admin Legal Data' page, successfully capturing the fourteenth flag.

### Flag 15: Directory Traversal on 'Disclaimer' Page
![flag 15 ](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/78deeb3c-0926-4618-9c54-a3c1b39c985f)

I exploited a directory traversal vulnerability on the 'Disclaimer' page to access the contents of directories, revealing the fifteenth and final flag.

## Conclusion

This CTF challenge tested my understanding and application of various exploitation techniques through a range of vulnerabilities common to insecure web applications. It took me approximately 11.3 hours to complete this challenge, demonstrating my tenacity and dedication to enhancing web security. I used a wide range of languages and protocols such as HTML, PHP, JavaScript, and HTTP.
![ctf day one timer ](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/fc8eba83-4d22-4124-b560-387faf04b58f)
 
