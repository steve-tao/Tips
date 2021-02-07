# Setting up Git

## View the current settings
```shell
git config --list --show-origin
```

## Setting identity

If we want to set the identify for only the current repository use ```--local```
instead of ```--global```.

```shell
$ git config [--global] user.name "John Doe"
$ git config [--global] user.email johndoe@example.com
```
