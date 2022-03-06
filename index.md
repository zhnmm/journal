# Repository
## John Hexa
```dataview
table file.size
from outgoing([[repository/jh-notes/index]])
where length(file.inlinks) = 1
sort file.size desc
limit 10
```
## Python for Everybody
```dataview
table file.inlinks
from "repository/py4e-cn/book3"
where file.name != "README"
sort file.name
```
# Web
```dataview
table file.inlinks
from "web"
```