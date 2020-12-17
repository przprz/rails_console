### Convert presentation from markdown to PDF:

```
  npm install -g @marp-team/marp-cli # install marp
```

```
  marp --allow-local-files --pdf rails_console.md # convert to pdf
```

### Work with pre-commit hooks

```
#!/bin/sh
# .git/hooks/pre-commit

touch .commit
exit
```

```
#!/bin/sh
# .git/hooks/post-commit

if [ -e .commit ]; then
    echo post-commit
    rm .commit
    marp --allow-local-files --pdf rails_console.md
    git add .
    git commit --amend -C HEAD --no-verify
fi
exit
```