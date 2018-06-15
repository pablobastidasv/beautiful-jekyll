---
layout: post
published: true
title: Web Service performance with "wrk"
---
## Intalling on Mac

```bash
brew install wrk
```

## Running your performance test

```bash
wrk -t6 -c24 -d30s 'http://localhost:8080'
```

Where:
  - `-t6` means: lets use 6 threads
  - `-c24` means: lets keep 24 connections
  - `-d30s` means: lets do the http call during 30 seconds
  
Getting results like this: 
```
Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency    11.14ms   21.01ms 237.22ms   90.22%
    Req/Sec     0.92k   358.97     1.76k    63.50%
  165669 requests in 30.05s, 73.82MB read
Requests/sec:   5512.96
Transfer/sec:      2.46MB
```

Where the "important" mesure is `Request/sec`, has more bigger it is, better is the performance of our service.