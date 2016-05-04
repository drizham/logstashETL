Logstash ETL Notes

Important Notes
New indices must always be in lower case.
No error messages will be returned if the file to load is not located.
No relative paths can be used, only used fully qualified paths.
Most of the times no error messages are returned.
Make sure the paths, filters etc are conifgured correctly.
This means going through them line by line

Example files for loading CSVs
1. csvETL0.conf - load a sample file with ISO8601 date format
2. google_price.conf - load a sample yahoo finance *.csv data file


##### Useful Commands to Check Elasticsearch
Check indices stored on a cluster:
curl 'localhost:9200/_cat/indices?v'

##### Command to launch ETL with logstash
From the logstash root directory
./bin/logstach -f <config file>
e.g.
./bin/logstash -f conf/google_price.conf

##### Save a *.csv from Python Pandas in ISO8601
Command to save date time index in a *.csv file in ISO format
df.to_csv('df_ISOdatetime.csv', date_format='%Y-%m-%dT%H:%M:%SZ')

##### Useful Logstash Commands
Run from Logstash command line
List all the available plugins: bin/logstash-plugin list

##### Useful Links:
Just as a reference.
NOTE: the configuration file from this link is not working!
https://kevinkirsche.com/2014/08/25/using-logstash-to-import-csv-files-into-elasticsearch/

This link provides the a strange in explicable fix for loading CSVs. Using:
sincedb_path => "/opt/logstash/bin/dbteste"
http://stackoverflow.com/questions/31095020/use-logstash-csv-filter-doesnt-work

Formatting Dates in Logstash/ Elasticsearch
https://www.elastic.co/guide/en/logstash/current/plugins-filters-date.html#plugins-filters-date-match

