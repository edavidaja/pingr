


# pingr: check if a server is alive

[![Linux Build Status](https://travis-ci.org/gaborcsardi/ping.png?branch=master)](https://travis-ci.org/gaborcsardi/ping)
[![Windows Build status](https://ci.appveyor.com/api/projects/status/4vvet9e6irj06g1w)](https://ci.appveyor.com/project/gaborcsardi/ping)

The pingr package is a simple utility that can be used to check
if a remote machine is running, by sending network packets to it.
It is similar to the command line `ping` program, in fact for ICMP
packages it just calls `ping`.

## ICMP ping

The `ping()` function does ICMP ping, via the system's `ping` utility:


```r
library(pingr)
ping("127.0.0.1")
```

```
#> [1] 0.037 0.143 0.087
```

By default it sends three packets and measures the time it receives and answer.
It waits between sending out the packets, so if you want a really quick check,
you can just send a single packet:


```r
ping("127.0.0.1", count = 1)
```

```
#> [1] 0.045
```

If a machine is down (or it does not exist), then `NA` is returned instead
of the roundtrip time:


```r
ping("192.0.2.1", count = 1)
```

```
#> [1] NA
```

## TCP ping

With TCP ping we can check if a machine is listeing on a TCP port, e.g. if
google's search web server is up and running:


```r
ping_port("www.google.com", port = 80, count = 1)
```

```
#> [1] 23.8
```
