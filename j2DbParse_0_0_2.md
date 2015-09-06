# Introduction #

only supports log files(using regular expressions)

_parse file based on rules and insert it into hsqldb_

```
usage: parser -f <filename> -r <filename>
 -f,--file <filename>    file to process
 -r,--rules <filename>   processing rules file
```


_parse file based on rules and insert it into hsqldb(memory db) and allows you to query that data from console_
```
usage: parserLive -f <filename> -r <filename>
 -f,--file <filename>    file to process
 -r,--rules <filename>   processing rules file
```


# Details #

_example usage_
```
parserLive -f example.log -r example.rules.properties

select count(*) from log
1400

select level, max(time) as max_time from log group by log.level
LEVEL                                                                 MAX_TIME
DEBUG                                                                 2010-05-03 14:30:15,154
INFO                                                                  2010-05-03 14:30:15,247
WARN                                                                  2010-05-03 14:30:15,294
```

_example data_
```
2010-05-03 14:30:01,341 INFO  [org.quartz.impl.StdSchedulerFactory] Quartz scheduler version: 1.5.2
2010-05-03 14:30:01,341 INFO  [org.quartz.core.QuartzScheduler] Scheduler DefaultQuartzScheduler_$
```
<pre>
_example processing rules file_<br>
executed for every line<br>
parser inserts only first group<br>
log = table name<br>
level = log table's column (VARCHAR(5000))<br>
</pre>
```
log.class=\[([\w\.]+)\]
log.level=^[\d-\s:,]+(\w+)
log.time=(^[\d-\s:,]+)
log.data=\[[\w\.]+\]\s(.+)
```