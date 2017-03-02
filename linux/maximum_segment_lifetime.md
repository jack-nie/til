Maximum segment lifetime is the time a TCP segment can exist in the internetwork system. It is arbitrarily defined to be 2 minutes long.[1]

The Maximum Segment Lifetime value is used to determine the TIME_WAIT interval (2*MSL)

The command that can be used on many Unix systems[not specific enough to verify] to determine the TIME_WAIT interval is:

```
ndd -get /dev/tcp tcp_time_wait_interval
60000 (60 seconds) is a common value.

```

On FreeBSD systems this description and value can be checked by the command sysctl:[2]

```
   sysctl -d net.inet.tcp.msl
   sysctl net.inet.tcp.msl

```

which gets the result:

```
   net.inet.tcp.msl: Maximum segment lifetime
   net.inet.tcp.msl: 30000

```

On some Linux systems, this value can be checked by either of the commands below:


```
   sysctl net.ipv4.tcp_fin_timeout
   cat /proc/sys/net/ipv4/tcp_fin_timeout

```
