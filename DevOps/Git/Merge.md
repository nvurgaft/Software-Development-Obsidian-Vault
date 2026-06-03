The git merge command is one of two commands (along with [[Rebase]]) used to combine one branch onto another.

```sh
git merge feature-branch
```

### Example

Lets say you forked on branch `main` after commit `B`

```
main:    A---B---C               
			   \
feature:        D---E
```

If you run the merge command git will creates a merge commit:

```
main:    A---B---C-------M               
			   \       /
feature:        D'----E'
```

`M` is the merge commit.

If you run the rebase command git will impose the commit history of `feature` on top of `main`

```
main:   A---B---D'---C---E'---M 
```
## Characteristics

### Pros

- Preserves full branch history
- Safe and non-destructive
- Good for collaborative/shared branches
- Easy to understand what happened historically
### Cons

- History can become cluttered with many merge commits