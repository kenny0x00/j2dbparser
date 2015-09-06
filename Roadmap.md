_Strikeout equals done_

<pre>
input:<br>
-~~log(regex in prop file)~~ 		                (1)<br>
-dir(recurence filenames with path)		        (3)<br>
-xml(xpath or maybe regex sax or StAX?<br>
so i could parse stackoverflow data dump)		(5)<br>
-excel(columns=table columns)	                        (5)<br>
-java(ANTR or http://code.google.com/p/javaparser/)     (5)<br>
-sql(ANTR or some SQL parser-Hibernate's sucks)	        (5)<br>
<br>
<br>
console options:<br>
-scan file(comma separated) - auto-recognize ext	(1)<br>
-~~scan file rulesProps~~				        (1)<br>
-dynamicUpdate (use stream & channels)			(5)<br>
-rescan file<br>
-sqlapp file params<br>
<br>
<br>
specification:<br>
-outputSqlTemplates.txt	-	templates to show after parsing<br>
(also for count and between dates)<br>
select $columns from $table<br>
-while parsing count bytes and show every 5%?<br>
-~~use commons-cli~~<br>
-prop regex - auto-detect is its escaped<br>
-props regex(rules): - extendable like expr in jQuery<br>
~~table.column=regex~~<br>
table.column(columnType)=regex<br>
table.column*=regex - index on column		(5)<br>
table.id_person^=person - surrogate keys<br>
<br>
<br>
addons:<br>
-update?<br>
-delete?<br>
-jpa/jdbc gen?<br>
-excute sql script after parsing? why use it? hmm<br>
<br>
TODO:<br>
Transform this into a table