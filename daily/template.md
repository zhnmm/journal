```dataview
table status
from "notes"
where author = "John Hexa"
and status = "0-IR"
```
```dataview
table file.inlinks
from outgoing([[repository/jh-notes/index]])
where length(file.inlinks) = 1
limit 5
```
```dataview
table file.inlinks
from outgoing([[repository/jh-notes/index]])
where length(file.inlinks) = 1
sort file.name desc
limit 5
```
- IR
	- xx
- ER
	- xx
- Others
	- xx