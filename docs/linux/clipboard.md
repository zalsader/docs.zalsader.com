---
title: "Pipe to clipboard"
---

To pipe to system clipboard, use `xclip`.

```console
echo "Hello World!" | xclip -sel clip
xclip -sel clip | cat
```

I use it so much I added an alias for it:
```bash
alias clip="xclip -sel clip"
```
