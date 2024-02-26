---
title: "Aliases"
---

All my aliases could be found in [my chezmoi repository](https://github.com/zalsader/dotfiles/tree/main/dot_bashrc.d). Some notable examples:

## kubectl with completions
I use `kubectl` a lot, so I created an alias `k` for it. To enable completions, I used [complete-alias](https://github.com/cykerway/complete-alias).

```bash
alias watch='watch '
source ~/.bash_completion.d/complete_alias
alias k=kubectl
complete -F _complete_alias k
```

## Useful git commands
```bash
alias gfpush='git push --force'
alias grmain='git rebase main'

# Force pull
gpullf () { 
	git fetch --all && git reset --hard origin/$(git branch --show-current); 
}

# Prune merged branches from local repository
gprune () {
	MAIN=$(git remote show origin | sed -n '/HEAD branch/s/.*: //p')
	git checkout -q $MAIN && git for-each-ref refs/heads/ "--format=%(refname:short)" | while read branch; do mergeBase=$(git merge-base $MAIN $branch) && [[ $(git cherry $MAIN $(git commit-tree $(git rev-parse "$branch^{tree}") -p $mergeBase -m _)) == "-"* ]] && git branch -D $branch; done; git fetch -p
}
```

## Pipe to clipboard

To pipe to system clipboard, use `xclip`.

```console
echo "Hello World!" | xclip -sel clip
xclip -sel clip | cat
```

I use it so much I added an alias for it:
```bash
alias clip="xclip -sel clip"
```
