# 🎣 Elevate Labs Cyber Security Internship - Task 2

## 🎯 Task: Analyze a Phishing Email Sample

### 📝 Objective

The objective of this task is to identify phishing characteristics in a suspicious email sample by performing both visual and technical header analysis.

### 🛠️ Tools Used

Raw Phishing Email Sample (.eml format)

EML Analyzer: Online tool used for header extraction and threat scoring.

### 🕵️ Executive Summary

During this task, a suspicious email impersonating PayPal was analyzed. The email claimed the user's account was temporarily restricted. Technical analysis using an EML Analyzer confirmed a "Malicious" verdict. The email failed critical authentication checks (SPF and DMARC) and utilized domain spoofing alongside social engineering tactics to steal credentials.

### 🚩 Indicators of Compromise (IoCs)

Spoofed Sender: service@paypal.com

Actual Sender (Return-Path): bounces@paypal-update-alert.com

Malicious Target URL: http://www.paypal-update-alert.com/login

Originating IP (from headers): 198.51.100.23

### 🔍 Phase 1: Visual & Social Engineering Analysis

Based on the message content, several red flags were identified:

Sense of Urgency/Threat: The subject line "URGENT: Your account has been temporarily restricted" and the body text "permanently suspended within 24 hours" attempt to induce panic, forcing the victim to act quickly.

Suspicious Body Length: The email body is unusually short, which is a common trait in low-effort phishing campaigns.

Mismatched URLs: While the button says "Verify Identity Now," the underlying link directs the user to a low-reputation, non-PayPal domain (paypal-update-alert.com).

(See 3-email-content.jpg for visual proof)

### ⚙️ Phase 2: Technical Header Analysis

Extracting and analyzing the raw email headers revealed the true origin of the message. The high-trust sender domain (paypal.com) failed domain authentication:

SPF (Sender Policy Framework): FAIL - The originating IP address is not authorized by PayPal to send emails on their behalf.

DMARC (Domain-based Message Authentication, Reporting, and Conformance): FAIL - The message did not pass authentication alignment.

Mismatched Sender: The "From" address and the "Return-Path" address do not match, confirming email spoofing.

(See 1-analysis-summary.jpg and 2-technical-details.jpg for technical proof)
