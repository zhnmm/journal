%%Goal: [[2022-01-01]]%%
#  Time for my weekly review ⏰
- [ ] Set file&template name: `= date(eow)+dur(5d, 1s)`

# Plan
- [ ] Open your This Week view to see all tasks you have due this week
- [ ] Add any tasks you need to complete this week that aren't already there
---
> This Week
> ```dataview
task
from outgoing([[]])
where due <= date(this.file.name)
and due
and !completed
group by header

>  ```dataview
list
from "notes"
where author = "John Hexa"
and status = "0-IR"

> ```dataview
list
from outgoing([[repository/jh-notes/index]])
where length(file.inlinks) = 1
limit 5

---
# Review
- [ ] Get to This Week Zero
	- [ ] Open your This Week view
	- [ ] Complete any tasks you've accomplished if you haven't already
	- [ ] Reschedule any tasks you didn't get to for later in the week or next week
- [ ] Review my Projects list
	- [ ] Open each of your projects
	- [ ] Complete or delete tasks that are no longer needed
	- [ ] Add any new tasks that come to mind
	- [ ] Add any relevant due dates
- [ ] Review past and upcoming calendar items
---
> Past
> ```dataview
task
from outgoing([[]])
where completion > date(this.file.name) - dur(7 d)
and completion <= date(this.file.name)
group by header

> IR
> ```dataview
table status, author
from [[]]
where status != "0-IR"
sort status

> ER
	> xx

> Upcoming
> ```dataview
task
from outgoing([[]])
where due <= date(this.file.name) + dur(10 d)
and due
and !completed
group by header

---
- [ ] Review my Waiting For list
> Waiting For
> ```dataview
task
from outgoing([[]])
where waiting_for
group by header
# After my review 🤔
- [ ] What went well this week?
- [ ] What could be adjusted?
	- [ ] Create a task to adjust these items
- [ ] What should I stop doing?
- [ ] What should I start doing?
	- [ ] Create a task to plan these items in more detail
- [ ] Review my Someday/Maybe list
> Someday/Maybe
>```dataview
task
from outgoing([[]])
where (due > date(this.file.name) + dur(8 d)
or !due)
and !completed
and !waiting_for
group by header
- [ ] Review Pending and support files
>  ```dataview
table status
from "notes"
where author = "John Hexa"
and status = "0-IR"
- [ ] Review any other relevant checklists