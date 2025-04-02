# IRONdb Relay Release Notes

## 0.1.1[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#011) <a href="#id-011" id="id-011"></a>

2024-03-27

* Update libmtev dependency, which fixes potential memory corruption issues.

## 0.1.0[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#010) <a href="#id-010" id="id-010"></a>

2024-01-31

* Add TLS support

## 0.0.57[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#0057) <a href="#id-0057" id="id-0057"></a>

2024-01-25

* Fix Docker build to bust apt caches and avoid errors.
* Update setup script to better support HTTPS URLs in the bootstrap list.
* Add C++ guards to headers and convert send code to C++ to take advantage of libsnowth features.

## 0.0.56[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#0056) <a href="#id-0056" id="id-0056"></a>

2023-11-06

* Add Docker support.

## 0.0.55[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#0055) <a href="#id-0055" id="id-0055"></a>

2023-09-05

* Use new `libsnowth_init` function to avoid potential buffer overflow.

## 0.0.54[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#0054) <a href="#id-0054" id="id-0054"></a>

2023-06-06

* Remove unused DH parameter files from configuration.

## 0.0.53[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#0053) <a href="#id-0053" id="id-0053"></a>

2023-03-06

* Fix simdjson linking.

## 0.0.52[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#0052) <a href="#id-0052" id="id-0052"></a>

2022-09-14

* Fix log rotation.

## 0.0.51[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#0051) <a href="#id-0051" id="id-0051"></a>

2022-06-09

* Initialize `metric_t` structures to avoid data corruption.

## 0.0.50[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#0050) <a href="#id-0050" id="id-0050"></a>

2022-02-07

* Replace deprecated `mtev_atomic*` types and functions with compatibles ones from ConcurrencyKit (libck).

## 0.0.49[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#0049) <a href="#id-0049" id="id-0049"></a>

2022-02-04

* Fix an issue where some jlog subscribers were not advanced when they did not have work to do. This led to increased disk usage from processed segments that could not be removed.

## 0.0.48[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#0048) <a href="#id-0048" id="id-0048"></a>

2021-04-09

* Bring setup and start scripts into the repo.

## 0.0.47[​](https://docs.circonus.com/irondb/tools/irondb-relay-release-notes#0047) <a href="#id-0047" id="id-0047"></a>

2021-03-24

* Improved error handling/data parsing.
* Accept UTF-8 Graphite data.
* Move `debug/parsing` log to `debug/parsing/graphite` and add `error/parsing/graphite` log to catch parsing errors.
* Add configurable limits to acceptable data timestamps. Default is one year into the past or future from the current time. This is available at `<ingestion max_allowable_days_before_current_time="<num days">/>` and `<ingestion max_allowable_days_after_current_time="<num_dats">/>`. A value of `0` means no limit.
