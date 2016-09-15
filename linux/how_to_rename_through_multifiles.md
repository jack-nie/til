### how to rename through multifiles

In a terminal, cd into the right directory and then run this.

```
rename 's/\:/-/g' *.png -vn

```

This will preview the renaming. It should replace : with -.

If that looks right, remove the n from the end and then it will do the actual renaming.
