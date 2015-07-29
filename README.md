# DNS fuzzing

This is the repository we store a unique seeds for American Fuzzy Lop (http://lcamtuf.coredump.cx/afl/) fuzzing.

## Packets

We have a fuzz test for (Knot DNS)[CZ-NIC/knot] packet parser and the packet/ directory contains some unique packets we have used to prime the AFL fuzzing.

## Contributions

You are certainly welcome to contribute more unique inputs (see afl-cmin how to produce unique corpus).  Please send the changes as Pull Requests.

As an example - to use corpus minimization with Knot DNS tests-fuzz/packet you need to do:

```
# store some packets in ~/knot-seeds
make check
afl-cmin -i ~/knot-seeds -o ~/knot-seeds-cmin -m 1000000 -t 400000 -- tests-fuzz/packet
```

The ~/knot-seeds-cmin will contain minimized corpus.

Please note that since each DNS server has a different code path the minimized corpus should be different for each DNS server.  This repository aims to contain the superset of unique packets and you will need to minimize it yourself before running fuzzer over your favorite DNS server.
