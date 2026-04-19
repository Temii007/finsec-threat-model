# 🔐 FinSec Mobile Banking Threat Model

## 📌 Introduction
Threat modeling is the process of systematically analyzing a system by thinking like an attacker to identify potential security threats, vulnerabilities, and attack vectors. It enables organizations to proactively design controls that protect sensitive data, financial transactions, and system integrity.

The FinSec application under consideration is a **mobile banking transfer application** that allows users to:

- Authenticate (sign-in)
- View account balances
- Perform airtime purchases
- Conduct internet banking operations
- Transfer funds between accounts

### 🎯 Security Objectives
- Confidentiality  
- Integrity  
- Availability  
- Non-repudiation  

---

## 📦 Scope

This threat model focuses on:

- Mobile banking application (user interface)
- Authentication and login system
- Funds transfer functionality
- Backend APIs and microservices
- Core banking database
- External third-party integrations (OTP, payment gateway)

---

## 🏗️ System Architecture & Data Flow

### 🔹 High-Level Architecture

Mobile App → API Gateway → Authentication Service → Business Services → Databases → External Services


### 🖼️ Architecture Diagram
![Architecture](architecture.png)

### 🔹 Key Components

- **Client Layer:** Mobile banking app  
- **Edge Layer:** API Gateway  
- **Security Layer:** Authentication Service  
- **Business Layer:** Transfer Service, Account Service  
- **Data Layer:** Core Banking Database, Application Database  
- **External Layer:** SMS/OTP service, Payment Gateway  

### 🔹 Trust Boundaries

- 🌐 Public Internet Boundary (Untrusted → Trusted)  
- 🏦 Internal Bank Network (Trusted zone)  
- 🔌 External Third-Party Services (Semi-trusted)  

> Each boundary represents a potential attack surface.

---

## 💰 Assets

- **Customer Funds**  
  Monetary balances stored in user accounts  

- **Authentication Credentials**  
  Usernames, passwords, PINs, biometrics  

- **Authentication Tokens**  
  Session tokens, JWTs, API keys  

- **Transaction Records**  
  Logs of all financial operations  

- **Personally Identifiable Information (PII)**  
  BVN, National ID, name, DOB, contact details  

- **Audit Logs**  
  Records of system and user activity  

---

## 👥 System Actors

### ✅ Legitimate Actors
- Customers  
- Bank administrators  
- Backend services  
- Payment providers  

### ⚠️ Threat Actors
- External attackers (hackers)  
- Fraudsters  
- Insider employees  
- Malware operators  

---

## ⚠️ Threat Identification (STRIDE)

### 📱 Mobile Application
- Spoofing: Fake or cloned apps  
- Tampering: Reverse engineering  
- Information Disclosure: Insecure storage  

### 🌐 API Gateway
- Denial of Service: Traffic flooding  
- Spoofing: Unauthorized API access  
- Tampering: Injection attacks  

### 🔑 Authentication Service
- Spoofing: Credential theft  
- Elevation of Privilege: Unauthorized access  
- Information Disclosure: Token leakage  

### 💸 Transfer Service (Critical)
- Tampering: Transaction manipulation  
- Repudiation: Denial of transactions  
- Elevation of Privilege: Unauthorized transfers  

### 👤 Account Service
- Information Disclosure: Data exposure  
- Tampering: Unauthorized modification  

### 🗄️ Core Banking Database
- Information Disclosure: Data breaches  
- Tampering: Unauthorized changes  
- Denial of Service: Unavailability  

### 🔌 External Services
- Spoofing: Fake endpoints  
- Information Disclosure: API leaks  
- Tampering: Manipulated responses  

---

## 🚨 Attack Scenarios

### 1. Account Takeover
- Phishing → credential theft  
- Login → unauthorized access  
- Transfer → financial fraud  

### 2. API Exploitation
- Direct API calls  
- Bypass frontend controls  
- Exploit weak authorization  

### 3. Insider Threat
- Internal access misuse  
- Data or transaction manipulation  
- Log tampering  

---

## 📊 Risk Assessment

| Component              | Risk Level | Reason                     |
|-----------------------|-----------|----------------------------|
| Authentication Service| High      | Entry point                |
| Transfer Service      | Critical  | Financial impact           |
| API Gateway           | High      | Internet-facing            |
| Database              | Critical  | Sensitive data storage     |

### 🔥 Highest Priority Risks
- Unauthorized access  
- Fraudulent transactions  
- Data breaches  

---

## 🛡️ Security Controls

### ✅ Preventive
- Multi-Factor Authentication (MFA)  
- Encryption (TLS & at rest)  
- Secure coding practices  
- API rate limiting  

### 🔍 Detective
- Logging and monitoring  
- Fraud detection systems  
- SIEM integration  

### 🔄 Corrective
- Incident response plan  
- Account lock/freeze mechanisms  
- Backup and recovery  

---

## ✅ Conclusion

This threat model identifies critical assets, system components, and potential threats within a mobile banking application. By applying STRIDE methodology, key vulnerabilities are identified and mitigated through layered security controls.

The most critical risks involve authentication and financial transactions, as compromise in these areas directly impacts customer funds and trust.

---

## 📚 Key Learnings

- Understanding trust boundaries  
- Applying STRIDE in real systems  
- Identifying financial attack vectors  