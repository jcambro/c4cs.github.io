---
---

uniq
------

`uniq`, often used with  `sort`, allows a user to report, or filter, repeated lines that are adjacent in a file. 

<!-- minimal example -->
~~~ bash
$ sort in.txt | uniq 
line1
line2
line3
~~~

<!--more-->

### Useful Options / Examples

Some common and useful flags include `-d` or `-u` for listing lines that are duplicated or that are unique, respectfully. As well as `-c` for counting the number of times a line was duplicated.

#### Example command

~~~ bash
$ sort in.txt | uniq -c 
  2 line1
  3 line2
  1 line3
~~~

The `-c` flag counts the number of times an adjacent line was duplicated. It displays the count followed by the line. 


#### Example command

~~~ bash
$ sort in.txt | uniq -d
line1
line2
~~~

The `-d` flag lists only the lines in the file that had a duplicate line adjacent to it. Considering the counts from the above `-c` example, we can see that only lines with counts greater than 1 were listed. 


#### Example command

~~~ bash
$ sort in.txt | uniq -u
line3
~~~

The `-u` flag lists only lines in the file that did not have a duplicate line adjacent to it. It is the inverse of the `-d` flag. 

#### Example command

~~~ bash
$ sort in.txt | uniq -i
line1
line2
line3
~~~

The `-i` flag tells uniq to be case insensitive when comparing adjacent lines. With the `-i` flag given, 'line1' and 'LINE1' will be conisered duplictes if adjacent in the file and which ever string appeared first in the file is the one that will be displayed.

#### Example command

~~~ bash
$ sort in.txt | uniq -c -f 1
6 line1
~~~

The `-f num` flag tells `uniq` to ignore the first `num` 'fields' in each line. A 'field' is a string in the line seperated by whitespace. In this example, since each line had only one field and we gave `num` a value of 1, the command would compare only the empty space in each line, which of course would be duplicates.
