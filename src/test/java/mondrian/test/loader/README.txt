base from mondrian-4.4
fix some bug and add some new characters
the bugs
========
1.support type long timestamp
2.support left/right join
3.fix sort filter:
    the dimension on both filter and row/column
    mdx like "SET [~ROWS_dev2.matrix_log_dev2.matrix_log.pf] AS
    {[dev2.matrix_log].[dev2.matrix_log.pf].[android]}"
    then the filer selections won't be wrote to slicer
    when do some sort, the result is't right, so get filter selections
    from memory and insert to slicer

...and so on


MondrianDataLoader README
=========================

java mondrian.test.loader.MondrianDataLoader 
[-verbose] [-tables] [-data] [-indexes] 
-jdbcDrivers=<jdbcDriver> 
-outputJdbcURL=<jdbcURL> [-outputJdbcUser=user] [-outputJdbcPassword=password] [-outputJdbcBatchSize=100] [-outputDirectory=<directory name>] 
[ [-inputJdbcURL=<jdbcURL> [-inputJdbcUser=user] [-inputJdbcPassword=password]] | [-inputfile=<file name>]]


Examples
========

# load from Access DB to create SQL scripts in the output directory. This directory will contain files: createTables.sql, createData.sql, createIndexes.sql in the dialect of SQL indicated by the outputJdbcURL

-verbose -tables -data -indexes -jdbcDrivers=sun.jdbc.odbc.JdbcOdbcDriver,org.postgresql.Driver -inputJdbcURL=jdbc:odbc:MondrianFoodMart -outputJdbcURL=jdbc:postgresql://localhost/FM2 -outputJdbcUser=postgres -outputJdbcPassword=pgAdmin -outputDirectory=C:\Temp\wip

# load from Access DB to MySQL

-verbose -tables -data -indexes -jdbcDrivers=sun.jdbc.odbc.JdbcOdbcDriver,com.mysql.jdbc.Driver -inputJdbcURL=jdbc:odbc:MondrianFoodMart -outputJdbcURL=jdbc:mysql://localhost/fm2?user=root&password=myAdmin

# load from named file containing insert statements to output JDBC connection (Postgres)

-verbose -data -jdbcDrivers=sun.jdbc.odbc.JdbcOdbcDriver,org.postgresql.Driver -inputFile=C:\Temp\wip\createData.sql -outputJdbcURL=jdbc:postgresql://localhost/FM3 -outputJdbcUser=postgres -outputJdbcPassword=pgAdmin

-verbose -data -indexes -jdbcDrivers=com.mysql.jdbc.Driver -inputFile=C:\Temp\wip\Loader-Output\createData.sql -outputJdbcURL=jdbc:mysql://localhost/textload?user=root&password=myAdmin
