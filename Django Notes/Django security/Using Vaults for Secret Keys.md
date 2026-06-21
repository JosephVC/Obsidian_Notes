---
---
If an attacker has access to your SECRET\_KEY, they can generate session data that the web app will trust, this session data being signed but not encrypted

environment variables are good, and something is better than nothing, a good alternative would be using a vault so the web app's particular secret keys are **only available at runtime**
