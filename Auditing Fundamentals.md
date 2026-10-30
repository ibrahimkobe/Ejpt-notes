
## I. Introduction to Security Auditing

**Security Auditing** is a systematic process of evaluating and verifying an organization's security measures and controls to ensure they are effective, appropriate, and compliant with relevant standards, policies, and regulations. This involves reviewing information systems, networks, applications, and procedures to identify vulnerabilities and areas for improvement.

### The Importance of Security Auditing

1. **Identifying Vulnerabilities and Weaknesses:** Uncovers vulnerabilities in systems and infrastructure that attackers could exploit, ensuring security controls remain effective and up-to-date.
    
2. **Ensuring Compliance:** Verifies adherence to standards such as GDPR, HIPAA, PCI DSS, and ISO 27001 to protect sensitive data and avoid legal and financial penalties.
    
3. **Enhancing Risk Management:** Provides a comprehensive assessment to identify and prioritize risks by their potential impact, allowing organizations to develop effective mitigation strategies.
    
4. **Improving Security Policies & Procedures:** Reviews the effectiveness of current policies to identify improvements and foster a strong security culture.
    
5. **Supporting Business Objectives:** Protects critical operations from disruptions and builds customer trust by ensuring data is handled securely.
    
6. **Continuous Improvement:** Acts as an ongoing process to ensure security measures evolve alongside new threats and vulnerabilities.
    

---

## II. Essential Terminology

Understanding standard vocabulary is critical for navigating security audits.

|**Term**|**Definition**|**Importance**|
|---|---|---|
|**Security Policies**|Formal documents defining an organization's security objectives, guidelines, and procedures.|Establishes the framework for implementing and enforcing controls.|
|**Compliance**|Adherence to regulatory requirements, industry standards, and internal policies.|Ensures the organization meets legal obligations and best practices.|
|**Vulnerability**|A weakness in a system or process exploitable for unauthorized access or harm.|Identifying these is crucial for assessing and improving security.|
|**Control**|A safeguard or countermeasure to mitigate risks and protect assets.|Designed to prevent, detect, or respond to security threats.|
|**Risk Assessment**|The process of identifying, analyzing, and evaluating risks to information assets.|Helps prioritize measures based on risk likelihood and impact.|
|**Audit Trail**|A chronological record of events providing evidence of actions within a system.|Supports accountability and traceability during audits and investigations.|
|**Compliance Audit**|Examination of adherence to regulatory requirements and standards.|Validates if compliance criteria are met and identifies gaps.|
|**Access Control**|Mechanisms used to regulate who can access information/systems and what they can do.|Protects sensitive information from unauthorized access.|
|**Audit Report**|A formal document presenting findings, conclusions, and recommendations from an audit.|Communicates results and provides guidance for improvement.|

---

## III. The Security Auditing Lifecycle

The security auditing process generally follows a structured methodology, often represented in a five-phase lifecycle (Planning, Information Gathering, Risk Assessment & Execution, Analysis/Reporting, and Remediation). This process expands into seven detailed steps:

1. **Planning and Preparation:** Determine audit goals, scope, and specific systems to evaluate. Gather documentation (policies, network diagrams) and establish the team and timeline.
    
2. **Information Gathering:** Review security policies and standards, conduct interviews to find potential gaps, and collect technical data on system configurations and network architecture.
    
3. **Risk Assessment:** List critical assets and potential threats. Evaluate existing vulnerabilities and assign risk levels based on likelihood and impact.
    
4. **Audit Execution:** Conduct technical testing (vulnerability scans, penetration tests). Verify regulatory compliance and evaluate the effectiveness of security controls.
    
5. **Analysis and Evaluation:** Review collected data to identify weaknesses. Measure security posture against industry standards and prioritize issues based on severity.
    
6. **Reporting:** Create a detailed document outlining vulnerabilities, non-compliance issues, and ineffective controls. Offer actionable recommendations and present findings to stakeholders.
    
7. **Remediation:** Work with the organization to develop and implement plans addressing the findings. Schedule follow-up audits to ensure effectiveness and continuously monitor the security posture.
    

---

## IV. Types of Security Audits

Security audits are categorized by their scope, methodology, and focus.

|**Audit Type**|**Objective**|
|---|---|
|**Internal Audits**|Conducted by the internal team to evaluate the effectiveness of internal controls and policy compliance.|
|**External Audits**|Performed by independent third parties to provide an unbiased evaluation of security and compliance.|
|**Compliance Audits**|Focus on verifying adherence to specific regulatory requirements like GDPR, HIPAA, or PCI DSS.|
|**Technical Audits**|Assess technical aspects of IT infrastructure, including hardware, software, and configurations.|
|**Network Audits**|Assess network infrastructure security, including routers, switches, and firewalls.|
|**Application Audits**|Evaluate software security, focusing on code quality, input validation, and data handling.|

---

## V. Security Auditing vs. Penetration Testing

While audits and penetration tests are separate assessments, understanding how they relate is crucial for a penetration tester.

- **Security Audit:** Evaluates the overall security posture against policies and regulations. It relies heavily on reviewing documentation, interviews, and technical assessments to identify compliance gaps, and is often performed regularly.
    
- **Penetration Test:** Simulates real-world attacks to identify and exploit technical weaknesses. It utilizes specific tools to attempt system breaches and is usually performed as needed (e.g., after significant system changes).
    

### Approaches to Integration

1. **Sequential Approach:** A security audit is performed first to evaluate posture and compliance. Based on the audit's findings, a penetration test is subsequently conducted to assess technical controls and identify vulnerabilities. This provides a comprehensive view and helps prioritize remediation.
    
2. **Combined Approach:** Integrates both into a single holistic assessment. This approach streamlines the process, provides a complete security picture, and can be more efficient and cost-effective.
    

---

## VI. Governance, Risk & Compliance (GRC)

GRC is a comprehensive framework organizations use to manage and align governance practices, risk management, and regulatory compliance.

- **Governance:** The framework of policies and procedures ensuring an organization meets its objectives and complies with laws. Components include policy development, defining roles, and establishing accountability.
    
- **Risk:** Identifying, assessing, and mitigating risks that could negatively impact operations. Components include risk identification, risk assessment, and risk mitigation.
    
- **Compliance:** Ensuring adherence to laws, regulations, and standards. Components include meeting regulatory requirements (e.g., GDPR), adhering to internal policies, and conducting audits.
    

---

## VII. Common Standards, Frameworks & Guidelines

- **Frameworks:** Structured, adaptable approaches to implementing security.
    
    - _NIST CSF:_ Guidelines for managing cybersecurity risk (Identify, Protect, Detect, Respond, Recover).
        
    - _COBIT:_ Framework for developing and monitoring IT governance, aligning IT with business goals.
        
- **Standards:** Specific, often mandatory requirements needed to achieve compliance.
    
    - _ISO/IEC 27001:_ International standard for information security management systems (ISMS).
        
    - _PCI DSS:_ Protects payment card data and secures transaction processing.
        
    - _HIPAA:_ U.S. law setting standards for protecting sensitive patient health information.
        
    - _GDPR:_ EU regulation governing data protection and privacy.
        
- **Guidelines:** Recommended best practices.
    
    - _CIS Controls:_ Actionable steps and foundational controls to improve cybersecurity posture.
        
    - _NIST SP 800-53:_ Catalog of security and privacy controls for federal information systems.
        

---

## VIII. Practical Example: From Audit to Pentest

This course section uses a fictional company, "SecureTech Solutions," to demonstrate the workflow from policy creation to penetration testing on Linux servers.

### Phase 1: Develop a Security Policy

Establish a baseline policy for Linux servers aligned with NIST SP 800-53.

|**Policy Area**|**Control ID**|**Policy Statement**|
|---|---|---|
|**Access Control (AC)**|AC-2, AC-5|Only authorized personnel granted access; unique accounts required; inactive accounts disabled within 30 days.|
|**Identification & Auth**|IA-2, IA-5|Strong passwords (12 chars min); use SSH keys where possible; implement 2FA for privileged accounts.|
|**Audit & Accountability**|AU-2, AU-3|Enable logging (rsyslog/journald).|
|**Log Review**|AU-6, AU-7|Regularly review logs; retain for at least 90 days.|
|**Config Management**|CM-2, 3, 5|Maintain secure baseline using tools (Ansible, Puppet); apply security patches within 30 days.|
|**System Integrity (SI)**|SI-3, SI-4|Implement malware protection; monitor systems using tools like Lynis.|
|**Maintenance (MA)**|MA-2, MA-3|Perform controlled maintenance using approved, secure tools.|

### Phase 2: Security Auditing With Lynis

- **Execution:** Install and run a Lynis audit scan on the target Linux server, then analyze the report for security issues.
    
- **Remediation:** Address the findings (e.g., update software, enforce password policies), document the actions, and update the security policy accordingly.
    

### Phase 3: Conduct Penetration Test

- **Execution:** Perform network scanning (Nmap), vulnerability scanning (Metasploit), and web application testing (Burp Suite) to validate remediation efforts.
    
- **Validation:** Compare the penetration test results against the initial audit findings to verify vulnerabilities are addressed, and check for new vulnerabilities introduced during remediation.
    
- **Reporting:** Output an executive summary, methodology, findings (with severity and impact), and recommendations for further securing the system.

---
# الخطوة 1: تثبيت Lynis

يتم تثبيت الأداة على السيرفر.

مثال:

```bash
apt install lynis
```

أو تحميلها من المصدر.

---

# الخطوة 2: تشغيل الفحص

الأمر الأساسي هو:

```bash
./lynis audit system
```

مثال كامل:

```bash
root@localhost:/opt/lynis# ./lynis audit system
```

### ماذا يفعل؟

يقوم بفحص:

- إعدادات النظام
    
- المستخدمين
    
- الشبكة
    
- الجدار الناري
    
- الخدمات
    
- التحديثات
    
- إعدادات SSH
    
- إعدادات كلمات المرور
    

---

# مثال نتائج Lynis

النتيجة قد تكون مثل:

```
Warning: SSH root login allowed
Suggestion: Install intrusion detection tools
Warning: Outdated packages found
```

أي أنه يعطي:

- **Warnings**
- **Suggestions**
- **Hardening Index**


مثلاً:

```
Hardening index : 62
```

كلما زاد الرقم كان النظام أكثر أماناً.

---

# الخطوة 3: مراجعة التقرير

التقرير يوجد عادة في:

```
/var/log/lynis.log
```

و

```
/var/log/lynis-report.dat
```

من خلال التقرير يتم معرفة:

- نقاط الضعف
    
- الإعدادات غير الآمنة
    
- التحسينات المطلوبة
    

---

# الخطوة 4: Remediation (إصلاح المشاكل)

بعد قراءة التقرير يتم إصلاح المشاكل مثل:

### تحديث النظام

```
apt update
apt upgrade
```

### تحسين كلمات المرور

تعديل ملف:

```
/etc/login.defs
```

أو

```
/etc/pam.d/common-password
```

---

### تعطيل SSH root login

تعديل:

```
/etc/ssh/sshd_config
```

وتغيير:

```
PermitRootLogin no
```

---

### تثبيت أدوات أمنية

مثل:

- IDS
    
- Rootkit detection
    

---

# تحديث Security Policy

بعد إصلاح المشاكل يجب:

- توثيق التغييرات
    
- تحديث السياسة الأمنية
    

مثال:

إضافة سياسة:

```
SSH root login must be disabled
```
---

# 1️⃣ الأمر الأساسي

```
./lynis audit system
```

المعنى:

تشغيل **فحص أمني كامل للنظام**.

يفحص:

- النظام
    
- الشبكة
    
- الخدمات
    
- إعدادات الأمان
    

---

# 2️⃣ تشغيل اختبار محدد

```
./lynis audit system --tests HRDN-7230
```

المعنى:

تشغيل **اختبار محدد فقط**.

HRDN = Hardening test

أي أنك لا تشغل الفحص الكامل بل اختبار واحد فقط.

مفيد عندما تريد:

- اختبار نقطة أمنية محددة
    
- إعادة فحص مشكلة تم إصلاحها
    

---

# 3️⃣ تحديد اسم المدقق

```
./lynis audit system --auditor "Alexis"
```

المعنى:

تحديد اسم الشخص الذي قام بالتدقيق.

يظهر في التقرير:

```
Auditor : Alexis
```

مفيد في:

- الشركات
    
- التقارير الرسمية
    
- الامتثال
    

---

# 4️⃣ تشغيل الفحص بدون مخرجات كثيرة

```
./lynis audit system --quiet --auditor "Alexis"
```

المعنى:

- `--quiet` يقلل الرسائل على الشاشة
    
- يعطي فقط النتائج المهمة
    

مفيد عندما:

- تشغل الأداة داخل script
    
- تريد تقارير نظيفة
    

---

# 5️⃣ تحديث النظام

```
sudo apt-get update
```

المعنى:

تحديث قائمة الحزم في النظام.

لكن **لا يقوم بتحديث البرامج** بل فقط يجلب معلومات الإصدارات الجديدة.

---
# 6️⃣ تثبيت أداة Rootkit detection

```
sudo apt-get install rkhunter -y
```

هذه الأداة هي:

Rootkit Hunter

وظيفتها:

- اكتشاف Rootkits
    
- اكتشاف Backdoors
    
- اكتشاف ملفات النظام المعدلة
    

---
# لماذا يقترح Lynis تثبيت rkhunte
لأنها تساعد في:
- كشف الاختراقات
- اكتشاف البرمجيات الخبيثة
- تحسين مستوى الأمان
---

###### Phase 3 - Conduct Penetration Test
بعد أن قمنا بـ:

1️⃣ إنشاء **Security Policy**  
2️⃣ إجراء **Security Audit باستخدام Lynis**  
3️⃣ إصلاح المشاكل (Remediation)

نقوم الآن بـ **Penetration Test** للتأكد أن:

- الثغرات تم إصلاحها فعلاً
    
- السيرفر أصبح أكثر أماناً
    
- النظام يلتزم بالسياسة الأمنية
    

---

# 1️⃣ Execution (تنفيذ اختبار الاختراق)

في هذه المرحلة يتم اختبار السيرفر باستخدام أدوات مختلفة.

---

## فحص الشبكة

يتم استخدام أداة:

Nmap

لمعرفة:

- البورتات المفتوحة
    
- الخدمات
    
- إصدارات البرامج
    

مثال:

```bash
nmap -sV 178.79.173.229
```

النتيجة قد تكون مثل:

```
22/tcp open ssh OpenSSH 8.2
80/tcp open http Apache
```

هذا يساعد في معرفة **سطح الهجوم (Attack Surface)**.

---

## فحص الثغرات

يتم استخدام:

Metasploit Framework

لـ:

- اكتشاف الثغرات
    
- محاولة استغلالها
    

مثلاً:

- استغلال ثغرة SSH
    
- استغلال خدمة Web
    

---

## اختبار تطبيقات الويب

إذا كان السيرفر يحتوي على موقع.

يتم استخدام:

Burp Suite

لفحص:

- SQL Injection
    
- XSS
    
- Authentication problems
    

---

# 2️⃣ التحقق من الإصلاحات (Validating Remediation)

بعد إجراء اختبار الاختراق يتم:

### مقارنة النتائج

نقارن بين:

- نتائج **Security Audit السابقة**
    
- نتائج **Penetration Test**
    

إذا كانت الثغرة موجودة سابقاً وتم إصلاحها  
فهذا يعني أن **الإصلاح نجح**.

---

### اكتشاف ثغرات جديدة

أحياناً الإصلاحات قد تسبب مشاكل أخرى.

مثلاً:

- تغيير إعدادات SSH
    
- تثبيت برامج جديدة
    

قد ينتج عنها ثغرات جديدة يجب إصلاحها.

---

# 3️⃣ إعداد التقرير (Reporting)

في النهاية يتم كتابة **تقرير اختبار الاختراق**.

---

## Executive Summary

ملخص بسيط للإدارة يحتوي على:

- هل النظام آمن أم لا
    
- أهم الثغرات المكتشفة
    

---

## Methodology

شرح:

- الأدوات المستخدمة
    
- طريقة الاختبار
    

مثلاً:

- Nmap
    
- Metasploit
    
- Burp Suite
    

---

## Findings

وصف الثغرات مثل:

- نوع الثغرة
    
- درجة الخطورة
    
- تأثيرها
    

مثال:

```
Weak SSH password detected
Severity: High
Impact: Unauthorized access to server
```

---

## Recommendations

اقتراحات لتحسين الأمان مثل:

- تغيير كلمات المرور
    
- تحديث النظام
    
- تفعيل جدار ناري
    

---

# الآن شرح الأمر الذي ذكرته

## هجوم brute force على SSH

الأمر:

```bash
hydra -l root -P /usr/share/seclists/Passwords/xato-net-10-million-passwords.txt ssh://178.79.173.229:22 -t 2 -V
```

الأداة المستخدمة هي:

THC Hydra

---

## شرح الأمر

### تحديد المستخدم

```
-l root
```

محاولة تسجيل الدخول باستخدام المستخدم:

```
root
```

---

### تحديد قائمة كلمات المرور

```
-P /usr/share/seclists/Passwords/xato-net-10-million-passwords.txt
```

استخدام wordlist تحتوي على **ملايين كلمات المرور**.

القائمة مأخوذة من مشروع:

SecLists

---

### تحديد الخدمة

```
ssh://178.79.173.229:22
```

الهجوم على:

- بروتوكول SSH
    
- البورت 22
    

---

### عدد الاتصالات المتوازية

```
-t 2
```

يعني:

2 محاولات تسجيل دخول في نفس الوقت.

---

### إظهار المحاولات

```
-V
```

يعرض:

كل محاولة كلمة مرور أثناء الهجوم.

---

# الهدف من الهجوم

التحقق من:

هل كلمة مرور SSH ضعيفة أم لا.

إذا نجح الهجوم فهذا يعني:

❌ سياسة كلمات المرور غير قوية  
❌ السيرفر غير آمن

---

# الحماية من هذا الهجوم

يمكن استخدام أداة:

Fail2Ban

لتمنع brute force.

---

## تثبيت Fail2Ban

الأمر:

```bash
sudo apt-get install fail2ban
```

وظيفته:

- مراقبة محاولات تسجيل الدخول
    
- إذا فشل الدخول عدة مرات يقوم بـ:
    

✔ حظر عنوان IP

مثلاً:

```
5 failed login attempts → block attacker
```

---

# مثال

إذا حاول المهاجم:

```
10 SSH login attempts
```

سيقوم Fail2Ban بـ:

```
Block IP for 10 minutes
```


---
