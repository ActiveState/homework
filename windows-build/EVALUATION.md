## Review Questions

These are the questions that we should ask when reviewing a homework submission.

* Is the submission documentation on hand-building the components sufficiently detailed?
  * are download locations for components listed?
  * are external dependencies on build tools documented?
  * are the instructions sufficient for someone else to follow and get a successful build?
* Is all documentation clear and readable?
* Are the instructions on how to use the automated solution sufficient?
* Are the instructions on how to add packages to the automated solution sufficient?
* Is the submission code in one of the languages listed in the instructions? If not, did the applicant get special permission to use something else?
* Is the submission code runnable on Windows 10 or Windows Server 2016?
* Is the code well organized?
  * Is adding a new package simply a matter of updating config or is new code required?
  * If new code is required, can it re-use existing code
* Does the code avoid repeating similar blocks of code for similar tasks?
* Does the code use third party libraries and tools as appropriate?
* Is the code in a modern style for the language? Does it avoid problematic idioms, packages, etc. for that language?

### Bonus Points

These are not expected as a baseline, but their presence is a good thing.

* Documentation is in Markdown
* Adding a new Python package is trivial
* Adding a new C library is simple
* `BLOSC` library is compiled externally rather than using the version supplied with `cblosc`
