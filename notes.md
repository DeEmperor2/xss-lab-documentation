# Lab Notes XSS

## Reflected XSS
- Payload fires immediately in the same request
- Server takes input and reflects it back unsanitised
- Attack requires victim to click a crafted URL
- Common in search boxes, error messages, URL parameters

## Stored XSS
- Payload saved permanently in database
- No malicious link needed victim just visits the page
- More dangerous than reflected because it's persistent
- Common in comment sections, user profiles, forum posts

## DOM-based XSS
- Vulnerability lives entirely in client side JavaScript
- Server never sees the payload bypass server side filters
- <script> tags don't work here need event based payloads
- svg onload, img onerror, iframe onload all work as alternatives
- Look for dangerous sinks: document.write(), innerHTML, eval()

## Payload Cheatsheet
# Basic
<script>alert(1)</script>

# When script tags are blocked
"><svg onload=alert(1)>
<img src=x onerror=alert(1)>
"><img src=x onerror=alert(1)>

# When inside an attribute
" onmouseover="alert(1)
' onmouseover='alert(1)

## Bug Bounty Notes
- alert(1) is proof of concept only never actual exploitation
- Stored XSS pays more than reflected on most programs
- DOM XSS is often overlooked by developers good hunting ground
- Always test comment fields, search boxes, profile fields, URL params
