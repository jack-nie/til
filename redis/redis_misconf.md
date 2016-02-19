###Redis misconf

MISCONF Redis is configured to save RDB snapshots, but is currently not able to persist on disk. Commands that may modify the data set are disabled. Please check Redis logs for details about the error.

```
$ redis-cli
> config set stop-writes-on-bgsave-error no
```
