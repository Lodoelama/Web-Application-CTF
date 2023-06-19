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

### Flag 1: Reflected XSS on 'Welcome' Page

On the 'Welcome' page, a reflected Cross-Site Scripting (XSS) vulnerability was identified by inputting `<script>alert('XSS');</script>` in the 'Put Your Name Here' field, which triggered an alert pop-up. This vulnerability is a type of XSS, where malicious scripts are injected into otherwise benign and trusted websites.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/4f70f228-883e-40fd-b6ca-55baff4289e7)

### Flag 2: XSS Payload in 'Choose Your Character' Field

The 'Memory-Planner' page was found to have a Cross-Site Scripting vulnerability which was exploited using the payload: `<SCRscriptIPT>alert(“Hello”);</SCRscriptIPT>`. This bypassed the input validation and revealed the second flag. XSS attacks enable the attacker to inject client-side scripts into web pages viewed by other users and potentially bypass access controls.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/4877b816-3146-4e23-9011-348ea27e8794)
![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/b4d78dc2-c095-45ce-b29d-5f5f0e991be7)

### Flag 3: Stored XSS on 'Comments' Page

A stored XSS vulnerability was identified on the 'Comments' page. The payload `<dummy<dummy<script>alert('Hello');</dummy</script></dummy>` was used, which unlike a reflected XSS attack, stores the payload on the server. This resulted in the third flag.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/985e4c09-6f46-45f5-a4a3-fb8eca046d63)

### Flag 4: Sensitive Data Exposure in 'About Rekall' Response Header

I found sensitive information within the HTTP response headers of the 'About Rekall' page. Response headers often contain metadata and properties about the requested page and can accidentally reveal sensitive information if not correctly managed. The exposure of such data yielded the fourth flag.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/422cf223-656e-4277-9c20-5d194295bd6f)

### Flag 5: Local File Inclusion on 'Memory-Planner' Page

A Local File Inclusion (LFI) vulnerability was exploited on the 'Memory-Planner' page. By uploading a .php file, the web application inadvertently executed the file's contents, indicating improper handling of user-supplied input. LFIs can allow attackers to read arbitrary files on a server, leading to sensitive information exposure and potentially further server-side attacks. This vulnerability revealed the fifth flag.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/bf66a8b1-49ce-44b1-b3c2-05ea709fcc16)

### Flag 6: LFI Exploit with File Name Manipulation

The LFI vulnerability on the 'Memory-Planner' page was further exploited using a technique of file name manipulation. By changing a .jpg file to .php and uploading it, the server executed the file, highlighting a lack of secure file handling. Exploiting this vulnerability unveiled the sixth flag.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/9a1b830b-d9c5-4cb9-9d6b-bb3272a57014)

### Flag 7: SQL Injection on 'Login' Page

A SQL Injection (SQLi) vulnerability was found on the 'Login' page. Using the username obtained from a directory traversal attack, I was able to inject SQL commands into the application's query. SQLi vulnerabilities occur when an application incorporates user-supplied data into SQL queries without proper validation or escaping, allowing an attacker to interact directly with the database. Successfully exploiting this vulnerability revealed the seventh flag.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/062f0fa3-7719-436f-98a5-1029c976d6ee)
![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/9199a5c4-15f3-4cd6-b7b0-434aac20b776)

### Flag 8: Sensitive Data Exposure on 'Login' Page

The eighth flag was discovered within the HTML source code of the 'Login' page, where the login credentials were mistakenly exposed. This is a classic case of sensitive data exposure where developers inadvertently leave sensitive data, such as credentials or API keys, within the client-side code.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/3e50f856-c9c1-4bfa-98fa-570b22b5bacb)

### Flag 9: Sensitive Data Exposure via 'Robots.txt'

I accessed the 'robots.txt' file, which often provides directives to web crawlers about which parts of the website should not be indexed. This file can sometimes inadvertently expose sensitive data or reveal the structure of the web application, as was the case here, allowing me to capture the ninth flag.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/78d1b5c4-d8cc-441a-9e2b-885b48de7330)

### Flag 10: Command Injection on 'Networking' Page

A command injection vulnerability was identified on the 'Networking' page. This type of vulnerability occurs when an application passes unsafe user-supplied data (forms, cookies, HTTP headers, etc.) to a system shell. I exploited this flaw by using the payload `www.example.com; cat vendors.txt`, which injected a command to display the content of the 'vendors.txt' file, revealing the tenth flag.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/9ea1790f-bb86-414f-95f6-4e353d474f6f)

### Flag 11: Advanced Command Injection on 'Networking' Page

Exploiting a further command injection vulnerability on the 'Networking' page, I used an advanced payload `www.example.com | cat vendors.txt` which not only returned the requested page but also outputted the contents of 'vendors.txt', resulting in the eleventh flag.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/4fc43b23-9a1d-4f1a-bce0-c4d6086cc173)

### Flag 12: Brute Force Attack on 'Login' Page

I conducted a brute force attack on the 'Login' page, utilising the Burp Intruder tool to automate the process. This form of attack systematically attempts all possible password combinations until the correct one is found. This method is highly effective when weak passwords are used, and in this case, it led to the discovery of the twelfth flag.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/fea02f16-4c3f-4abf-a1ee-192c1ce1bb24)

### Flag 13: PHP Injection on 'Souvenirs' Page

I exploited a PHP injection vulnerability on the 'Souvenirs' page by appending `;system(‘cat/etc/passwd’)` at the end of the URL. PHP Injection is a web vulnerability that lets the attacker create, alter, or delete queries that are being passed to the SQL database from a PHP script. The exploitation of this vulnerability revealed the thirteenth flag.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/60ed656a-512f-4007-ad49-b7e5dc212363)

### Flag 14: Session Management Vulnerability on 'admin_legal_data.php' Page

I exploited a session management vulnerability on the 'admin_legal_data.php' page to gain unauthorized access. Session management vulnerabilities arise when a web application mishandles user sessions, allowing an attacker to hijack user sessions or manipulate session data. I used the Burp Intruder tool to brute force session IDs, leading to the discovery of the fourteenth flag.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/d5d5c059-7d3e-42f1-93ba-7cb296ecb23e)

### Flag 15: Directory Traversal on 'disclaimer.php' Page

The fifteenth flag was achieved by exploiting a directory traversal vulnerability on the 'disclaimer.php' page. Directory traversal is a type of HTTP exploit which allows attackers to access restricted directories and execute commands outside of the web server's root directory. I navigated the contents of the directory due to a common injection exploit, which led to the exposure of the fifteenth and final flag.

![Image](https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/1432e64b-3f84-4cc6-bbc6-0e9b570574c3)


## Conclusion

This challenge has reinforced my understanding of various web application vulnerabilities and how they can be exploited in a real-world scenario. Through persistence, I was able to successfully capture all 15 flags and complete the CTF challenge. I'm eager to apply my expanded knowledge to future cybersecurity endeavors.

<img src="https://github.com/Lodoelama/Web-Application-CTF/assets/125059539/0a6dc05c-b2e9-4746-bf15-265d8718ed68" width="550" height="450">

