###How to make --no-ri --no-rdoc the default for gem install?

add following line to your local `~/.gemrc` file (it is in your home folder)

```
  gem: --no-document
```

or you can add this line to the global gemrc config file. Here is how to find it (in Linux)

```
  strace gem source 2>&1 | grep gemrc
```


