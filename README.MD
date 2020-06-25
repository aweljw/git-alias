## git alias

```
pr  = "!f() { git fetch -fu ${2:-$(git remote |grep ^upstream || echo origin)} refs/pull/$1/head:pr/$1 && git checkout pr/$1; }; f"
pr-clean = "!git for-each-ref refs/heads/pr/* --format='%(refname)' | while read ref ; do branch=${ref#refs/heads/} ; git branch -D $branch ; done"
l = "log \
    --color --graph --decorate \
    --date=format:'%Y-%m-%d' \
    --abbrev-commit \
    --pretty=format:'%C(red)%h%C(auto)%d %s %C(green)(%cr)%C(bold blue) %an'"
ll = "log \
    --color --graph --decorate \
    --date=format:'%Y-%m-%d' \
    --abbrev-commit \
    --pretty=format:'%C(red)%H%C(auto)%d %s %C(green)(%cr)%C(bold blue) %an'"
lh = "!# Show log graph | head \n\
    f() { \
        if [ $# = 0 ]; then \
            git l | head -25; \
        else \
            git l -$1; \
        fi; \
        echo ''; \
    }; f"
```