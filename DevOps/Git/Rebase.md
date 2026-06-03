The git rebase command is one of two commands (along with [[DevOps/Git/Merge|Merge]]) used to combine one branch onto another.

```sh
git rebase main
```

### Example

Lets say you forked on branch `main` after commit `B`

```
main:    A---B---C               
			   \
feature:        D---E
```

The `main` branch gets more commits:

```
main:    A---B---C---F---G               
			   \
feature:        D---E
```

Git places the commit of `feature` over the last commit of `main`:

```
main:    A---B---C---F---G                           
						   \
feature:                    D'---E'
```

`D'` and `E'` are now the last commits of `main`

## Characteristics

### Pros

- Cleaner, linear history
- Easier to read logs
- Avoids unnecessary merge commits
### Cons

- Rewrites commit history
- Dangerous on shared/public branches
- Can confuse collaborators if already pushed