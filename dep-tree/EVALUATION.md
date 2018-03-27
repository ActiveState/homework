## Review Questions

These are the questions that we should ask when reviewing a homework submission.

* Is the submission in one of the languages listed in the instructions? If not, did the applicant get special permission to use something else?
* Is the submission runnable on Ubuntu Trusty or Xenial, or via Docker? Did the instructions supplied by the candidate outline all the steps needed to get this working, including installing packages (system, language, etc.)? Are there any unreasonably complicated steps required (editing `/etc` files, installing many packages from non-official sources, creating complex config files, etc.)?
* If the submission is not in Go or Perl, do the instructions contain enough detail for us to understand how to run the submission?
* Does the submission include instructions for us in a `README` or via a `--help` flag?
  * Note that if the submission isn't in Go or Perl it must have a `README`.
* Does the submission pass our test harness?
* Does the code handle corner cases sanely?
  * Cannot find metadata for a distro.
  * Cannot resolve a module name to a distro name.
  * No `--name` flags on the command line.
* Is the code well organized?
  * Is it split into multiple packages/classes/modules in an appropriate way?
  * Is it split into reasonable sized subs/methods?
  * Is there a clear split between the command line program and libraries?
* Does the code avoid repeating similar blocks of code for similar tasks?
* Does the code use third party libraries and tools as appropriate?
* Is the code in a modern style for the language? Does it avoid problematic idioms, packages, etc. for that language?

### Bonus Points

These are not expected as a baseline, but their presence is a good thing.

* Does the code have unit and/or functional tests?
  * Is this code organized and clear?
* Does the code have API documentation?
  * How well written and organized is this documentation?
