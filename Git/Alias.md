# Popular Alias

## Common shortcuts

```shell
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global alias.type 'cat-file -t'
git config --global alias.dump 'cat-file -p'
```

## Collection of git history in a series of one line

### Plain history
```shell
git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
```

### A pretty history
```shell
git config --global alias.hist "log --pretty=format:'%C(yellow)[%ad]%C(reset) %C(green)[%h]%C(reset) | %C(red)%s %C(bold red){{%an}}%C(reset) %C(blue)%d%C(reset)' --graph --date=short"
```

### A blend of the above two
```shell
git config --global alias.hist "log --pretty=format:'%h %ad | %C(red)%s%C(reset) %C(blue)%d%C(reset) [%an]' --graph --date=short"
```

## Manage output format
### Keep the output when exit from less
```shell
git config --global --replace-all core.pager "less -iXFR"
```

### Using cat instead of less for pager
```
git config --global core.pager cat
```
