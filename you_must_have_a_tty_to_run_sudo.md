###Sudo: Sorry, You Must Have a Tty to Run Sudo

To disable requiretty globally or to a single command, you have two options:

1. Replace Defaults requiretty by Defaults !requiretty in your /etc/sudoers. This will impact your global sudo configuration.

Alternatively, you can change this configuration at a per user, per group or per command basis

```
    Defaults!/path/to/my/bin !requiretty
    Defaults:myuser !requiretty
```

2. Connect by ssh using -t options

####From man ssh:

```
 -t      Force pseudo-tty allocation.  This can be used to execute arbitrary screen-based programs on a remote
         machine, which can be very useful, e.g. when implementing menu services.  Multiple -t options force
         tty allocation, even if ssh has no local tty.
```
