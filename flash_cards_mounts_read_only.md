###Flash Cards Mounts Read Only

1. First, Eject the flash card, then run:

```
tail -f /var/log/syslog
```

2. Plugin in the flash card again and check the output.
  Find the wrong place. Lets say `/dev/sdb4`.

3. run `sudo dosfsck -v -a /dev/sdb4`.
