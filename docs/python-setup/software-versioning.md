# Software Versions and Which to Choose

## Semantic Versioning

In the dynamic world of software development, versioning plays a crucial role in managing the evolution and maintenance of software applications. Versioning is the process of assigning unique identifiers to different states or releases of a software product. This practice helps developers and users keep track of changes, improvements, bug fixes, and new features over time.

Software versioning involves a systematic method to label different iterations of software as it evolves. These versions often include a set of numbers separated by periods, such as 1.0.0 or 2.1.3. The components of these version numbers typically represent:

- **Major Version:** Significant changes that might include backward-incompatible updates or major new features.
- **Minor Version:** Incremental improvements and additions that are backward-compatible.
- **Patch Version:** Small fixes and patches, often for bugs or security vulnerabilities, that are backward-compatible.

This clear identification helps teams coordinate development, manage dependencies, and communicate the nature of changes to users effectively. This convention is also known as semantic versioning.

For example, in the version number 2.1.3:

- 2 indicates the major version with potentially breaking changes.
- 1 indicates the minor version with new, backward-compatible features.
- 3 indicates the patch version with backward-compatible fixes.

## My Approach to Choosing Python Versions

I tend to stay one version behind the latest release as it often takes time for python packages to catch up. For example, at the time of writing, the latest version of Python is 3.13, but I am using 3.12 for this course. It is important to be clear which version of Python your code runs on.
