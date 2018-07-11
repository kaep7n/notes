# commands

## clone

 clone a a remote repository to the default folder

```bash
$ git clone https://gitlab.adestis.net/m.hillermeier/Adestis.Services.CatalogService.git
```

clone a a remote repository to a specific folder

```bash
$ git clone https://gitlab.adestis.net/m.hillermeier/Adestis.Services.CatalogService.git Adestis.Services.CatalogService.mh
```

## remote

add remote

```bash
$ git remote add https://gitlab.adestis.net/adestis/Adestis.Services.CatalogService.git
```

add remote with specific name

```bash
$ git remote add adestis https://gitlab.adestis.net/adestis/Adestis.Services.CatalogService.git
```

## branches

Delete all merged branches except master

```bash
$ git branch --merged | egrep -v "(^\*|master)" | xargs git branch -d
```

## revert

revert specific commit

```bash
$ git revert 1ef414875a40eb5336ecb7f74da550af0d2f51dc
```

revert specific commit without creating a new commit

```bash
$ git revert 1ef414875a40eb5336ecb7f74da550af0d2f51dc --no-commit
```

