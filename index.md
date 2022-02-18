# Repository
## John Hexa
```dataview
table file.inlinks
from outgoing([[repository/jh-notes/index]])
where length(file.inlinks) > 1
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
# 读书笔记
## John Hexa
```dataview
table status
from "notes"
where author = "John Hexa"
sort status
```
## Others
```dataview
table status
from "notes"
where author != "John Hexa"
sort file.name
```