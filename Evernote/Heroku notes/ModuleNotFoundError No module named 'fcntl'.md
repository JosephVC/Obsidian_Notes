---
---
The 'fcntl' module is apparently not supported under Windows :(

Trying to get the variables in my .env file recognized by Heroku, but encountered the following issue:

![[./_resources/ModuleNotFoundError_No_module_named_'fcntl'.resources/unknown_filename.png]]

The solution was to 

1. switch from **python-decouple** to **python-dotenv**
2. start up **WSL** to get around the 'fcntl' issue
3. start up your poetry shell within WSL
4. run **'heroku local**' to allow Heroku to see the values in the .env file
5. See the following:
	1. ![[./_resources/ModuleNotFoundError_No_module_named_'fcntl'.resources/unknown_filename.1.png]]
6. Quit the above and get out of WSL
7. Update your **requirements.txt** with the new dependency and push to github
8. **deploy** your updated repo to Heroku
9. You should be good to go :)
