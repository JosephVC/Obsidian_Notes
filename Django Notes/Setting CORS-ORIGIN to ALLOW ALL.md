---
source: https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/Errors/CORSMissingAllowOrigin?utm_source=devtools&utm_medium=firefox-cors-errors&utm_campaign=default
---
**Why you need to set CORS-ORIGIN\_ALLOW\_ALL**

If you see the error involving **Reason: CORS header 'Access-Control-Allow-Origin' missing** you likely need to go back to settings.py and create the **CORS-ORIGIN\_ALLOW\_ALL** variable and set it to **True** (at least while in production)

# NOTE: CORS was set to specify a whitelist, but this caused runserver to goof
# changing CORS to ALLOW\_ALL allows things to run
# This enables all API requests from a different server to be allowed.
