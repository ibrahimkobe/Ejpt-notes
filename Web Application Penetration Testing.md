### HTTP Method Enumeration

1. `ifconfig` , eth 1: 192.191.151.3
2. `wireshark -i eth1` , open wire shark from the terminal because form the desktop eth1 won't appear
3. `curl -v http://192.191.151.3/` , is used to make an HTTP request to a target server and display detailed information about the connection.
4. `curl -I http://192.191.151.3` , Tells `curl` to send an **HTTP HEAD request** instead of GET. The server responds with **headers only**, **no body (no HTML page)**.
- Burp suite:
1. open firefox then on the top right enable burp suite in foxy proxy
2. then open burp suite , open proxy tab and make intercept is on
3. reload the page
4. add the changes you want like: connection close change it to keep-alive , then press forward
- Repeater Module in burp suite (you can see the response immediatly)
1. right click on the raw area then click on send it to the repeater
2. if you want to see what is allowed on the website , you just put options in the first line in the raw tab instead of (get), you can use it to see if you can upload a malicious file
3. `curl http://192.191.151.3/uploads --upload-file /usr/share/webshells/php/simple-backdoor.php` , the file will be uploaded successfully
4. change options or get to delete , to delete files , `DELETE /uploads/simple-backdoor.php HTTP/1.1` and then send (in burp suite)
---
### Network & HTTP Basics

**Wireshark**

| Command             | English Explanation                                                                                                                 | Arabic Explanation                                                                                            |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `wireshark -i eth0` | Starts Wireshark and listens on interface eth0 to capture network packets, HTTP requests, DNS traffic, and unencrypted credentials. | يقوم بتشغيل البرنامج ويبدأ في التقاط البيانات من كرت الشبكة eth0 لرؤية حركة الشبكة، طلبات HTTP، ومعلومات DNS. |

**cURL (HTTP Requests)**

| Command                               | English Explanation                                                 | Arabic Explanation                                       |
| ------------------------------------- | ------------------------------------------------------------------- | -------------------------------------------------------- |
| `curl -v <url>`                       | Verbose mode; shows full request/response headers and status codes. | الخيار -v يظهر الهيدر المرسل والمستلم وكود الاستجابة.    |
| `curl -I <url>`                       | Sends a HEAD request; returns only headers, no page content.        | يرسل طلب HEAD فقط ويعرض Headers بدون تحميل الصفحة.       |
| `curl -x <proxy> <url>`               | Sends the request through a proxy server (e.g., Burp Suite).        | يرسل الطلب عبر Proxy للتحليل أو التعديل.                 |
| `curl -X POST <url>`                  | Sends a POST request instead of the default GET.                    | إرسال طلب POST بدل GET.                                  |
| `curl -d "user=admin&pass=123" <url>` | Sends data (like login credentials) with the request.               | إرسال بيانات تسجيل الدخول.                               |
| `curl -H "User-Agent: test" <url>`    | Adds or modifies an HTTP header.                                    | تغيير الهيدر مثل User-Agent.                             |
| `curl -o file.html <url>`             | Saves the page output to a file.                                    | حفظ الصفحة في ملف.                                       |
| `curl -L <url>`                       | Follows HTTP redirects automatically.                               | متابعة التحويلات (redirect).                             |
| `curl -k <url>`                       | Ignores SSL/TLS certificate errors.                                 | تجاهل أخطاء الشهادة.                                     |
| `curl <url> --upload-file <file>`     | Uses HTTP PUT method to upload a file (if allowed by server).       | يرفع ملف إلى الخادم باستخدام HTTP PUT (إذا كان مسموحاً). |

---

### Web Server Vulnerability Scanning

**Nikto**

|Command|English Explanation|Arabic Explanation|
|---|---|---|
|`nikto --help`|Displays all available Nikto options and parameters.|يعرض جميع أوامر Nikto وخيارات الفحص.|
|`nikto -h <url/ip>`|Performs a basic scan finding server versions and common vulnerabilities.|يفحص الموقع لاكتشاف إصدار الخادم والثغرات والملفات المهمة.|
|`nikto -h "<url>?page=test"`|Scans a dynamic page with parameters (useful for finding LFI).|يفحص صفحة تحتوي على باراميتر لاكتشاف ثغرات مثل LFI.|
|`nikto -h <url> -Tuning 9`|Controls the type of tests run (e.g., 9 means all tests).|يحدد نوع الفحص (رقم 9 يعني فحص شامل لكل شيء).|
|`nikto -h <url> -o nikto.html`|Saves scan results into a file.|حفظ نتائج الفحص في ملف.|
|`nikto -h <url> -Format html -o nikto.html`|Saves results specifically in HTML format.|حفظ النتائج بصيغة HTML لعرضها في المتصفح.|

---

### Directory & Content Discovery

**DIRB**

|Command|English Explanation|Arabic Explanation|
|---|---|---|
|`dirb <url>`|Basic scan using the default wordlist (`common.txt`).|يستخدم قائمة كلمات افتراضية للبحث عن مجلدات وملفات مخفية.|
|`dirb <url> /path/wordlist.txt`|Uses a custom wordlist for the scan.|استخدام قائمة كلمات مخصصة.|
|`dirb <url> -X .php,.html`|Searches only for specific file extensions.|يبحث عن ملفات بامتدادات محددة مثل php أو html.|
|`dirb <url> -N 404`|Ignores specific HTTP response codes (like 404).|يتجاهل الصفحات غير الموجودة.|
|`dirb <url> -q`|Quiet mode; shows only found results without extra details.|يعرض النتائج المهمة فقط بدون تفاصيل.|
|`dirb <url> -t 20`|Sets the number of threads to increase scan speed.|تحديد عدد العمليات لزيادة السرعة.|
|`dirb <url> -p <proxy>`|Sends DIRB requests through a proxy (like Burp Suite).|يرسل الطلبات عبر Burp Suite لتحليلها.|
|`dirb <url> -o result.txt`|Saves the output to a text file.|حفظ النتائج في ملف.|

**Gobuster**

|Command|English Explanation|Arabic Explanation|
|---|---|---|
|`gobuster dir -u <url> -w <wordlist>`|Basic directory and file brute-force mode.|وضع البحث الأساسي عن المجلدات والملفات باستخدام قائمة كلمات.|
|`gobuster vhost -u <url> -w <wordlist>`|Virtual host enumeration (finds hidden subdomains on same IP).|اكتشاف المواقع المختلفة المستضافة على نفس السيرفر.|
|`gobuster dns -d <domain> -w <wordlist>`|DNS subdomain enumeration.|اكتشاف النطاقات الفرعية عن طريق خوادم DNS.|
|`-b 404,403` _(Flag)_|Ignores specific status codes to hide unwanted responses.|يتجاهل نتائج معينة مثل 404 (غير موجود) و 403 (ممنوع).|
|`-x .php,.txt` _(Flag)_|Searches for files with specific extensions.|يبحث عن ملفات بامتدادات معينة.|
|`-r` _(Flag)_|Follows HTTP redirects (301, 302).|يتبع التحويلات في الموقع.|
|`-t 50` _(Flag)_|Controls scan speed (threads).|زيادة سرعة الفحص.|
|`-e` _(Flag)_|Shows full URLs in the output.|عرض الرابط كامل في النتائج.|

---

### CMS & WordPress Security Testing

**WPScan**

|Command|English Explanation|Arabic Explanation|
|---|---|---|
|`wpscan --url <target url>`|Basic scan; checks if the site is WordPress and gathers general info/version.|يتأكد من عمل الموقع على ووردبريس ويجمع معلومات عامة وإصدار النظام.|
|`wpscan --url <target url> -eu`|Enumerates users; tries to discover valid usernames on the site.|تعداد المستخدمين لاكتشاف أسماء الحسابات الظاهرة في الموقع.|
|`wpscan --url <target url> -U <user> -P <wordlist>`|Brute-forces a specific username against a password list (e.g., rockyou.txt).|تجربة كلمات مرور كثيرة على حساب معروف (مسموح فقط في بيئة تدريبية).|

---
### 🌟 High-Yield Exam Tips & Indicators

These are the specific things your notes emphasized looking out for during a pentest or lab:

- **HTTP Methods:** If you find the **PUT** method enabled (by changing `GET` to `OPTIONS` in Burp Suite), or you find an `/uploads/` directory, immediately check for a **file upload vulnerability**.
    
- **LFI (Local File Inclusion):** If Nikto or Gobuster finds a dynamic parameter like `?page=`, try changing it to `?page=../../etc/passwd`. This is a strong indicator of an LFI vulnerability.
    
- **Sensitive Directories/Files:** Always keep an eye out for these in your Gobuster/DIRB results:
    
    - `/admin` (Admin panels)
        
    - `/backup` or `/backup.zip` (Download and extract these immediately!)
        
    - `/config` or `config.php` (May contain database credentials)
        
    - `.git` or `.env` (Source code and environment variables/API keys)
        
- **ETag Headers:** Look at ETags in HTTP responses. They can be used to track users, leak server configuration info, or be used in cache poisoning.
    

---

### 🗺️ Standard Penetration Testing Workflows

Your notes highlighted specific step-by-step processes for tackling labs:

**General Web Pentest Flow:**

1. **Nmap:** Find the web server (e.g., port 80/443 open).
    
2. **Nikto:** Run a vulnerability scan to find outdated software or low-hanging fruit.
    
3. **DIRB / Gobuster:** Find hidden paths, directories, and files.
    
4. **Burp Suite / curl:** Intercept traffic, modify headers, test file uploads, and manually exploit.
    

**WordPress Pentest Flow:**

1. **Identify:** Use Wappalyzer to confirm the site is running WordPress.
    
2. **Enumerate:** Run `wpscan` to find the WordPress version, installed plugins, and themes.
    
3. **Users:** Run `wpscan -eu` to extract valid usernames.
    
4. **Exploit:** Search for known vulnerabilities for those specific plugins/versions, or perform a brute-force attack on the login page (`/wp-login.php`) if authorized.
    

---

### 🛠️ GUI Tools & Concepts (No Commands Needed)

**Burp Suite vs. OWASP ZAP**

- **Burp Suite:** Used primarily for intercepting and modifying requests (like changing `GET` to `OPTIONS`). It has a **Live Scan** feature with three modes: _Crawl_ (maps the site), _Audit_ (finds vulnerabilities), and _Crawl + Audit_ (full scan).
    
- **OWASP ZAP:** Features a powerful automated **Spider** tool. It operates in four modes: _Safe_ (no attacks), _Protected_ (limited), _Standard_ (normal), and _Attack_ (aggressive).
    

**Crawling vs. Spidering**

- **Crawling:** Passive and limited depth. It acts like a normal user clicking visible links to map the website structure.
    
- **Spidering:** Active, automated, and deep. It aggressively follows all links, discovers hidden pages, and tests parameters. It is much "louder" and easier for defenders to detect.
    

**Wappalyzer (Browser Extension)** Used for passive reconnaissance to identify technologies without sending aggressive traffic. It reveals:

- **CMS:** WordPress, Drupal, Joomla.
    
- **Web Servers:** Apache, Nginx.
    
- **Frameworks & Languages:** PHP, React, jQuery (great for finding outdated versions!).
    

**HTTPS (HTTP + SSL/TLS)**

- Operates over **TCP** to ensure reliable delivery.
    
- Provides the Security Triad: **Confidentiality** (encryption prevents eavesdropping), **Integrity** (prevents data modification in transit), and **Authentication** (validates server identity via certificates).
    

---
