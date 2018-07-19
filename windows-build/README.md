Thank you for your interest in working with ActiveState as a build
engineer. This programming assignment will help us to evaluate your skills
relative to our working environment and is used as a primary tool in our
hiring process. Later on in the hiring process we will have one of our
developers pair with you on making changes to your code, fixing bugs, etc.

We expect this assignment to occupy no more than 3 hours of your time.
We are primarily looking for high-quality documentation and we recognize
that you may not have time to fully polish your work, so focus on
documentation before code tests and other niceties.

We strongly encourage the use of third party tools and packages as you
work on this assignment.

We will also accept automation solutions provided in the following
languages:

* PowerShell
* Perl
* Tcl
* Python
* Ruby

If you would like to use a different language or tool, please contact
us before continuing with this assignment.

## Time Limit

We'd like you to complete this assignment within one week of receiving
instructions to do this from your recruiting contact. However, we
understand that this may not always be possible, for any number of
reasons. If this poses a problem for you, please let your recruiting
contact know what timeline works for you.

## Assignment

Document and automate building `Python 3.5.4` and the `python-blosc
1.14.2` python package from source on either Windows 10 64-bit or Windows
Server 2016 64-bit using the Visual Studio 2015 toolchain.  You should
also build `c-blosc 1.5.1` from source and have your python-blosc build
use it.

You should write detailed notes on downloading and building each
component by hand, provide a script which automates this process and
provide documentation on how to use this script and extend it for other
extensions.

If you don't have a ready-built windows system with Visual Studio 2015
installed, we have provided an [importable virtual machine for
VirtualBox (19Gb)](https://s3.amazonaws.com/activestate-homework-support/ActiveState+Homework+Builder.ova)

## Sharing Your Code and Docs With Us

We do not want your solution available on the public Internet. **Do not
put this code into a public repo in order to share it with us.**

You can share it with us in one of two ways:

* Make a private repo and share it with us. You should have already been told
  who to invite if we asked you do this homework.
  * Note that while GitHub charges for private repos, BitBucket and GitLab
    both offer private repos as part of their free plans.
* Send an email containing a zip or tarball attachment. You can send this to
  your recruiting contact at ActiveState.

## HINTS

* Always discover the flags needed for each component required to build for
  a 64-bit architecture
* To build a usable Python on windows, it is best to use the scripts in
  Tools\\msi in the python source distribution and then install python using
  the resultant installer
* c-blosc uses CMake to build.  The correct flag for a 64-bit build of
  c-blosc using Visual Studio 2015 is ```-G "Visual Studio 14 2015 amd64"```
