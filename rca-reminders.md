# Root Cause Analysis: Reminders sent after cancellation (#13)

> Note: This is a simulated incident. Technical causes below are
> working hypotheses that the team would verify against logs and code.

## Symptom
Patients who cancel an appointment occasionally still receive an
appointment reminder.

## Five Whys
1. **Why did cancelled patients receive reminders?**
   The reminder job sent reminders for appointments that were already cancelled.
2. **Why?**
   The job prepares its list of reminders ahead of time and does not
   re-check appointment status at send time. A cancellation that happens
   between list preparation and sending is missed, which explains why it
   happens only "occasionally".
3. **Why is it designed that way?**
   Cancellation and reminders were built as separate flows, and the
   interaction between them was never defined. Issue #10 (stale search
   results) shows a similar pattern: data going out of date between
   components.
4. **Why was this not caught before production?**
   Acceptance criteria and tests covered each flow separately, not their
   interaction. Test coverage is limited to the booking path (#7) and
   there is no automated check on pull requests yet (#8).
5. **Why did those gaps exist?**
   Our issue template and Definition of Done do not prompt for side
   effects on related features, and the system gives us no visibility into
   what messages it sends or fails to send (#12). Problems reach us
   through clinics and patients.

## Structured analysis

| Level | Finding |
|---|---|
| **Symptom** | Patients who cancel still receive reminders |
| **Immediate cause** | The reminder job sends from a prepared list without re-checking appointment status at send time |
| **Contributing factors** | No defined interaction between cancellation and reminder flows; tests cover booking only (#7); no automated gate on PRs (#8); no monitoring of messaging behavior (#12); similar stale-data behavior seen in #10 |
| **Underlying causes** | DoD and issue template do not require checking side effects on related features; the team has no routine for monitoring what the system sends |

## Information still needed
- How often this happens and how many patients were affected
- Whether it correlates with cancellations made shortly before the send time
- Whether SMS and email behave the same way
- Whether it began with a specific release

## Corrective and preventive actions

| # | Type | Action | Issue | Owner | Due |
|---|---|---|---|---|---|
| 1 | Corrective | Check appointment status at send time; remove queued reminders when an appointment is cancelled | #14 | [name] | [date] |
| 2 | Preventive | Add "side effects on related features checked" to the Definition of Done and issue template | #15 | [name] | [date] |
| 3 | Preventive | Add a regression test: cancel an appointment, confirm no reminder is sent | #7 (scope extended) | [Negin] | [date] |
| 4 | Preventive | Log/alert when a reminder is sent for a non-active appointment | #12 (scope extended) | [Felix] | [date] |
| 5 | Preventive | Add cancellation/reminder behavior to acceptance criteria of upcoming work | #1, #2 (updated) | [Julian / Leana] | [date] |

## Lessons
The incident came from gaps in how requirements, tests and monitoring were
set up, not from an individual's action. The actions above target those
process gaps.
