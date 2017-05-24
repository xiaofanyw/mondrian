This is a source, binary or data distribution of Mondrian,
an OLAP Engine written in Java.

This code is released under the terms of the Eclipse Public
License v1.0 (EPL); see LICENSE.html.

For installation instructions, see doc/install.html
(http://mondrian.pentaho.com/documentation/installation.php).

The version is described in VERSION.txt.

Home page: http://mondrian.pentaho.com
Project home: http://sourceforge.net/projects/mondrian/
Email: jhyde@pentaho.com


base on mondrian-4.4
fix some bug and add some new characters
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