# About
Proxy Connect is a ld preload library that can be used to tunnel 
arbitrary TCP connections via HTTP proxies which support the `CONNECT`
command.

# Configuration
Currently, two tunnel setups are supported:
```
                     Point to Point to Multipoint
                +--------+    +-------+    +----------+
                | CLIENT +----+ PROXY +----+ INTERNET |
                +--------+    +-------+    +----------+
   This configuration makes sense if you are connected to a LAN which
   provides a HTTP proxy that takes `CONNECT' commands to arbitrary
   ports.


                Point to Point to Point to Multipoint
       +--------+    +---------+    +---------+    +----------+
       | CLIENT +----+ PROXY A +----+ PROXY B +----+ INTERNET |
       +--------+    +---------+    +---------+    +----------+
  This setup can be used to tunnel through a connected proxy A which
  supports `CONNECT' to certain ports only (eg https, 443). Over this
  connection another `CONNECT' can be sent to proxy B without this
  limitation that isn't reachable otherwise.
```

See Makefile for configuration issues.

# Installation
After executing "make" enter `LD_PRELOAD="/path/to/proxy_connect.so" command` for single usage or `echo "/path/to/proxy_connect.so" >> /etc/ld.so.preload` for system wide setup.

