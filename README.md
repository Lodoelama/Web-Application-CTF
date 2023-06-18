# CTF Challenge: 'Rekall Memory Intrusion'

![HTML](https://img.shields.io/badge/-HTML-E34F26?style=for-the-badge&logo=HTML5&logoColor=white)
![PHP](https://img.shields.io/badge/-PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)
![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Networking](https://img.shields.io/badge/-Networking-5896AB?style=for-the-badge&logo=cisco&logoColor=white)

## Objective

The aim of this Capture The Flag (CTF) challenge was to exploit multiple vulnerabilities in the 'Rekall' web application to capture 15 flags. Each flag represents a common vulnerability found in insecure web applications.

## Preparation

We logged into Kali and navigated to the relevant directory, then we pulled and started the Docker container. We accessed the web application at `http://192.168.14.35` and clicked "Get Started".

## Flags

### Flag 1: Reflected XSS on 'Welcome' Page

We entered `<script>alert('XSS');</script>` in the 'Put Your Name Here' field, resulting in an alert pop-up due to a reflected Cross-Site Scripting (XSS) vulnerability.

### Flag 2: XSS Payload in 'Choose Your Character' Field

On the 'Memory-Planner' page, we bypassed input validation by using a cleverly formatted script: `<SCRscriptIPT>alert(“Hello”);</SCRscriptIPT>`. The script alert confirmed an XSS vulnerability, revealing the second flag.

### Flag 3: Stored XSS on 'Comments' Page

On the 'Comments' page, we triggered a stored XSS vulnerability with the following payload: `<dummy<dummy<script>alert('Hello');</dummy</script></dummy>`. This caused a pop-up and revealed the third flag.

### Flag 4: Sensitive Data Exposure in 'About Rekall' Response Header

Inspecting the response headers of the 'About Rekall' page revealed sensitive information, representing our fourth flag.

### Flag 5: Local File Inclusion on 'Memory-Planner' Page

The second field on the 'Memory-Planner' page was vulnerable to Local File Inclusion (LFI). We exploited this by uploading a .php file to obtain the fifth flag.

### Flag 6: LFI Exploit with File Name Manipulation

We further exploited the LFI vulnerability on the 'Memory-Planner' page by renaming a .jpg file to .php and uploading it. This successfully revealed our sixth flag.

### Flag 7: SQL Injection on 'Login' Page

With the username obtained from the directory traversal attack (mentioned later), we performed a simple SQL Injection attack on the 'Login' page to capture flag seven.

### Flag 8: Sensitive Data Exposure on 'Login' Page

We discovered the credentials needed for login within the HTML source code of the 'Login' page, revealing the eighth flag.

### Flag 9: Sensitive Data Exposure via 'Robots.txt'

By accessing the 'robots.txt' file, we uncovered sensitive data leading us to our ninth flag.

### Flag 10: Command Injection on 'Networking' Page

We executed a command injection on the 'Networking' page using the payload `www.example.com; cat vendors.txt` to capture the tenth flag.

### Flag 11: Advanced Command Injection on 'Networking' Page

An advanced command injection on the 'Networking' page using the payload `www.example.com | cat vendors.txt` helped us secure flag eleven.

### Flag 12: Brute Force Attack on 'Login' Page

We brute-forced the login credentials on the 'Login' page using Burp Suite Intruder, using the password 'melina'. This led us to the twelfth flag.

### Flag 13: PHP Injection on 'Souvenirs' Page

By appending `;system('cat/etc/passwd')` to the URL of the 'Souvenirs' page, we executed a PHP Injection attack which unveiled the thirteenth flag.

### Flag 14: Session Management Exploit on 'Admin Legal Data' Page

We brute-forced the session ID using the Burp Suite Intruder tool on the 'Admin Legal Data' page, successfully capturing the fourteenth flag.

### Flag 15: Directory Traversal on 'Disclaimer' Page

We exploited a directory traversal vulnerability on the 'Disclaimer' page to access the contents of directories, revealing the fifteenth and final flag.

## Conclusion

This CTF challenge offered a diverse range of vulnerabilities common to insecure web applications, testing our understanding and application of various exploitation techniques. We employed a wide range of languages and protocols such as HTML, PHP, JavaScript, and HTTP.
