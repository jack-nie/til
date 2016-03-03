###How can I search and replace recursively in a directory?

Th syntax for sed is similar to Vim's (they're both descendants of ed), though not identical. With GNU sed you can also use -i for in-place edits (normally sed emits the modified version to stdout).

For example:

```
find proj -name '*.rb' -type f -exec sed -i -e 's/regex/replacement/g' -- {} +
```

Piece by piece:

```
    proj = search in "proj" tree
    -name '*.rb' = for things whose names match '*.rb'
    -type f = and are regular files (not directories, pipes, symlinks, etc.)
    -exec sed = run sed with these arguments:
        -i = with in-place edits
        -e 's/regex/replacement/g' = execute a "substitute" command (which almost identical to Vim's :s, but note lack of % -- it's the default in sed)
        -- = end of flags, filenames start here
        {} = this tells find that the filenames it found should be placed on sed's command-line here
        + = this tells find that the -exec action is finished, and we want to group the arguments into as few sed invocations as possible (generally more efficient than running it once per filename). To run it once per filename you can use \; instead of +.
```
