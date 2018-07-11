---
description: common git configuration
---

# config

{% hint style="info" %}
 .gitconfig could be found under C:\Users\{User} \(Windows\)
{% endhint %}

## alias

```text
[alias]
    aa = add --all
    bv = branch -vv
    ba = branch -ra
    bd = branch -d
    ca = commit --amend
    cb = checkout -b
    ca = commit -a --amend -C HEAD
    ci = commit -a -v
	cm = commit -a -m
    co = checkout
    di = diff
    ll = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --numstat
    ld = log --pretty=format:"%C(yellow)%h\\ %C(green)%ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=short --graph
    ls = log --pretty=format:"%C(green)%h\\ %C(yellow)[%ad]%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=relative
    mm = merge --no-ff
    st = status --short --branch
    tg = tag -a 
	pu = push --set-upstream
    pt = push --tags
	p = push
    un = reset --hard HEAD  
    uh = reset --hard HEAD^
```



