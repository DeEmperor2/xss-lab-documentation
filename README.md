# XSS Lab Documentation PortSwigger Web Security Academy

## Overview
Hand son cross site scripting labs completed on PortSwigger Web Security 
Academy. Covers all three major XSS vulnerability types using a live 
vulnerable application environment.

## Labs Completed

### Lab 1 Reflected XSS
- Platform: PortSwigger Web Security Academy
- Payload: <script>alert(1)</script>
- Injected via search parameter, reflected in server response
- Impact: Executes arbitrary JavaScript in victim's browser

### Lab 2 Stored XSS
- Platform: PortSwigger Web Security Academy  
- Payload: <script>alert(1)</script>
- Injected via comment field, stored in database permanently
- Impact: Every user visiting the page executes attacker's JavaScript

### Lab 3DOM-based XSS
- Platform: PortSwigger Web Security Academy
- Payload: "><svg onload=alert(1)>
- Injected via search parameter, processed by client-side JavaScript
- Impact: Browser executes payload without server ever seeing input

## Key Differences Between XSS Types

| Type | Where it lives | Who is affected | Severity |
| Reflected | Server response | Only victim who clicks link | Medium |
| Stored | Database | Every user who visits page | High |
| DOM-based | Client-side JS | Victim who clicks link | Medium-High |

## Real World Impact
XSS vulnerabilities can be used to:
- Steal session cookies and hijack accounts
- Redirect users to phishing pages
- Capture keystrokes and credentials
- Perform actions as the victim silently

## Tools Used
- PortSwigger Web Security Academy lab environment
- Browser DevTools inspecting DOM changes

## Defensive Recommendations
- Encode all user output HTML encode <, >, ", '
- Use Content Security Policy (CSP) headers
- Never use document.write() with user input
- Use safe JavaScript methods like textContent instead of innerHTML
- Validate and sanitise all input server-side
