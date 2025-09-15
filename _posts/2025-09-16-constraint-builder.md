---
title: "CONSTRAINT-BUILDER"
date: 2025-09-16
---

I have this big data model called `Constraint`

I have to interpret this `Constraint` and create an actual expression to add to my `model`

When I implement a new model, or new functionality, I clearly have to do this in stages.

My process is this:
```
for each constraint: # there could be 100 or more
  interpret and build a constraint
```

However `interpret and build a constraint` is a big job.
(Also I’m sure there is lots of duplication that I could remove in future from one constraint to the next.)
