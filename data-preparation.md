## Infrastructure preparation

### Create DB

1. prepare CH database with required scale

```bash
git clone https://github.com/Altinity/tpc-ds.git
cd tpc-ds
cd bin

./build-tool.sh

rm -rf ../data

./generate-data.sh 100 # 100 is scale

clickhouse-client -mn < schema/tpcds.sql

./bin/upload-data.sh

# script to monitoring DB size
# while :; do sudo du -hs /var/lib/clickhouse/data/tpcds; sleep 90; done
```

2. check the correctness of CH database

Compare the count of rows with [TPC DS Specification (see '3.2 TEST DATABASE SCALING')](https://github.com/Altinity/tpc-ds/blob/master/tpc-ds-tool/v2.11.0rc2/specification/specification.pdf) per table.
