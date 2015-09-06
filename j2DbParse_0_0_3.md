# Introduction #

version 0.0.3 only supports log files(using regular expressions)

_parse file based on rules and insert it into hsqldb_

```
usage: parser [-f <filename>] [-r <ruleName>] [-v]
 -f,--file <filename>   file to process
 -r,--rule <ruleName>   name of section in rules.ini
 -v,--version           version of application
```


_parse file based on rules and insert it into hsqldb(memory db) and allows you to query that data from console_
```
usage: parserLive [-f <filename>] [-r <ruleName>] [-v]
 -f,--file <filename>   file to process
 -r,--rule <ruleName>   name of section in rules.ini
 -v,--version           version of application
```


# Details #

_example usage_
```
parserLive -f example.log -r log

select count(*) from log
21012

select level, max(time) as max_time, count(*) as how_many from log group by log.level order by how_many desc
LEVEL                        MAX_TIME                     HOW_MANY
DEBUG                        2010-03-19 15:43:28,654      19104
INFO                         2010-03-19 15:30:42,122      1784
ERROR                        2010-03-19 15:02:49,388      82
WARN                         2010-03-19 15:30:42,435      42

```

_example data_
```
2010-03-19 14:30:01,341 INFO  [org.quartz.impl.StdSchedulerFactory] Quartz scheduler version: 1.5.2
2010-03-19 14:30:01,341 INFO  [org.quartz.core.QuartzScheduler] Scheduler DefaultQuartzScheduler_$
```
<pre>
_example rules.ini file_<br>
executed for every line<br>
parser inserts only first group<br>
log = table name<br>
level = log table's column (VARCHAR(5000))<br>
</pre>
```
[log]
log.time=(^[\d-\s:,]+)\s\w+\s*\[[\w\.]+\]\s.+
log.level=^[\d-\s:,]+\s(\w+)\s*\[[\w\.]+\]\s.+
log.class=^[\d-\s:,]+\s\w+\s*\[([\w\.]+)\]\s.+
log.data=^[\d-\s:,]+\s\w+\s*\[[\w\.]+\]\s(.+)
```