# Contributions

Return to [Table of Contents](/README.md#table-of-contents)

*Note: Reference this file in a markdown file in the root of your repository with the name `CONTRIBUTING.md` - Github will then put an alert & link to this file whem creating a Pull Request.* 

* We are using GitFlow https://github.com/nvie/gitflow
    * Branch name example `{type}/{ticket-no}-{description}` (e.g. `feature/123-user-registration`)
* Every commit (inc. code / documentation etc) must go through a Pull Request
    * Pull Request must contain the template below 
* Before merging a Pull Request, in addition to reviewing the code, check the following:
    * Build status
    * Static Code Analysis
    * Code Coverage
    * Documentation
* When merging a Pull Request `Squash` the **Commits** with the **Feature** Description - this is used for the **Changelog**  
    * Do not delete branches once merge as they will contain the **commit history**

---

## Pull Request check list (please include in your PR description)

```
| - Q. - | - A. - |
| ------ | ------ |
| Tickets | JIRA # |
| Type | Bug Fix / Feature / Tech Debt / Documentation |
| BC breaks? | yes / no |
| Deprecations? | yes / no |
| Docs | new / updated / none |
| Build | - BADGE - SEE SCREENSHOT BELOW - |
| Coverage | - BADGE - SEE SCREENSHOT BELOW - |
| Quality | - BADGE - SEE SCREENSHOT BELOW - |
```

![MarkDown Badges](/contributions/assets/badges.png "MarkDown Badges")
