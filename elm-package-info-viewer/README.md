Thank you for your interest in working with ActiveState as a developer. This programming assignment will help us to evaluate your skills relative to our working environment and is used as a primary tool in our hiring process. Later on in the hiring process we will have one of our developers pair with you on making changes to your code, fixing bugs, etc.

We expect this assignment to occupy no more than 3 hours of your time.  We are primarily looking for high-quality code, including test code, and we recognize that you may not have time to fully polish your work, so focus on code before documentation and other niceties.

## Time Limit

We'd like you to complete this assignment within one week of receiving instructions to do this from your recruiting contact, unless you were told otherwise. However, we understand that this may not always be possible, for any number of reasons. If this poses a problem for you, please let your recruiting contact know what timeline works for you.

## Requesting an Exemption

The purpose of this assignment is to help us better understand your abilities as a software engineer. In addition, we will also use the work you produce as part of a pairing session during our hiring process.

You may already have some publicly available code which would help us on both these fronts. If you do, let us know and we will take a look. We’re looking for something with the following characteristics:

* This must be your project, meaning that you wrote most of the code and you are the project's primary maintainer.
* It should be something that is neither trivially small nor overwhelmingly large. We’re looking for something that ranges from 500-2000(ish) lines of code. Anything much smaller won’t have enough complexity for us to evaluate your engineering skill. Anything much larger is just overwhelming for us to evaluate and pair with you on.
* There should be something in the project that you’d like to work on during a pairing session. This could be fixing a bug, adding a small feature, doing a refactoring, adding tests, etc. We don’t have to finish this work during the session, but it should be something simple enough that we can really dig into it in the space of 90 minutes.

Please let your recruiting contact at ActiveState know if you have something you think is appropriate. We'll get back to you promptly to let you know if it is, in which case you can skip the homework assignment entirely.

## Assignment

Your assignment is to build a small front-end application written in Elm that uses the PyPi API to display information about the following packages.

* `requests`
* `Pendulum`
* `xhtml2pdf`

#### Requirements

* The app allows the user to select from the three packages above.
* By default, no pacakge is selected.
* When one of the packages is selected it should display information for just that package.
* When displaying a package it should list the following information...
  * The package name
  * A list of available versions
    * Found in `releases` in the response
    * We don't care about the associated meta-data for each version, just the version numbers are OK
  * A list of related links
    * Found in `project_urls` in the response
  * A list of dependencies for that package
    * Found in `requires_dist` in the response

#### API Info

The PyPi API documentation is avialable here
* https://warehouse.readthedocs.io/api-reference/json.html

A sample call to fetch information for the `Pendulum` package
* `https://pypi.org/pypi/Pendulum/json`


### Using Boilerplate is OK
It's totally fine if you use a light weight boilerplate to kickstart your development process.
  

### Instructions for Us

Please list any instructions for us to get your code up and running, you can put that information into a `README` file or something like that.


## Sharing Your Code with Us

Please upload a zip or tarball attachment to our recruiting system.

We do not want your solution available on the public Internet. **Do not
put this code into a public repo in order to share it with us.**
