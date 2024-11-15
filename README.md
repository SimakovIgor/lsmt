```
Usage: lsmt --<command> --<p1>[=<value1>] ... --<pN>[=<valueN>]
 * commands are
   generate: generate bash-script for series using templated output and cycle ranges
   extract: extract data from files (and filenames) generated by varios external benchmarking tools (supported: memtier-json, wrk, TODO: memtier, redis-benchmark, sysbench)
   help: see this message
   plot: TODO
   version: use "lsmt -v" or "lsmt --version" to show the version

Examples:
 * lsmt --generate --out="/local/wrk -c128 -t8 -R{{R}} -d30 -L http://localhost > results/wrk_nginx_c128_t4_R{{R}}.txt" --cycles='R=10000-150000,10000' --sleep=10
 * lsmt --extract --origin=wrk --files="results/wrk/*.txt" | sort -n -t, -k10.3 # comma-separated kv-pairs sorted by Rate value numerically
 * lsmt --extract --origin=wrk --files="results/wrk/*.txt" --out="R={{R}}, rps={{rps}}, l={{latency_p99}}" | sort -t ',' -n -k1.3 # template-based output sorted numerically by Rate values
```
