
https://stackoverflow.com/questions/68775869/message-support-for-password-authentication-was-removed

## For a Linux-based OS [⤴](https://git-scm.com/docs/git-credential-cache)

For Linux, you need to configure the local GIT client with a username and email address,

```
$ git config --global user.name "your_github_username"
$ git config --global user.email "your_github_email"
$ git config -l
```

Once GIT is configured, we can begin using it to access GitHub. Example:

```
$ git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
> Cloning into `YOUR-REPOSITORY`...
Username: <type your username>
Password: <type your password or personal access token (GitHub)
```

Now cache the given record in your computer to remembers the token:

```
$ git config --global credential.helper cache
```

If needed, anytime you can delete the cache record by:

```
$ git config --global --unset credential.helper
$ git config --system --unset credential.helper
```


**TO SAVE THE CREDENTIAL SO YOU NO LONGER NEED TO ENTER IT EVERY TIME**

## Developer's hack (shortcode):

```
git remote set-url origin https://<githubtoken>@github.com/<username>/<repositoryname>.git
```