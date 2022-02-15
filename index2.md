# Repository
## John Hexa
```dataview
table file.inlinks
from "repository/jh-notes/All" or "repository/jh-notes/titled"
sort file.name
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