###How can I apply stored macro to multiline

Execute the macro stored in register a on line 5 through 10

```
  :5, 10norm! @a
```
Execute the macro stored in register a on all lines do

```
  :%norm! @a
```

for more info, enter `:help normal`
