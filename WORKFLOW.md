## WIP limits
- In Progress: 3 | Code Review: 2 | Verification: 2
### Why these numbers
Our team has four members, and each one owns three work items, including
exactly one P1. We set In Progress to 4 so every member can work on their
top-priority item at the same time, but no one is working on more than one
item at once. Our team lead also owns hands-on work (#5, #8, #12), so the
lead counts toward this limit.

In the previous release, developers started new tasks while existing work
was waiting for review, and some pull requests stayed open for days. We set
Code Review and Verification lower than In Progress on purpose. Our
Definition of Done requires a review and a verification by someone other
than the author, so every item in those columns consumes a teammate's time.
With four people, at most two reviews and two verifications can happen at
once without everyone being pulled away from their own work. If these
columns fill up, work stalls visibly, which tells us review capacity is the
bottleneck instead of hiding it.

### Team rule
If a column is at its limit, no one pulls new work into it. Instead, help
clear the next stage: review a pull request or verify an item before
starting anything new.

### The lead's work
The lead also coordinates, unblocks, and coaches, so the lead's items may
move more slowly. We accept this, and the lead should flag when coaching or
production support will delay their own item.

### Review plan
These numbers are a hypothesis. We will track review turnaround and blocked
work, and revisit the limits at the end of the cycle using our own data.
