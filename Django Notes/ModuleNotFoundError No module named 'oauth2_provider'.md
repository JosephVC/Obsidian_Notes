---
---
1.15.21 - This error popped up when deploying to Heroku

1.18.21 - the reason is that the [needed package](https://github.com/wagnerdelima/drf-social-oauth2) was not installed, plus i was using old import names

* 'rest\_framework\_\[rest of import statement\]' needed to become 'drf\_\[rest of import statement\]'
