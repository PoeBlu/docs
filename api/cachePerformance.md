---
title: Cache performance
---

## Cache performance

### Overview

DADI API has caching xupport built in for both a file-based cache and Redis. Caching can be configured globally and at individual collection level.

Due to the thin nature of the server, and because we assume the use of Mongo's mem caching, the cache doesn't have a major impact on performance in a dev environment. If significant network traffic were required to hit the db this should change significantly.

Benchmarks undertaken with ApacheBenchmark (ab) can be seen below.

### File based cache

#### Config

Inside config.{ENVIRONMENT}.json

    "caching": {
        "enabled": false,
        "ttl": 300,
        "directory": "./cache/api/",
        "extension": "json"
    }

* `enabled` if app should use caching (defaults to false)
* `ttl` how long in seconds a cached file should be considered valid (required if cache is enabled)
* `directory` path to the directory where files should be stored. **Important:** this dir must already exist! (required if cache is enabled)
* `extension` the file extension to use when naming the cache files. This has no bearing on the `content-type` of the response, so feel free to put anything here (required if cache is enabled)

#### Notes

The naming convention for files is based on a hex string from a sha1 hash of node's `req.url` value, with the extension per config appended. This keeps cache values unique and avoids naming conflicts.

#### Benchmarks

##### Benchmarks With disk Cache

    Server Hostname:        localhost
    Server Port:            3000

    Document Path:          /vtest/testdb/test-schema
    Document Length:        2 bytes

    Concurrency Level:      10
    Time taken for tests:   2.985 seconds
    Complete requests:      5000
    Failed requests:        0
    Write errors:           0
    Total transferred:      640000 bytes
    HTML transferred:       10000 bytes
    Requests per second:    1674.90 [#/sec] (mean)
    Time per request:       5.971 [ms] (mean)
    Time per request:       0.597 [ms] (mean, across all concurrent requests)
    Transfer rate:          209.36 [Kbytes/sec] received

    Connection Times (ms)
                  min  mean[+/-sd] median   max
    Connect:        0    0   0.0      0       0
    Processing:     2    6   1.9      5      17
    Waiting:        2    6   1.9      5      17
    Total:          2    6   1.9      5      17

    Percentage of the requests served within a certain time (ms)
      50%      5
      66%      6
      75%      7
      80%      7
      90%      8
      95%      9
      98%     12
      99%     14
     100%     17 (longest request)

##### Benchmarks Without disk Cache

    Server Hostname:        localhost
    Server Port:            3000

    Document Path:          /vtest/testdb/test-schema
    Document Length:        2 bytes

    Concurrency Level:      10
    Time taken for tests:   3.043 seconds
    Complete requests:      5000
    Failed requests:        0
    Write errors:           0
    Total transferred:      640000 bytes
    HTML transferred:       10000 bytes
    Requests per second:    1643.32 [#/sec] (mean)
    Time per request:       6.085 [ms] (mean)
    Time per request:       0.609 [ms] (mean, across all concurrent requests)
    Transfer rate:          205.41 [Kbytes/sec] received

    Connection Times (ms)
                  min  mean[+/-sd] median   max
    Connect:        0    0   0.0      0       0
    Processing:     4    6   2.4      5      23
    Waiting:        4    6   2.3      5      23
    Total:          4    6   2.4      5      23

    Percentage of the requests served within a certain time (ms)
      50%      5
      66%      6
      75%      7
      80%      7
      90%      8
      95%     11
      98%     13
      99%     17
     100%     23 (longest request)

### Redis

**_To be added icne Redis support is available_**
