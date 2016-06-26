# Release Management



## Release Versioning

Since version 1.0, rsquarelabs-core’s release numbering works as follows:

- Versions are numbered in the form **A.B** or **A.B.C**.

- **A.B** is the feature release version number. Each version will be 
mostly backwards compatible with the previous release. Exceptions to this 
rule will be listed in the release notes.

- **C** is the patch release version number, which is incremented for 
bugfix and security releases. 
These releases will be 100% backwards-compatible with the previous patch release. 
The only exception is when a security or data loss issue can’t be fixed without breaking 
backwards-compatibility. If this happens, the release notes will provide detailed upgrade instructions.

- Before a new feature release, we’ll make alpha, beta, and release candidate releases. 
These are of the form **A.B alpha/beta/rc N**, which means the **Nth alpha/beta/release** candidate of version **A.B**.

In git, each release will have a tag indicating its version number, signed 
with the release key. Additionally, each release series has its own branch, 
called **stable/A.B.x**, and bugfix/security releases will be issued from those branches.


### Feature release
Feature releases (A.B, A.B+1, etc.) will happen roughly every eight months – see release process for details. These releases will contain new features, improvements to existing features, and such.

### Patch release
Patch releases (A.B.C, A.B.C+1, etc.) will be issued as needed, to fix bugs and/or security issues.

These releases will be 100% compatible with the associated feature release, unless this is 
impossible for security reasons or to prevent data loss. So the answer to “should I upgrade 
to the latest patch release?” will always be “yes.”

### Long-term support release
Certain feature releases will be designated as long-term support (LTS) releases. These releases will get security and data loss fixes applied for a guaranteed period of time, typically three years.

-------
## Supported versions

At any moment in time, developer team will support a set of releases to varying levels.

- The current development master will get new features and bug fixes requiring non-trivial refactoring.

- Patches applied to the master branch must also be applied to the last feature release branch, to be released in the next patch release of that feature series, when they fix critical problems:

    - Security issues.
    - Data loss bugs.
    - Crashing bugs.
    - Major functionality bugs in newly-introduced features.
    - Regressions from older versions of rsquarelabs-core.

The rule of thumb is that fixes will be backported to the last feature release 
for bugs that would have prevented a release in the first place (release blockers).

- Security fixes and data loss bugs will be applied to the current master, 
the last two feature release branches, and any other supported long-term 
support release branches.

- Documentation fixes generally will be more freely backported to the last 
release branch. That’s because it’s highly advantageous to have the docs 
for the last release be up-to-date and correct, and the risk of introducing 
regressions is much less of a concern.

- As a concrete example, consider a moment in time halfway between the release 
of rsquarelabs-core 5.1 and 5.2. At this point in time:

- Features will be added to development master, to be released as rsquarelabs-core 5.2.

- Critical bug fixes will be applied to the stable/5.1.x branch, and released as 5.1.1, 5.1.2, etc.

- Security fixes and bug fixes for data loss issues will be applied to master and to the stable/5.1.x, stable/5.0.x, and stable/4.2.x (LTS) branches. They will trigger the release of 5.1.1, 5.0.5, 4.2.8, etc.

- Documentation fixes will be applied to master, and, if easily backported, to the latest stable branch, 5.1.x.


-------
## Release cycle

Each release cycle consists of three parts:

### Phase one: feature proposal

The first phase of the release process will include figuring out what major features to include in the next version. This should include a good deal of preliminary work on those features – working code trumps grand design.

Major features for an upcoming release will be added to the wiki roadmap page, e.g. https://github.com/rsquarelabs/rsquarelabs-core/wiki/ROADMAP.

###  Phase two: development

The second part of the release schedule is the “heads-down” working period. Using the roadmap produced at the end of phase one, we’ll all work very hard to get everything on it done.

At the end of phase two, any unfinished features will be postponed until the next release.

Phase two will culminate with an alpha release. At this point, the stable/A.B.x branch will be forked from master.


###  Phase three: bugfixes


The last third of a release cycle is spent fixing bugs – no new features will be accepted during this time. We’ll try to release a beta release after one month and a release candidate after two months.

The release candidate marks the string freeze, and it happens at least two weeks before the final release. After this point, new translatable strings must not be added.

During this phase, committers will be more and more conservative with backports, to avoid introducing regressions. After the release candidate, only release blockers and documentation fixes should be backported.

In parallel to this phase, **master** can receive new features, to be released in the **A.B+1** cycle.



-------



## Bug-fix releases

After a major release (e.g. A.B), the previous release will go into bugfix mode.

The branch for the previous major release (e.g. **stable/A.B-1.x**) will include 
bugfixes. Critical bugs fixed on master must also be fixed on the bugfix branch; 
this means that commits need to cleanly separate bug fixes from feature additions. 
The developer who commits a fix to master will be responsible for also applying 
the fix to the current bugfix branch.


----- 
  
