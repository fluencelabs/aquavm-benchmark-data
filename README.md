# Preparing data for the performance_metering

One may need to regenerate data on changing data format.  Here is the instruction for data regeneration.

## `parser_10000_100`

Data are empty, no regeneration required.

## `dashboard`, `network_explore`, `multiple-cids{N}` and `multiple-peers{N}`

Run `junk/gen-bench-data/gen_benchmark_data.sh` in the `aquavm` repo.  No WASM binary required.
It will save all required benchmark files into a dest directory, including params and keypair.

## `big_data` and `long_data`

In the `junk/cidify` directory, run

``` sh
cargo run -- ./anomaly_big.json simple-calls-info.json > ../../air/benches/data/anomaly_big.json
cargo run -- ./anomaly_long.json simple-calls-info.json > ../../air/benches/data/anomaly_long.json
cp ../../air/benches/data/anomaly_big.json ../../benches/performance_metering/big_values_data/prev_data.json
cp ../../air/benches/data/anomaly_long.json ../../benches/performance_metering/long_data/cur_data.json
```

You may need update the `junk/cidify` tool if you change data format again.
