# impala-get-json-object-udf
A UDF for Cloudera Impala ( Hive [`get_json_object`](https://cwiki.apache.org/confluence/display/Hive/LanguageManual+UDF#LanguageManualUDF-get_json_object) equivalent )

## build
- install impala-udf-dev(el), libboost-dev(el)
- `cmake .`
- `make`

## install
- upload `build/libjsonUdf.so` to `[hdfs path]/libjsonUdf.so`
- `impala-shell> create function [database.]json_get_object (string, string) returns string location '[hdfs path]/libjsonUdf.so' symbol='JsonGetObject';`

## usage
- `impala-shell> select json_get_object('{"name":"steven"}', '$.name');`
- --> returns a string `steven`
