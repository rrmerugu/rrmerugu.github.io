# Project management

This document outlines our project management processes for R2-Core Framework.


The aim is to ensure that the project has a high ["bus factor"](https://en.wikipedia.org/wiki/Bus_factor), and can continue to remain well
 supported for the foreseeable future. Suggestions for improvements to our process are welcome.

-----
## Maintenance team

We have a quarterly maintenance cycle where new members may join the maintenance team. 
We currently cap the size of the team at 5 members, and may encourage folks to step out of the 
team for a cycle to allow new members to participate.


### Current Team

The current maintenance team includes:

1. [@rrmerugu](https://github.com/rrmerugu)
2. [@nitish515](https://github.com/nitish515)


### Maintenance cycles

Each maintenance cycle is initiated by an issue being opened with the `Process` label.

To be considered for a maintainer role simply comment against the issue.
Existing members must explicitly opt-in to the next cycle by check-marking their name.
The final decision on the incoming team will be made by `@rrmerugu`

Members of the maintenance team will be added as collaborators to the repository.

------
###  Responsibilities of team members.

Team members have the following responsibilities.

1. Close invalid or resolved tickets.
2. Add triage labels and milestones to tickets.
3. Merge finalized pull requests.
4. Build and deploy the documentation, using `mkdocs gh-deploy`.
5. Build and update the included translation packs.


Further notes for maintainers:

1. Code changes should come in the form of a pull request - do not push directly to master.
2. Maintainers should typically not merge their own pull requests.
3. Each issue/pull request should have exactly one label once triaged.
4. Search for un-triaged issues with [is:open no:label](https://github.com/rsquarelabs/rsquarelabs-core/issues?q=is%3Aopen+no%3Alabel).


It should be noted that participating actively in this project clearly 
** does not require being part of the maintenance team**. Almost every import part of issue triage and project 
improvement can be actively worked on regardless of your collaborator status on the repository.

-----


##  Release process

The release manager is selected on every quarterly maintenance cycle.

1. The manager should be selected by [@rrmerugu](https://github.com/rrmerugu).

2. The manager will then have the maintainer role added to PyPI package.

3. The previous manager will then have the maintainer role removed from the PyPI package.

Our PyPI releases will be handled by either the current release manager, or by [@rrmerugu](https://github.com/rrmerugu). 
Every release should have an open issue tagged with the `Release` label and marked against the appropriate milestone.

The following template should be used for the description of the issue, and serves as a release checklist.



```
Release manager is @***.
Pull request is #***.

During development cycle:

- [ ] Upload the new content to be translated to [transifex](https://github.com/rsquarelabs/rsquarelabs-core/about/project-management/#translations).


Checklist:

- [ ] Create pull request for [release notes](https://github.com/rsquarelabs/rsquarelabs-core/blob/master/docs/topics/release-notes.md) based on the [*.*.* milestone](https://github.com/rsquarelabs/rsquarelabs-core/milestones/***).
- [ ] Ensure the pull request increments the version to `*.*.*` in [`rsquarelabs_core/__init__.py`](https://github.com/rsquarelabs/rsquarelabs-core/blob/master/rsquarelabs_core/__init__.py).
- [ ] Confirm with @rrmerugu that release is finalized and ready to go.
- [ ] Ensure that release date is included in pull request.
- [ ] Merge the release pull request.
- [ ] Push the package to PyPI with `./setup.py publish`.
- [ ] Tag the release, with `git tag -a *.*.* -m 'version *.*.*'; git push --tags`.
- [ ] Deploy the documentation with `mkdocs gh-deploy`.
- [ ] Make a release announcement on twitter.
- [ ] Close the milestone on GitHub.

To modify this process for future releases make a pull request to the [project management](http://rsquarelabs.github.io/rsquarelabs-core/about/project-management/) documentation.

```


rsquarelabs-core uses a time-based release schedule, with feature releases every eight months or so.
After each feature release, the release manager will announce a timeline for the next feature release.

----- 
## Project requirements

All our test requirements are pinned to exact versions, in order to ensure that our test runs are reproducible. 
We maintain the requirements in the `requirements` directory. The requirements files are referenced from the `tox.ini`
configuration file, ensuring we have a single source of truth for package versions used in testing.

Package upgrades should generally be treated as isolated pull requests. You can check if there are any packages available at 
a newer version, by using the `pip list --outdated`.

----
## Project ownership

The PyPI package is owned by [@rrmerugu](https://github.com/rrmerugu). As a backup [@shivamsk](https://github.com/shivamsk) also has ownership of the package.

If [@rrmerugu](https://github.com/rrmerugu) ceases to participate in the project then [@shivamsk](https://github.com/shivamsk) has responsibility for handing over ownership duties.




