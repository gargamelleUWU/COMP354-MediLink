# Definition of Done

A work item moves to **Done** only when every applicable item below is checked.
If an item doesn't apply, write "N/A" with a short reason in the issue.

## All work items
- [ ] Every acceptance criterion in the issue is met
- [ ] Pull request reviewed and approved by at least one teammate (not the author)
- [ ] Verified by someone other than the author, with a short note in the issue
      describing what was checked
- [ ] Automated tests added or updated, and CI is passing
- [ ] No sensitive patient information (names, health details) in logs, code,
      or test data
- [ ] README or runbook updated if behavior, setup, or support steps changed
- [ ] Issue updated with a brief summary and linked to its pull request

## Additional checks by type
**Defects**
- [ ] Root cause noted in the issue
- [ ] Regression test added that fails without the fix

**Maintenance / production support**
- [ ] Change tested in staging before production
- [ ] Rollback or recovery step documented
- [ ] Affected clinics informed if their workflow was impacted

**Technical (CI, logging, dependencies)**
- [ ] Setup or usage instructions documented
- [ ] Team informed of any change to how they work (e.g., new merge rules)

**Update**
- [ ] Side effects on related features (reminders, notifications, search) considered and tested
