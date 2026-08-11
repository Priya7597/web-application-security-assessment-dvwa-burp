# Web Application Security Assessment using DVWA & Burp Suite

## Overview

This project demonstrates a manual web application security assessment performed against DVWA (Damn Vulnerable Web Application) using Burp Suite Community Edition in a Kali Linux lab environment.

The objective was to intercept HTTP requests, analyze request/response behavior, manipulate application parameters, and validate SQL Injection vulnerabilities using Burp Repeater.

## Lab Environment

* Kali Linux
* DVWA (Apache / PHP / MySQL)
* Burp Suite Community Edition
* Firefox Browser

## Assessment Workflow

1. Configured Burp Suite Proxy and Firefox for HTTP interception.
2. Captured requests sent to the DVWA SQL Injection module.
3. Sent requests to Burp Repeater for manual testing.
4. Modified the `id` parameter to test SQL Injection behavior.
5. Compared server responses to identify vulnerability indicators.
6. Documented findings and evidence.

## SQL Injection Testing

### Baseline Request

A normal request using `id=1` returned a single valid user record.

### Malformed Input Test

Payload:

`1'`

Result:

* HTTP 500 Internal Server Error
* Indicates that unsanitized input reached the backend SQL query and caused a server-side failure.

### Boolean-based SQL Injection

Payload:

`1' OR '1'='1`

Result:

* Returned multiple user records
* Demonstrated successful SQL Injection through parameter manipulation.

### UNION-based SQL Injection

Payload:

`1' UNION SELECT user,password FROM users#`

Result:

* Extracted usernames and password hashes from the backend database
* Demonstrated data retrieval through UNION-based SQL Injection.

## Evidence

The repository includes:

* Burp Proxy interception screenshots
* Burp Repeater screenshots
* SQL Injection test evidence
* Raw repeater request used during assessment
* Assessment report

## Skills Demonstrated

* HTTP request interception
* HTTP response analysis
* Burp Suite Proxy
* Burp Repeater
* Parameter tampering
* SQL Injection validation
* OWASP Top 10 awareness
* Manual web application penetration testing
